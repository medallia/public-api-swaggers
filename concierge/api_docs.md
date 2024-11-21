# Zingle REST API

The Zingle REST API can be used to perform almost any of the functions that can be performed from the Zingle Team Inbox, including managing contacts, sending messages, and configuring your Zingle service.

All users with an active Zingle account have access to the REST API using their existing Zingle


# Authentication

## Basic Authentication

Zingle's API supports basic authentication using your Zingle username and password.

## JWT Auth

A JWT may be obtained using the [JWT API](/api/auth-ref/jwt/get-jwt) (if using Zingle's build-in authentication) or in the "My Settings" window in the product (if using oAuth or SSO).

Once you've obtained a JWT, you may use it as the Bearer token in any API request.


# Request & Response formats

The Zingle API accepts JSON for all requests, except where noted.

## Headers
Ensure the `Content-Type` header to be set to `application/json`.

## Data Formats

### Dates

Zingle's API accepts any valid ISO-8601 date format and returns the same

### Phone Numbers

It's always best to use the full `E.164` format (ex. "+14065551212") when specifying phone numbers.  If a string in another format (such as "406-555-1212") is supplied, Zingle will attempt to detect the country of the number automatically.


# Opt-in/out notifications

### Triggering Events

Opt-in status change webhooks are sent whenever the opt-in/out status of a contact's phone number changes.  This can happen several ways:

- A contact sends an opt-out keyword such as STOP or UNSUBSCRIBE
- A Zingle user manually blocks inbound or outbound messaging for a channel
- A contact sends an opt-in keyword such as START

```json title="Schema" jsonSchema
{
  "type": "object",
  "properties": {
    "action": {
      "type": "string",
      "enum": [
        "block",
        "unblock"
      ],
      "description": "Whether the channel is being blocked or unblocked"
    },
    "direction": {
      "type": "string",
      "enum": [
        "inbound",
        "outbound"
      ],
      "description": "Whether the block/unblock applies to inbound or outbound messages"
    },
    "service_id": {
      "type": "string",
      "format": "uuid"
    },
    "service_name": {
      "type": "string"
    },
    "contact_id": {
      "type": "string",
      "format": "uuid"
    },
    "contact_external_id": {
      "type": "string",
      "description": "If the contact was created from or is synced with an external system (such as Oracle Opera, Salesforce, Mindbody, or any custom integration you've configured with Zingle) their ID from the external system will be "
    },
    "service_phone": {
      "type": "string"
    },
    "contact_phone": {
      "type": "string"
    },
    "is_auto_blocked": {
      "type": "boolean",
      "description": "If the block is 'auto' that indicates that the block was initiated by the contact and therefor can only be changed by the contact. \n\nIf this value is false, that means the block was created by a Zingle user and the block may also be removed by a Zingle user without confirmation from the contact."
    }
  }
}
```

```json title="Sample Payload"
{
    "action": "block",
    "direction": "outbound",
    "service_id": "fbb44d67-7437-464d-b249-17e9f918dc8e",
    "service_name": "Foo Hotel",
    "contact_id": "f6882aa2-afaf-4230-ae0a-cde79e78afb4",
    "contact_external_id": "9879a777",
    "contact_phone": "+14065551212",
    "service_phone": "+17605558585",
    "is_auto_blocked": true
}
```
