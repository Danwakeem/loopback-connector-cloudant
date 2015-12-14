## loopback-connector-cloudant

Cloudant DB connector for the StrongLoop Loopback framework.

Please see the full documentation at [docs.strongloop.com](https://docs.strongloop.com/display/public/LB/Cloudant+connector)

### Key Features

* Uses Cloudant Query (Lucene) to support ad-hoc searching
* [Loopback Query](https://docs.strongloop.com/display/public/LB/Querying+data) support for: fields, limit, order, skip and where filters
* Query and filtering is performed on the database for optimal efficiency
* Use different DB instances per Model definition
* Support basic Model discovery

### LoopBack Connectors

LoopBack provides connectors for popular relational and NoSQL databases.
These connectors implement CRUD operations as a common set of methods
across different databases and allow quick and easy API creation for new
or existing datasources.

[More Info>>](https://www.ng.bluemix.net/docs/starters/LoopBack/index.htm)

### IBM Cloudant

IBM Cloudant® is a NoSQL database platform built for the cloud. You can
use Cloudant as a fully-managed DBaaS running on public cloud platforms
like Bluemix, SoftLayer or via an on-premise version called Cloudant
Local.

[More Info>>](https://www.ng.bluemix.net/docs/services/Cloudant/index.html)

### Install

To install the connector cd into the top level directory of your
loopback application, enter:

```
$ npm install loopback-connector-cloudant --save
```

The --save options automatically as the dependency to the package.json
file

### Configuring the Cloudant datasource

Use the [Data source generator](https://docs.strongloop.com/display/public/LB/Data+source+generator) to add the Cloudant data source to your
application. The entry in the applications /server/datasources.json will
look something like this:

```
"mydb": {
  "name": "mydb",
  "connector": "cloudant",
  "username": "XXXX-bluemix",
  "password": "YYYYYYYYYYYY",
  "database": "test"
}
```

Edit the datasources.json to add other supported properties as required:

Property  | Type | Description
----------| -----| --------
database  | String | Database name
username  | String | Cloudant username, use either 'url' or username/password
password  | String | Cloudant password
url       | String | Cloudant URL containing both username and password
modelIndex | String | Specify the model name to document mapping, defaults to 'loopback\_\_model\_\_name'


### Model Specific Configuration

Per Model configuration is also supported for database selection and to
specify different Loopback Model to document mappings:

common/models/<model_name>.json
```
{
  "name": "User",
  "base": "PersistedModel",
  "idInjection": true,
  ...
  "settings": {
    "cloudant": {
        "modelIndex": "myPropertyName",
        "database": "test2"
    }
  },
  ...
```
Model specific configuration settings:

Property  | Type | Description
----------| -----| --------
database  | String | Database name
modelIndex | String | Specify the model name to document mapping, defaults to 'loopback\_\_model\_\_name'
