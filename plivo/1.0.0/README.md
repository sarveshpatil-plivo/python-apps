# Plivo

An app for sending SMS through the Plivo Messages API. Use it in a workflow to text an on-call responder when a monitor fires, a case is created, or an alert changes state.

## Requirements
A Plivo account with an Auth ID and Auth Token, and a sender (a Plivo phone number, short code, or where allowed an alphanumeric sender). Find your Auth ID and Auth Token in the Plivo console at https://cx.plivo.com.

## Authentication
1. url - the Messages API URL for your account, `https://api.plivo.com/v1/Account/YOUR_AUTH_ID/Message/`
2. username - your Plivo Auth ID
3. password - your Plivo Auth Token

## Actions
1. Send_SMS - sends an SMS through the Plivo Messages API.
   - From - the sender ID
   - To - one receiver, or a comma separated list of receivers sent as a single request
   - body - the message text

## Notes
- A successful call means the message is queued, not yet delivered. Delivery status arrives on a separate callback URL if you configure one.
- Each call sends and bills a new message, so guard against accidental retries in a loop.
- The action returns a summary. The raw Plivo response, including message_uuid, is under results[0].body.
