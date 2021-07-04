# Account Linking

When a user signs up with a SSO (Single Sign-On) method a new user is created with the email provided by the auth provider and the same applies for the full name (if the provider supports it).

If a user with the same email already exists and the account has not been linked to that user the authentication will fail.

To link to an existing user profile a new auth provider the user must follow these steps:
1. Redirect the browser to the account linking URL: `{{ API_URL }}/users/{{ USER_ID }}/accounts/link/{{ AUTH_PROVIDER_ID }}`, where:
  - `API_URL` is the API's endpoint
  - `USER_ID` is the id of the user to which the account will be linked
  - `AUTH_PROVIDER_ID` is the id of the auth provider, supported values are:
    - `facebook`
    - `google`
    - `twitter`
2. An `HMAC` is computed (in `hex` format) with the `USER_ID` as the input value
3. The user is redirected to the auth URL: `{{ API_URL }}/auth/{{ AUTH_PROVIDER_ID }}?link={{ HMAC }}--{{ USER_ID }}`, where:
  - `API_URL`, `AUTH_PROVIDER_ID` and `USER_ID` are the same as before
  - `HMAC` is the HMAC computed in the previous step
4. If the HMAC is valid, the user does not have already linked an account from the same auth provider and that account is not already linked to any other user the linking process is completed successfully.
