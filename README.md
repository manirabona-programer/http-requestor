# HttpRequestor from Patienceman

HTTP Requestor: Package for a client request that supports you to make an external service request easily and with fast usage.

## Installation

To install the package don't require much requirement except to paste the following command in laravel terminal, and you're good to go.

```bash
  composer require patienceman/httprequestor
```

## Usage

To use Http Requestor u need to call ```bash HttpRequest `` class,
Let take example with it and see the simplisity

```PHP
  $http = HttpRequest::server('https://commandement.com');
```
So!, now you can make request with all stardard methods.
There are two way this package is usefull, by requesting 
access token to server or by send normal request

let take example on requesting access token
```PHP
  $http = HttpRequest::server('https://commandement.com');

  $http->buildHttpQuery([
      'grant_type' => 'client_credentials',
      'client_id' => config('services.custom.client_id'),
      'client_secret' => config('services.custom.client_secret'),
      'scope' => config('services.custom.scope)
  ]);

  return $http->requestToken('/oauth/token');
```
So now we are able to request access token.

Let also take example on normally api request with stardand http methods
```PHP
  $http = HttpRequest::server('https://commandement.com');

  $http->withHeaders([
      'Authorization' => $accessToken,
      'Accept' => 'application/json',
  ])->withData([
    'name' => 'moses',
    'location' => 'mountain-sinai',
    'command' => 'navigate islaels'
  );
  
  $http->request('POST', '/api/sync-movement')

  return $http->then(function($response, $error) {
      return $response->last_update_at;
  });
```
Fantastic right! and super cool!

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License
[MIT](https://choosealicense.com/licenses/mit/)
