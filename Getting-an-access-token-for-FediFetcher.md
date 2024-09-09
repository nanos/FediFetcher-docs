Regardless of how you want to run FediFetcher, you must first get an access token:

#### If you are an Admin on your instance

1. In Mastodon go to Preferences > Development > New Application
   1. Give it a nice name
   2. Enable the required scopes for your options. You could tick `read` and `admin:read:accounts`, or see below for a list of which scopes are required for which options.
   3. Save
   4. Copy the value of `Your access token`

#### If you are not an Admin on your Instance

1. Go to [GetAuth for Mastodon](https://getauth.thms.uk?scopes=read&client_name=FediFetcher)
2. Type in your Mastodon instance's domain
3. Copy the token.