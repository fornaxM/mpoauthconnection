# Introduction #

MPOAuthAPIRequestLoader encapsulates API requests to the service endpoint in order to keep the request, response, and connection together.


# Properties & Tasks #
## Properties ##
```
@property (nonatomic, readwrite, retain) id <MPOAuthCredentialStore, MPOAuthParameterFactory> credentials;
@property (nonatomic, readwrite, retain) MPOAuthURLRequest *oauthRequest;
@property (nonatomic, readwrite, retain) MPOAuthURLResponse *oauthResponse;
@property (nonatomic, readonly, retain) NSData *data;
@property (nonatomic, readonly, retain) NSString *responseString;
@property (nonatomic, readwrite, assign) id target;
@property (nonatomic, readwrite, assign) SEL successSelector;
@property (nonatomic, readwrite, assign) SEL failSelector;
```

## Initialization ##
```
- (id)initWithURL:(NSURL *)inURL;
- (id)initWithRequest:(MPOAuthURLRequest *)inRequest;
```

## Performing the loading ##
```
- (void)loadSynchronously:(BOOL)inSynchronous;
```