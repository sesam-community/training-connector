# Tripletex
A Sesam connector for training purposes. Simulates a push receiver working with a rest system, in this case Tripletex.

# How to test

Add the following variables to an ``.authconfig`` file at the root:

`Consumer token` and `Employee token` stated here: https://github.com/datanav/sesam-talk-config/wiki/Connectors:Tripletex under the **Sesam training** section

## Upload configs to your dev node
Use sesam-py to upload the connector skeleton to your local dev node. In addition to the *.authconfig* file you also need the normal *.syncconfig* file

## Step 1: Push data to http_endpoint source
To push data to the http_endpoint source you need to define the correct url: ....receivers/<pipe-name>/entities

The entity (entities) you push should have the following general structure:
```json
[
    {
        "_id": "90213",
        "id": "90213",
        "email": "kafka3@companymail.com",
        "name": "Kafka3 company",
        "phoneNumber": "+47 98798787",
        "website": "www.kafkacompany.com"
    }
]
```

To enable webhooks you must ensure that the service_url environment variable is set in your metadata config of your subscription. The service_url should look like so:

``https://<your_datahub_id>.sesam.cloud/api``

To register your webhooks make sure to run the webhook register pipes for each of your defined datatypes that support webhooks.

Verify in the execution log for each of your webhooks pipes that the pipe succeeded in registering the webhooks.
