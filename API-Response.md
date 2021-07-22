# API Response

These should be the default response codes for successful requests.

- `GET`:
  - Status Code: `200 OK`
  - Response Body: *object* or *array of objects*
- `POST`: `201 Created` -> { id: *resource_id* }
  - Status Code: `201 Created`
  - Response Body: *object with only the ID of the new resource*
- `PATCH`:
  - Status Code: `204 No Content`
  - Response Body: *void*
- `PUT`:
  - Status Code: `204 No Content`
  - Response Body: *void*
- `DELETE`:
  - Status Code: `204 No Content`
  - Response Body: *void*

## Errors

How to throw an error:

*Note: here we are using `badRequest` and `badImplementation` but this applies to all other methods*

```typescript
/**
 * SPECIFIC ERROR
 * 
 * "undefined" so that Hapi uses its default
 * error message (for example: "Bad Request")
 */
throw Boom.badRequest(undefined, [
    {
        /**
         * The field that caused the error, if this is a request with
         * no fields from the client, such as "DELETE" requests, the
         * field is the name of the resource (for example: "user")
         */
        field: "field",
        /**
         * The error message that will be displayed on the client
         */
        error: "error message",
    },
]);

/**
 * GENERIC ERROR
 */
throw Boom.badImplementation();
```
