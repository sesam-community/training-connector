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
        "_id": "<my-company-id>",
        "id": "<my-company-id>",
        "email": "<my-company-email>",
        "name": "<my-company-name>",
        "phoneNumber": "<my-company-phonenumber>",
        "website": "<my-company-website>"
    }
]
```
