Energenie can be accessed via API. API documentation is available [here](https://mihome4u.co.uk/docs/api-documentation).

To do anything with Energenie via API, you need to authenticate. Easiest way to do it is by using [HTTP Basic auth](https://en.wikipedia.org/wiki/Basic_access_authentication). A call with "Authorization: Basic" header will fetch the API key, that is much more handy to use in further calls.

> $ echo -n "user:password" \| base64 \# generates TOKEN  
> $ curl -s [https://mihome4u.co.uk/api/v1/users/profile](https://mihome4u.co.uk/api/v1/users/profile) -H "Authorization: Basic TOKEN"  
> {"status": "success", "time": 0.0, "flags": {},  
>     "data": {"api\_key": "1234", "password\_hash": "23456", "id": 111, "first\_name": "Bart", "last\_name": "Prokop"}}

From above we need to copy the api\_key field. For obvious reasons the above has been redacted. It is recommended to use API key for API calls. The following commands list all gateways.

> $ curl -s [https://mihome4u.co.uk/api/v1/devices/list](https://mihome4u.co.uk/api/v1/devices/list) -H "Authorization: Basic TOKEN"

Gateways are't so interesting, more interesting are \(sub\)**devices**:

> $ curl -s https://mihome4u.co.uk/api/v1/subdevices/list -H "Authorization: Basic TOKEN"  
> {"status": "success", "time": 0.01, "flags": {}, "data": \[  
>         {"device\_type": "legacy", "id": 111111, "label": "Television",

We just need to parse results and note device **id**. Then it is trivial to switch devices on/ff:

> curl -s https://mihome4u.co.uk/api/v1/subdevices/power\_on -H "Authorization: Basic TOKEN" --data 'params={"id":111111}'
>
> curl -s https://mihome4u.co.uk/api/v1/subdevices/power\_off -H "Authorization: Basic TOKEN" --data 'params={"id":111111}'

.

