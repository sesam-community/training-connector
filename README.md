# Tripletex

A Sesam connector for Tripletex

## Structure needed to make the connector workflow function

```
training-connector/
    .authconfig (Set CONSUMER_TOKEN & EMPLOYEE_TOKEN)
    .syncconfig (Set NODE & JWT)
    README.md
    manifest.json (Set and define which templates to use for datatypes)
    templates/

```

## General instruction when editing files.

You should not change the json files within the templates folder locally. The `manifest.json` file you can change locally to reflect which datatypes you want generated in your Sesam subscription when doing your development. 

## .authconfig
tripletex uses the format:

consumer_token=.....

employee_token=....


## Exercises
1. Collect the product data from Tripletex
   - What can be used as _id? How is that added to the entity? 
2. Insert a new Tripletex product (you will need to repost and edit an entity to do this)
   - How to construct a REST operation? How does the share entity need to be edited in order to provoke an insert? 
3. Update the Tripletex product you inserted (you will need to repost and edit an entity to do this)
   - How does a share entity need to be edited to provoke an update? What happens in the share template before the actual update REST operation? 
4. $last-modified is using \["now"\]. Use data from the incoming entity instead
   - What data exists in the entity that can be used to construct $last-modified?
      <details> 
      <summary>HINT 1 </summary>
        Tripletex has an array called "changes". 
      </details>
      <details> 
      <summary>HINT 2 </summary>
        This can contain the events CREATE and UPDATE.
      </details>
      <details> 
      <summary>HINT 3 </summary>
        $last-modified should be the data of the most recent change.
      </details>
5. Add the project datatype
   - What strategies exist for adding a new datatype? 
        <details> 
        <summary>HINT </summary>
          Can you reuse an existing template? 
        </details> 

## Helpful Links and tips
- [Tripletex API documentation](https://tripletex.no/v2-docs/)
- [Internal wiki for the connector-workflow](https://github.com/datanav/sesam-talk-config/wiki/Connector-Development-Pipeline)
- [Internal tripletex wiki](https://github.com/datanav/sesam-talk-config/wiki/Connectors:Tripletex)
  - "Older account, not used" is what we have been using for training. Otherwise create own account and populate with contact and product data.
- [Connector Contract](https://docs.sesam.io/hub/documentation/data-synchronization/connectors/contract-connectors.html)
- [Rest Transform Docs](https://docs.sesam.io/hub/documentation/service-configuration/pipes/configuration-transforms-rest.html)
- Run collect pipes to test that upload works.
  - Pump-failed.. 
    - Trace works wonders! You can read about the details on docs
    - Execution Log like always

- To insert an entity the $origin property must be present and the primary_key must be missing
- To update an entity you need $based_on and $based_on_properties
- Example insert
```
{
    "$last-modified": "~t2023-04-19T20:55:53Z",
    "$origin": "~:hubspot-contact:1",
    "_deleted": false,
    "_hash": "199260a25d37b14bf724d8170dfbeec1",
    "_id": "global-test:1",
    "_previous": null,
    "_ts": 1684918153221315,
    "_updated": 227,
    "email": "hg@gmail.com",
    "firstName": "Holger",
    "lastName": "Rune"
  }
```
- Example update
```
{
"$based_on": {
    "firstName": "Donatella",
    "id": 1764741,
    "lastName": "Pizzeria"
  },
  "$based_on_properties": [
    "firstName",
    "lastName",
    "id",
    "phoneNumberMobile"
  ],
  "$last-modified": "~t2023-04-19T20:55:53Z",
  "firstName": "Donatella",
  "id": 1764741,
  "lastName": "Pizzeria",
  "phoneNumberMobile": "+47 40 376 872"
}
```
