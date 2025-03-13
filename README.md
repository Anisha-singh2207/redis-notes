# INTRODUCTION TO REDIS
Redis (REmote DIctionary Server) is an open-source, in-memory data structure store used as a database, cache, and message broker. It is known for its speed, simplicity, and powerful features, making it a popular choice in many modern applications.

In-memory storage: Redis stores data in memory (RAM) rather than on disk, making data retrieval extremely fast. This is a major reason why Redis is often used for caching purposes.

# INSTALLATION
1.Search reddis stack on web browser
2.click on redis docker in docs
3.Copy the exact same command docker run -d --name redis-stack -p 6379:6379 -p 8001:8001 redis/redis-stack:latest and run it on the terminal 
4.Once the image is downloaded it will be shown in docker daemon
5.Go to any browser and type localhost:8001
6.YOU will see redis GUI click submit
7.Go to terminal type redis-cli and then ping .
8.If you will receive PONG as message then all set :)

# Redis Strings

1.STRING
The following is the CLI command 
![image](https://github.com/user-attachments/assets/649f4dec-6e82-4a99-841b-bab41d1fa812)

The followwing is the node js command
![image](https://github.com/user-attachments/assets/49e9d5b5-e0da-474a-a078-f3a601c29909)

# Getting and setting Strings
SET stores a string value.
SETNX stores a string value only if the key doesn't already exist. Useful for implementing locks.
GET retrieves a string value.
MGET retrieves multiple string values in a single operation.

The ability to set or retrieve the value of multiple keys in a single command is also useful for reduced latency. For this reason there are the MSET and MGET commands:

![image](https://github.com/user-attachments/assets/db82512e-68e0-49e8-a6b1-0a7e484940ab)


# Redis lists
Redis lists are linked lists of string values. Redis lists are frequently used to:

Implement stacks and queues.
Build queue management for background worker systems.

 # Basic commands
LPUSH adds a new element to the head of a list; RPUSH adds to the tail.
LPOP removes and returns an element from the head of a list; RPOP does the same but from the tails of a list.
LLEN returns the length of a list.
LMOVE atomically moves elements from one list to another.
LRANGE extracts a range of elements from a list.
LTRIM reduces a list to the specified range of elements.

# Blocking commands
Lists support several blocking commands. For example:

BLPOP removes and returns an element from the head of a list. If the list is empty, the command blocks until an element becomes available or until the specified timeout is reached.
BLMOVE atomically moves elements from a source list to a target list. If the source list is empty, the command will block until a new element becomes available.

Treat a list like a queue (first in, first out):
![image](https://github.com/user-attachments/assets/68cc39e9-732e-46ee-8d22-dfd043b1880b)

Treat a list like a stack (first in, last out):

![image](https://github.com/user-attachments/assets/91379afa-5808-438e-8ccb-22f90eaf8c73)

# Check the length of a list:
![image](https://github.com/user-attachments/assets/c4feb621-da54-4eba-8abf-e28bb19837b1)

The LPUSH command adds a new element into a list, on the left (at the head), while the RPUSH command adds a new element into a list, on the right (at the tail). Finally the LRANGE command extracts ranges of elements from lists:

Note that LRANGE takes two indexes, the first and the last element of the range to return. Both the indexes can be negative, telling Redis to start counting from the end: so -1 is the last element, -2 is the penultimate element of the list, and so forth.

As you can see RPUSH appended the elements on the right of the list, while the final LPUSH appended the element on the left.

![image](https://github.com/user-attachments/assets/8b66ffd9-ff72-4013-ae2c-b5b63bb24320)


# Redis sets
A Redis set is an unordered collection of unique strings (members). You can use Redis sets to efficiently:

Track unique items (e.g., track all unique IP addresses accessing a given blog post).
Represent relations (e.g., the set of all users with a given role).
Perform common set operations such as intersection, unions, and differences

# Basic commands
SADD adds a new member to a set.
SREM removes the specified member from the set.
SISMEMBER tests a string for set membership.
SINTER returns the set of members that two or more sets have in common (i.e., the intersection).
SCARD returns the size (a.k.a. cardinality) of a set

Store the sets of bikes racing in France and the USA. Note that if you add a member that already exists, it will be ignored.

![image](https://github.com/user-attachments/assets/5f5484f4-c3c2-4660-bceb-9023f1ec0f70)

Check whether bike:1 or bike:2 are racing in the US.
![image](https://github.com/user-attachments/assets/e48dac7b-3247-4de1-8d69-b5332dd2d673)

Which bikes are competing in both races?
![image](https://github.com/user-attachments/assets/1ee550aa-7ad9-479b-8ac8-b247da62a134)

The SADD command adds new elements to a set. It's also possible to do a number of other operations against sets like testing if a given element already exists, performing the intersection, union or difference between multiple sets, and so forth.


# Redis hashes

Redis hashes are record types structured as collections of field-value pairs. You can use hashes to represent basic objects and to store groupings of counters, among other things.

![image](https://github.com/user-attachments/assets/798e65a1-5e5b-43a0-824b-6c9311eae41c)

![image](https://github.com/user-attachments/assets/525524fc-25ed-4e12-867d-1fe3a00b2ec8)

The command HSET sets multiple fields of the hash, while HGET retrieves a single field. HMGET is similar to HGET but returns an array of values:

![image](https://github.com/user-attachments/assets/44dc50af-a187-42aa-a836-b8064c930c8b)


# Basic commands
HSET: sets the value of one or more fields on a hash.
HGET: returns the value at a given field.
HMGET: returns the values at one or more given fields.
HINCRBY: increments the value at a given field by the integer provided.

# Redis sorted sets

A Redis sorted set is a collection of unique strings (members) ordered by an associated score. When more than one string has the same score, the strings are ordered lexicographically. Some use cases for sorted sets include:

Leaderboards. For example, you can use sorted sets to easily maintain ordered lists of the highest scores in a massive online game.
Rate limiters. In particular, you can use a sorted set to build a sliding-window rate limiter to prevent excessive API requests.

As you can see ZADD is similar to SADD, but takes one additional argument (placed before the element to be added) which is the score. ZADD is also variadic, so you are free to specify multiple score-value pairs, as shown in the example above.

![image](https://github.com/user-attachments/assets/eb79c5ad-f9e6-4be7-93a2-48ab6830f557)

The list are arranges in arranged in sorted as well as reverse sorted order
![image](https://github.com/user-attachments/assets/b798741a-ede6-44c9-9af1-866a459cd427)

Note: 0 and -1 means from element index 0 to the last element (-1 works here just as it does in the case of the LRANGE command).


# Redis geospatial

Redis geospatial indexes let you store coordinates and search for them. This data structure is useful for finding nearby points within a given radius or bounding box.

 # Basic commands
GEOADD adds a location to a given geospatial index (note that longitude comes before latitude with this command).
GEOSEARCH returns locations with a given radius or a bounding box.

Suppose you're building a mobile app that lets you find all of the bike rental stations closest to your current location.

Add several locations to a geospatial index:

![image](https://github.com/user-attachments/assets/4fdc1560-368d-46ae-be76-fff774ecc35d)

Find all locations within a 5 kilometer radius of a given location, and return the distance to each location:

![image](https://github.com/user-attachments/assets/210042b4-1456-4a73-a279-93147994d633)

# Probabilistic data structures in Redis
Probabilistic data structures give approximations of statistics such as counts, frequencies, and rankings rather than precise values. The advantage of using approximations is that they are adequate for many common purposes but are much more efficient to calculate. They sometimes have other advantages too, such as obfuscating times, locations, and other sensitive data.

Probabilistic data structures are not available by default in the basic Redis server, so you should install Redis Stack or Redis Enterprise, both of which include probabilistic structures and other useful modules. See Install Redis Stack or Install Redis Enterprise for full installation instructions.

HyperLogLog
HyperLogLog is a probabilistic data structure that estimates the cardinality of a set.

Bloom filter
Bloom filters are a probabilistic data structure that checks for presence of an item in a set

Cuckoo filter
Cuckoo filters are a probabilistic data structure that checks for presence of an element in a set

t-digest
t-digest is a probabilistic data structure that allows you to estimate the percentile of a data stream.

Top-K
Top-K is a probabilistic data structure that allows you to find the most frequent items in a data stream.

Count-min sketch
Count-min sketch is a probabilistic data structure that estimates the frequency of an element in a data stream.

# JSON support for Redis
The JSON capability of Redis Stack provides JavaScript Object Notation (JSON) support for Redis. It lets you store, update, and retrieve JSON values in a Redis database, similar to any other Redis data type. Redis JSON also works seamlessly with the Redis Query Engine to let you index and query JSON documents.

# Primary features
Full support for the JSON standard
A JSONPath syntax for selecting/updating elements inside documents (see JSONPath syntax)
Documents stored as binary data in a tree structure, allowing fast access to sub-elements
Typed atomic operations for all JSON value types

The first JSON command to try is JSON.SET, which sets a Redis key with a JSON value. JSON.SET accepts all JSON value types. This example creates a JSON string:

![image](https://github.com/user-attachments/assets/277c523d-4a94-467c-bf88-a0fce8f40cec)

Here are a few more string operations. JSON.STRLEN tells you the length of the string, and you can append another string to it with JSON.STRAPPEND.

![image](https://github.com/user-attachments/assets/6ede7240-c91c-47eb-9733-4a9aee1d6f0b)

Numbers can be incremented and multiplied:
![image](https://github.com/user-attachments/assets/359d3653-15b9-47a7-a0c2-80dd7a6a4402)

# Redis JSON RAM Usage

Every key in Redis takes memory and requires at least the amount of RAM to store the key name, as well as some per-key overhead that Redis uses. On top of that, the value in the key also requires RAM.

Redis JSON stores JSON values as binary data after deserializing them. This representation is often more expensive, size-wise, than the serialized form. The JSON data type uses at least 24 bytes (on 64-bit architectures) for every value, as can be seen by sampling an empty string with the JSON.DEBUG MEMORY command:


















