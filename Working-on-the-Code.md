<!-- omit in toc -->
This page covers the practical side of working on FediFetcher's code: getting set up,
the checks your Pull Request needs to pass, and where things live.

For how to report a bug, suggest a feature, or submit a change, see
[Contributing to FediFetcher](Contribute-To-FediFetcher).

<!-- omit in toc -->
## Table of Contents

- [Getting set up](#getting-set-up)
- [The checks](#the-checks)
- [How the code is laid out](#how-the-code-is-laid-out)
- [Adding a configuration option](#adding-a-configuration-option)
- [Supporting a new server software](#supporting-a-new-server-software)
- [Writing tests](#writing-tests)

## Getting set up

FediFetcher needs **Python 3.11 or newer**.

```bash
git clone https://github.com/nanos/FediFetcher
cd FediFetcher
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements-dev.txt
```

`requirements-dev.txt` includes everything in `requirements.txt`, plus the test and
linting tools. If you only want to *run* FediFetcher rather than work on it,
`requirements.txt` on its own is enough.

## The checks

Your Pull Request has to pass all of these. Running them locally is much faster than
waiting for CI:

```bash
ruff check .        # linting
mypy                # type checking
pytest              # the test suite
pytest --cov        # the same, with the coverage gate
```

`ruff` can fix much of what it finds:

```bash
ruff check --fix .
```

### Coverage is enforced

The suite has to keep total coverage above the threshold set in `pyproject.toml`. A Pull
Request that adds code without tests will fail CI even if every test passes. If you are
adding a new module, please add tests alongside it.

### Tests run in a random order

`pytest-randomly` shuffles the tests on every run, so that no test can come to depend on
another having run first. If your test only passes in a particular order, that is a bug
in the test — usually shared state that is not being reset.

### What CI runs

Pull Requests are checked on Python 3.11, 3.12 and 3.13. Linting and type checking run
once, on 3.11.

## How the code is laid out

Everything lives in the `fedifetcher` package. `find_posts.py` at the top level is a
small shim that calls into it, kept so that existing cron jobs and containers keep
working.

| module | what it does |
|---|---|
| `config.py` | reads settings from the command line, environment and config file |
| `http.py` | makes requests: rate limiting, robots.txt, the instance blocklist |
| `urls.py` | works out which server and post a URL refers to |
| `servers.py` | discovers what software a server runs, and which API it speaks |
| `api/` | one client per server software |
| `state.py` | the collections FediFetcher remembers between runs |
| `store.py` | reading and writing the state directory, and the lock file |
| `context.py` | gathering replies to a post from its original server |
| `backfill.py` | pulling an account's posts |
| `tasks.py` | the individual features, one function each |
| `run.py` | ties it together: `main()`, logging, the monitoring callbacks |

`tests/` mirrors this layout, so `fedifetcher/urls.py` is tested by `tests/test_urls.py`.

## Adding a configuration option

Options are declared once, as a field on `Config` in `config.py`:

```python
max_list_length: int = opt(100,
    help="Determines how many posts we'll fetch replies for in each list. ...")
```

The command-line flag (`--max-list-length`), the environment variable
(`FF_MAX_LIST_LENGTH`), the config file key (`max-list-length`) and how the value is
parsed are all derived from that one line. There is no second place to update.

## Supporting a new server software

This takes three small steps:

1. Write `fedifetcher/api/yoursoftware.py` with a class providing `fetch_user_posts()`
   and `fetch_context_urls()`. Copy `api/peertube.py` — it is the shortest example.
2. Add the software's name to `SOFTWARE_APIS` in `servers.py`, under the API it speaks.
   If it is a genuinely new API rather than another implementation of an existing one,
   add a value to `ApiFlavour` too.
3. Add your class to `CLIENTS` in `api/__init__.py`.

The test suite will tell you if you miss step 3.

## Writing tests

`tests/conftest.py` provides fixtures you can ask for by name:

- `http` — a stand-in HTTP client; set `http.get.return_value` to whatever the test needs
- `reply` — builds fake responses: `reply(200, {"key": "value"})`
- `state` — a real, empty `State`
- `home` — a stand-in for our own instance

```python
def test_context_is_empty_on_an_error_status(http, reply):
    http.get.return_value = reply(500)
    assert PeerTubeApi("video.example", http).fetch_context_urls("1", "url") == []
```

Please prefer tests that check what a function *does* over tests that check which
functions it called. Tests written against the real objects survive refactoring; tests
that assert on a chain of mocks tend to break without catching anything.
