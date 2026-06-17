# Database CLI Cheatsheet

Panduan lengkap untuk **PostgreSQL**, **MySQL**, **Redis**, dan **MongoDB**.

---

## 🐘 PostgreSQL (psql)

### Connect to Database

```bash
psql -U username -d dbname   # Connect ke database
psql -h localhost -U postgres # Connect ke localhost
psql                         # Connect dengan default
```

### Basic Commands

```sql
\l                           # List databases
\c dbname                    # Connect ke database
\dt                          # List tables
\d tablename                 # Describe table
\du                          # List users
\dn                          # List schemas
\df                          # List functions
\dv                          # List views
\q                           # Quit psql
```

### Common Queries

```sql
SELECT * FROM table;         -- Select all
CREATE DATABASE dbname;      -- Create database
DROP DATABASE dbname;        -- Delete database
CREATE USER user WITH PASSWORD 'pass';  -- Create user
GRANT ALL ON DATABASE dbname TO user;   -- Grant permissions
```

### Backup & Restore

```bash
pg_dump dbname > backup.sql  # Backup database
psql dbname < backup.sql     # Restore database
pg_dumpall > all.sql         # Backup all databases
```

---

## 🐬 MySQL/MariaDB

### Connect to Database

```bash
mysql -u username -p         # Connect ke database
mysql -u root -p             # Connect sebagai root
mysql -h hostname -u user -p # Connect ke remote host
```

### Basic Commands

```sql
SHOW DATABASES;              # List databases
USE dbname;                  # Select database
SHOW TABLES;                 # List tables
DESCRIBE tablename;          # Describe table
SHOW COLUMNS FROM tablename; # Show columns
SHOW USERS;                  # List users
EXIT;                        # Quit mysql
```

### Common Queries

```sql
SELECT * FROM table;         -- Select all
CREATE DATABASE dbname;      -- Create database
DROP DATABASE dbname;        -- Delete database
CREATE USER 'user'@'localhost' IDENTIFIED BY 'pass';  -- Create user
GRANT ALL ON dbname.* TO 'user'@'localhost';          -- Grant permissions
FLUSH PRIVILEGES;            -- Reload privileges
```

### Backup & Restore

```bash
mysqldump -u user -p dbname > backup.sql  # Backup
mysql -u user -p dbname < backup.sql      # Restore
mysqldump --all-databases > all.sql       # Backup all
```

---

## 🔴 Redis

### Connect to Redis

```bash
redis-cli                    # Connect ke Redis
redis-cli -h localhost -p 6379 # Connect dengan host/port
redis-cli -a password        # Connect dengan password
```

### Basic Commands

```bash
KEYS *                       # List semua keys
GET key                      # Get value
SET key value                # Set value
DEL key                      # Delete key
EXISTS key                   # Check if key exists
TTL key                      # Time to live
TYPE key                     # Get key type
DBSIZE                       # Count keys
INFO                         # Server info
PING                         # Test connection
FLUSHALL                     # Hapus semua data
FLUSHDB                      # Hapus database saat ini
```

### Data Types

```bash
# Strings
SET name "value"
GET name

# Lists
LPUSH mylist "item"
RPUSH mylist "item"
LRANGE mylist 0 -1

# Sets
SADD myset "item"
SMEMBERS myset

# Hashes
HSET myhash field value
HGETALL myhash

# Sorted Sets
ZADD myzset 1 "member"
ZRANGE myzset 0 -1 WITHSCORES
```

### Pub/Sub

```bash
SUBSCRIBE channel            # Subscribe to channel
PUBLISH channel "message"    # Publish message
```

---

## 🍃 MongoDB (mongosh)

### Connect to MongoDB

```bash
mongosh                      # Connect ke MongoDB
mongosh mongodb://localhost:27017 # Connect dengan URI
mongosh -u user -p pass      # Connect dengan auth
```

### Basic Commands

```javascript
show dbs                     # List databases
use dbname                   # Select database
db                           # Show current database
show collections             # List collections
db.collection.find()         # Query documents
db.collection.findOne()      # Find one document
db.collection.insertOne({})  # Insert document
db.collection.updateOne({}, {$set: {}}) # Update
db.collection.deleteOne({})  # Delete document
db.collection.drop()         # Drop collection
db.dropDatabase()            # Drop database
exit                         # Quit mongosh
```

### Common Queries

```javascript
// Find all
db.users.find()

// Find with filter
db.users.find({ age: { $gt: 18 } })

// Find specific fields
db.users.find({}, { name: 1, email: 1 })

// Sort
db.users.find().sort({ name: 1 })

// Limit
db.users.find().limit(10)

// Count
db.users.countDocuments()

// Aggregate
db.users.aggregate([
  { $match: { status: "active" } },
  { $group: { _id: "$country", total: { $sum: 1 } } }
])
```

### Indexes

```javascript
db.collection.createIndex({ field: 1 })     # Create index
db.collection.getIndexes()                  # List indexes
db.collection.dropIndex("index_name")       # Drop index
```

### Backup & Restore

```bash
mongodump --db dbname -o /backup/    # Backup database
mongorestore --db dbname /backup/    # Restore database
```

---

## 🎯 Quick Reference

| Database | Command | Description |
|----------|---------|-------------|
| PostgreSQL | `\l` | List databases |
| PostgreSQL | `\dt` | List tables |
| MySQL | `SHOW DATABASES;` | List databases |
| MySQL | `SHOW TABLES;` | List tables |
| Redis | `KEYS *` | List all keys |
| Redis | `GET/SET` | Get/Set value |
| MongoDB | `show dbs` | List databases |
| MongoDB | `db.col.find()` | Query documents |

---

> Last Updated: 17-Juni-2026
