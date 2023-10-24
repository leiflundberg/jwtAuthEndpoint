# jwtAuthEndpoint
An example of endpoints written in Golang with the Echo framework that demonstrate the following routes: unrestricted, login and restricted. Uses JWT and middleware.

By logging in with the following credentials a user will receive a token that grants access to the restricted endpoint for 72 hours.

* username: **Avicii**
* password: **rip**

To test locally:
```bash
go run .
```

## / - Accessible (unrestricted route)
```bash
curl http://localhost:8080/
```
Returns: Hello, World!

## /login - Fetch token
```bash
curl --request POST \
  --url http://localhost:8080/login \
  --header 'Content-Type: application/x-www-form-urlencoded' \
  --data username=Avicii \                  
  --data password=rip
```
Example:
```json
{
	"token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoiVGltIiwiYWRtaW4iOnRydWUsImV4cCI6MTY5ODQzNzExOH0.GEA7TjSavsUnPWWrfgkQC14n8vEaUoY3UhkfmL136X4"
}
```

## /restricted
Remember to replace the bearer token with the token you receive from the login endpoint.
```bash
curl --request GET \
  --url http://localhost:8080/restricted \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoiVGltIiwiYWRtaW4iOnRydWUsImV4cCI6MTY5ODQzNjM2Nn0.K-Dlb_FjegbBdxSJStt5rdHliQde5Nh8o_XOkgxXu-Y' \
```
Returns: Welcome Tim!