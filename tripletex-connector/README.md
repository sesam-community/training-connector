# Tripletex
A Sesam connector for training purposes. Simulates a push receiver working with a rest system, in this case Tripletex.

# How to test

Add the following variables to an ``.authconfig`` file at the root:

`Consumer token` and `Employee token` stated here: [https://github.com/datanav/sesam-talk-config/wiki/Connectors:Tripletex under the Workshop section](https://github.com/datanav/sesam-talk-config/wiki/Connectors:Tripletex)

## Setting up Webhooks

To enable webhooks you must ensure that the service_url environment variable is set in your metadata config of your subscription. The service_url should look like so:

``https://<your_datahub_id>.sesam.cloud/api``

To register your webhooks make sure to run the webhook register pipes for each of your defined datatypes that support webhooks.

Verify in the execution log for each of your webhooks pipes that the pipe succeeded in registering the webhooks.
