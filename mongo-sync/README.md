# Sync mongodb script
I edit shell script for make it work in mongo current versions.

## Credit
this script from https://github.com/sheharyarn/mongo-sync.git

## Introduction
mongo-sync is use for dump mongodb from difference host. In technically this script shouldn't use with shading,
Because it's use mongodump and mongorestore.
https://docs.mongodb.com/manual/tutorial/backup-sharded-cluster-with-database-dumps/

## Usage

- Edit `config.yml` and insert your configuration details

- Use the script like this:
	
	```bash
	./mongo-sync push [options]		# Push DB to Remote
	./mongo-sync pull [options]		# Pull DB to Local
	```
- Options

	```
	-y  # Skip confirmation
	--config alternate-config-file.yml
	```

## Practice
use docker-compose and run script
- create DB and add docs
- go to another service
- run this script