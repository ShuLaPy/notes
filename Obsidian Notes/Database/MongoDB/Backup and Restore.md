If you ever wanted to backup or restore your mongodb database then `mongodump` and `mongorestore` are the best tools.

Here are the commands to backup and restore the database

---
**Backup Database:**

```
mongodump --uri="mongodb://mongodb0.example.com:27017" --db="integration" --out="integration"
```

`--uri=<connectionString>`

Connection string for database

`--db=<database>, -d=<database>`

Specifies a database to backup. If you do not specify a database, `mongodump` copies all databases in this instance into the dump files.

`--out=<path>, -o=<path>`

Specifies the directory where `mongodump` will write [BSON](https://www.mongodb.com/docs/manual/reference/glossary/#std-term-BSON) files for the dumped databases. By default, [`mongodump`](https://www.mongodb.com/docs/database-tools/mongodump/#mongodb-binary-bin.mongodump) saves output files in a directory named `dump` in the current working directory.

---
**Restore Database:**

```
mongorestore --uri="mongodb://mongodb0.example.com:27017" --db="audict-dev" --dir="/Users/shubham/Desktop/databackup/audict-dev"
```

`--uri=<connectionString>`

Connection string for database

`--db=<database>, -d=<database>`

Specifies the destination database for [`mongorestore`](https://www.mongodb.com/docs/database-tools/mongorestore/#std-program-mongorestore) to restore data _into_ when restoring from a BSON file. If the database does not exist, [`mongorestore`](https://www.mongodb.com/docs/database-tools/mongorestore/#std-program-mongorestore) creates the database.

`--dir=string`

Specifies the dump directory.



!!! info "Backup only specific collection to database"

    `--collection=<collection>, -c=<collection>`
    If you ever wanted to restore just specific collection then you have to add this parameter and instead of passing entire dir just pass that perticular collections BSON.
    Specifies the name of the destination collection for [`mongorestore`](https://www.mongodb.com/docs/database-tools/mongorestore/#std-program-mongorestore) to restore data _into_ when restoring from a BSON file. If you do not specify [`--collection`](https://www.mongodb.com/docs/database-tools/mongorestore/#std-option-mongorestore.--collection), [`mongorestore`](https://www.mongodb.com/docs/database-tools/mongorestore/#std-program-mongorestore) takes the collection name from the input filename. If the input file has an extension, MongoDB omits the extension of the file from the collection name.

    ```
    mongorestore --db=reporting --collection=empsalaries dump/test/salaries.bson
    ```