# Introduction #

MPOAuthConnection was created primarily to be a very high level wrapper around Web Services that utilize OAuth as a an authorization mechanism. The goal is that you merely give it your credentials and then call the methods on the remote server endpoint that you're interested in receiving the data requested either synchronously or asynchronously for. It will even take care of the credential storage utilizing the keychain on Mac OS X and iPhone for secure storage. It also allows people who are interested to directly use the underlying MPOAuthConnection class directly and manage the OAuth state themselves.

# The useful snippet #
The lines of code that take you from nothing to working are:
```

NSDictionary *credentials = [NSDictionary dictionaryWithObjectsAndKeys:	@"consumerKey"], kMPOAuthCredentialConsumerKey,
									@"consumerSecret", kMPOAuthCredentialConsumerSecret,
									nil];

_oauthAPI = [[MPOAuthAPI alloc] initWithCredentials:credentials
				  authenticationURL:[NSURL URLWithString:@"http://example.com/login/oauth"]
					 andBaseURL:[NSURL URLWithString:@"http://example.com/webservice"]]];
```

The above is all you really need(after you've input your urls and credentials), once you've done that the framework will automatically try and connect to the service, authorize itself, open a browser to get authorized by the user, and finally get an access token allowing you to begin making authorized API calls as soon as the access token notification has been received.

# Samples #
  * [MPOAuthClient](MPOAuthClient.md) - Mac
  * [MPOAuthMobile](MPOAuthMobile.md) - iPhone/iPod Touch

# High Level Classes #
  * [MPOAuthAPI](MPOAuthAPI.md)
  * [MPOAuthAPIRequestLoader](MPOAuthAPIRequestLoader.md)

# API Components #
  * [MPOAuthConnection](MPOAuthConnection.md)
  * [MPOAuthURLResponse](MPOAuthURLResponse.md)
  * [MPOAuthURLRequest](MPOAuthURLRequest.md)
  * [MPURLRequestParameter](MPURLRequestParameter.md)
  * [MPOAuthSignatureParameter](MPOAuthSignatureParameter.md)