# ![LOGO](logo.png) NPR Sponsorship Service **flow**ground Connector

## Description

A generated **flow**ground connector for the NPR Sponsorship Service API (version 2).

Generated from: https://api.apis.guru/v2/specs/npr.org/sponsorship/2/swagger.json<br/>
Generated at: 2019-05-07T17:43:17+03:00

## API Description

Sponsorship for non-NPR One client applications

## Authorization

Supported authorization schemes:
- OAuth2

For OAuth 2.0 you need to specify OAuth Client credentials as environment variables in the connector repository:
* `OAUTH_CLIENT_ID` - your OAuth client id
* `OAUTH_CLIENT_SECRET` - your OAuth client secret

## Actions

### Request DAAST sponsorship units

> **Not** for use by NPR One clients (for whom sponsorship is already integrated into the Listening Service), this endpoint is designed to be used by our other client applications to request sponsorship on behalf of a user. Sponsorship units are returned in the form of DAAST XML. It is worth noting that this endpoint attempts to always return XML, even in the case of exceptions.<br/>
> <br/>
> The default behavior of this endpoint is asynchronous; on an initial request, a call to our external sponsorship provider is placed on a queue, which is typically processed within 3 minutes. Once the sponsorship call is received and processed, the returned sponsorship units are placed in a cache on our server for the current user. Subsequent calls to this endpoint will return DAAST sponsorship units from this cache until tracking information is submitted, which removes the ad from the cache and will automatically request additional ads asynchronously if there are fewer than a certain number remaining in the cache.<br/>
> <br/>
> For development purposes, it's worth noting that there is currently no way to clear a user's cache without submitting some form of tracking.

*Tags:* `sponsorship`

#### Input Parameters
* `Authorization` - _required_ - Your access token from the Authorization Service. Should start with `Bearer`, followed by a space, followed by the token.
* `X-Advertising-ID` - _optional_ - A device-specific advertising identifier, if possible. Apple's IDFA is an example.
* `forceResult` - _optional_ - Whether to force a synchronous call to our external sponsorship provider; the default behavior is asynchronous.
* `adCount` - _optional_ - How many sponsorship units to request in one call; if left unspecified, the default behavior is to return only 1.

### Record tracking data for DAAST sponsorship units

> **Not** for use by NPR One clients (for whom sponsorship is already integrated into the Listening Service), this endpoint is designed to be used by our other client applications to submit tracking information for sponsorship units obtained from the `GET /sponsorship/v2/ads` endpoint.<br/>
> <br/>
> The tracking information should be submitted in the body of the request in the form of a JSON object following the Collection.Doc+JSON specification.

*Tags:* `sponsorship`

#### Input Parameters
* `Authorization` - _required_ - Your access token from the Authorization Service. Should start with `Bearer`, followed by a space, followed by the token.
* `X-Advertising-ID` - _optional_ - A device-specific advertising identifier, if possible. Apple's IDFA is an example.

## License

**flow**ground :- Telekom iPaaS / npr-org-sponsorship-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
