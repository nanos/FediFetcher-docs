Below are the scopes that you must enable for the various FediFetcher options:

 - For all actions, your access token must include these scopes:
   - `read:search`
   - `read:statuses`
   - `read:accounts`
 - If you are supplying `reply-interval-in-hours` you must additionally enable this scope:
   - `admin:read:accounts`
 - If you are supplying `max-follow-requests` you must additionally enable this scope:
   - `read:follows`
 - If you are supplying `max-bookmarks` you must additionally enable this scope:
   - `read:bookmarks`
 - If you are supplying `max-favourites` you must additionally enable this scope:
   - `read:favourites`
 - If you are supplying `from-notifications` you must additionally enable this scope:
   - `read:notifications`
 - If you are supplying `from-lists` you must additionally enable this scope:
   - `read:lists`
