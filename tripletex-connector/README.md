# Tripletex
A Sesam connector for training purposes. Simulates a push receiver working with a rest system, in this case Tripletex.

# How to test
Add the following variables to an ``.authconfig`` file at the root:

`Consumer token` and `Employee token` stated here: https://github.com/datanav/sesam-talk-config/wiki/Connectors:Tripletex under the **Sesam training** section

## Step 1: Upload configs to your dev node
Use sesam-py to upload the connector skeleton to your local dev node. In addition to the *.authconfig* file you also need the normal *.syncconfig* file

## Step 2: Push data to http_endpoint source
To push data to the http_endpoint source you need to define the correct url: ....receivers/push-company-all/entities

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

## Step 3: Set up a push-company-collect endpoint
This specific datatype (**company**) for this system (**push**) is read-only, so no collect template is necessary. 

## Step 4: Finish the insert part of the share template for **xxxxxx-customer-share**
There are both data in the actual share template, but also the system (**xxxxxx**) that needs to be filled in

## Step 5: Collect the newly inserted customer back in your collect pipes

## Step 6: Merge entities
Make sure the original entity and the newly inserted entity merge in **xxxxxx-global-organisation**. Equality sets should be used. 

Tip: Look at the *$original_entity* property in your new entity in the sink dataset of the **xxxxxx-customer-organisation-enrich** pipe

## Step 7: Finish the update part of the share template for **xxxxxx-customer-share**
There are both data in the actual share template, but also the system (**xxxxxx**) that needs to be filled in

## Step 8: Play around
