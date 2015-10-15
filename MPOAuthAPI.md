# Introduction #

MPOAuthAPI is the class in which all the magic happens. It's responsible for creating and maintaining an authorized API connection to the service endpoint you requested, once given the proper credentials to do so with. It will connect to the server, and perform a 3 legged oauth authorization request, collect and store your request and access tokens on the keychain, and refresh your access token periodically as necessary. It also allows you to make requests on the remote API synchronously and asynchronously.


# Properties & Tasks #

## Properties ##
```
@property (nonatomic, readonly, retain) NSURL *baseURL;
@property (nonatomic, readonly, retain) NSURL *authenticationURL;
@property (nonatomic, readwrite, assign) MPOAuthSignatureScheme signatureScheme;
@property (nonatomic, readwrite, assign) id <MPOAuthAPIDelegate> delegate;
```
## Initialization ##
```
- (id)initWithCredentials:(NSDictionary *)inCredentials andBaseURL:(NSURL *)inURL;
- (id)initWithCredentials:(NSDictionary *)inCredentials authenticationURL:(NSURL *)inAuthURL andBaseURL:(NSURL *)inBaseURL;
```

Initialization minimally requires credentials containing a consumer secret and key, as well as a base URL for the API service endpoint. Once you create the MPOAuthAPI instance it will automatically begin the authorization sequence to get the proper credentials and once complete it sends a notification, **MPOAuthNotificationAccessTokenReceived**.
## Authentication ##
```
- (void)authenticate;
```
"Do the right thing" in regards to authentication. You usually need to only call this once after the user has authorized your application through the browser unless you made use of the callback URL which automatically informed your application of the successful authorization request completed. When you have no request token it requests one, when you have a request token, it will ask for an access token.  Finally if you already have a valid Access Token, and it's new enough to not have expired nothing happens, otherwise it will refresh the access token.

## Asynchronous API Requests ##
```
- (void)performMethod:(NSString *)inMethod withTarget:(id)inTarget andAction:(SEL)inAction;
- (void)performMethod:(NSString *)inMethod atURL:(NSURL *)inURL withParameters:(NSArray *)inParameters withTarget:(id)inTarget andAction:(SEL)inAction;
```

Perform an asynchronous request by providing the method string relative to the baseURL, the target object you'd like the passed in action selector to be called on when the load is complete and the document is ready. Parameters are passed in as an array of MPURLParameter objects. You can also pass in a different baseURL in the case where a service shares credentials across more than one service endpoint.

## Synchronous API Requests ##
```
- (NSData *)dataForMethod:(NSString *)inMethod;
- (NSData *)dataForMethod:(NSString *)inMethod withParameters:(NSArray *)inParameters;
- (NSData *)dataForURL:(NSURL *)inURL andMethod:(NSString *)inMethod withParameters:(NSArray *)inParameters;
```

Perform a synchronous request by providing the method string relative to the baseURL, the data object is returned to the caller. You can also pass in a different baseURL in the case where a service shares credentials across more than one service endpoint.