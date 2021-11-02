# Azure Cosmos DB API for MongoDB Query RU Consumption
Optimizing Azure Cosmos DB API for MongoDB Query RU Consumption by virtue of Indexing Changes

The Azure Cosmos DB API for MongoDB makes it easy to use Microsoft's premier NoSQL database, Azure Cosmos DB as if it were a MongoDB database. You can leverage your MongoDB experience and continue to use your favorite MongoDB drivers, SDKs, and tools by pointing your application to the API for MongoDB account's connection string. Visit [here](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb/mongodb-introduction) for getting started with Azure Cosmos DB API for MongoDB.

**How do I find the request unit charge for operations executed in Azure Cosmos DB API for MongoDB**

You can use the [Azure portal](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb/find-request-unit-charge-mongodb#use-the-azure-portal), [MongoDB .NET driver](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb/find-request-unit-charge-mongodb#use-the-mongodb-net-driver), [MongoDB Java driver](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb/find-request-unit-charge-mongodb#use-the-mongodb-java-driver) & [MongoDB Node.js driver](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb/find-request-unit-charge-mongodb#use-the-mongodb-nodejs-driver).

**If my Query is using too many RUs, where do I look for optimizing my RU Consumption**
There are a couple of places you should look at as documented here.

The starting place is $explain command.
```
db.coll.find({foodGroup: "Baby Foods"}).explain({"executionStatistics": true })
```

If your Query's RU is too high, then you should investigate further to understand whether you've correctly set Indexes for the Collection. As explained here in this document.

**Example process:**
- Step1: Use this [QuickStart](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb/create-mongodb-dotnet) to build a .NET Web API using Azure Cosmos DB's API for MongoDB. Then load the sample data using [mongoimport](https://docs.mongodb.com/database-tools/mongoimport/#mongodb-binary-bin.mongoimport), a CLI tool that easily imports small amounts of JSON, CSV, or TSV data.
```
mongoimport --host <HOST>:<PORT> -u <USERNAME> -p <PASSWORD> --db cosmicworks --collection products --ssl --jsonArray --writeConcern="{w:0}" --file Data/products.json
```

- Step2: 
![Image1](media/1.png)
