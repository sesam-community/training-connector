# Tripletex
A Sesam connector for Tripletex

# How to test

The following varibles need to be configured:

`base_url` and `token` (used by the special tripletexlogin.py in connector-cli), see https://developer.tripletex.no/docs/documentation/getting-started/1-creating-a-test-account/

## Setting up Webhooks

To enable webhooks you must ensure that the service_url environment variable is set in your metadata config of your subscription. The service_url should look like so:

``https://<your_datahub_id>.sesam.cloud/api``

To register your webhooks make sure to run the webhook register pipes for each of your defined datatypes that support webhooks.

Verify in the execution log for each of your webhooks pipes that the pipe succeeded in registering the webhooks.