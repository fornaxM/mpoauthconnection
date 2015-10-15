# Introduction #

MPOAuthClient is the default application used for testing MPOAuth with your service endpoints. It's compiled to link to the MPOAuth framework and requires you to put in your service endpoint and OAuth credentials to be able to quickly test the remote service endpoint responses outside of your application. MPOAuthClient is written using Objective-C 2.0 and requires Leopard or greater to run.


# Using MPOAuthClient #

## 1. Provide your Service URL and Authentication URL ##
After you've either compiled or downloaded a copy of the application you double click to launch it and you're presented with a very simple UI. You need to first set your remote server endpoint on which you'll be making authenticated API requests. On some services, namely some from Yahoo! and Google, the API endpoint is actually different from the authorization endpoint you'll be using for requests. MPOAuth allows for this and the MPOAuthClient application has a separate optional field for you to fill in if this is the case for your service.

## 2. Provide your credentials ##
OAuth has three signing methods, Plaintext, HMAC-SHA1, and RSA-SHA1, most of them require at least a consumer key, and a consumer secret. In the case of RSA-SHA1 the secret is a certificate that you're given. In order to successfully connect to the service you'll need to copy paste in your consumer key and secret into the appropriate fields.

## 3. Hit the Authorize button ##
OAuth preferrably goes through a 3 step authorization sequence in which you first ask for a request token, are issued one and then move on to the next step which is asking for user authorization, generally in a browser. And finally after the user has granted access, the application requesting authorization is given an access token and secret to use for authenticated requests.

  * 3a. A browser will automatically open where you will provide user access credentials
  * 3b. The Authorize button should now say "Request User Access", hit that one last time and it changes to "Access Token Acquired"


## 4. Type in the API requests you wish to now make and they should all successfully return ##

# How MPOAuthClient is built #
MPOAuthClient boils down to 1 source file and 1 header file. Source totally a whopping ~65 lines of code. Only parts that are required are including and linking to the MPOAuth framework, then creating an instance of MPOAuthAPI and setting your urls and credentials.