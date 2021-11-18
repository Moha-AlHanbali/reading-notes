[Home](README.md)

<br>

# HashTables

<br>

## Readings from [Hashtables](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-30/resources/Hashtables.html)

<br>

### Overview

<br>

- Terminology
  - `Hash`
    - A hash is the result of some algorithm taking an incoming string and converting it into a value that could be used for either security or some other purpose.
    - In the case of a hashtable, it is used to determine the index of the array.
  - `Buckets` 
    - A bucket is what is contained in each index of the array of the hashtable. Each index is a bucket. An index could potentially contain multiple key/value pairs if a collision occurs.
  - `Collisions` 
    - A collision is what happens when more than one key gets hashed to the same location of the hashtable.

<br>

### Usage

<br>

- Hold unique values
- Dictionary
- Library

<br>

### What are Hash Tables?

<br>

> Hashtables are a data structure that utilize key value `pairs`.

> This means every `Node` or `Bucket` has both a `key`, and a `value`.

> The basic idea of a hashtable is the ability to store the key into this data structure, and quickly retrieve the value.

> This is done through what we call a `hash`.

> A `hash` is the ability to encode the key that will eventually map to a specific location in the data structure that we can look at directly to retrieve the value.

> Since we are able to `hash` our key and determine the exact location where our value is stored, we can do a lookup in an `O(1)` time complexity.

> Basically, the hash function takes a key and returns an integer.

> We use the integer to determine where the key/value pair should be placed in the array.

> The hash code is calculated in constant time and writing to an array at one index is `O(1)` so the hash map has `O(1)` access.

<br>

### Structure

<br>

#### Hash

<br>

> Basically, a hash code turns a key into an integer.

> It’s very important that hash codes are deterministic: their output is determined only by their input.

> Hash codes should never have randomness to them.

> The same key should always produce the same hash code.

<br>

#### Creating a Hash

<br>

> A hashtable traditionally is created from an array.

> I always like the size 1024. this is important for index placement.
 
> After you have created your array of the appropriate size, do some sort of logic to turn that “key” into a numeric number value.

- Here is a possible suggestion:
  - Add or multiply all the ASCII values together.
  - Multiply it by a prime number such as 599.
  - Use modulo to get the remainder of the result, when divided by the total size of the array.
  - Insert into the array at that index.

<br>

> Each index of the array can hold many types of values.

> The trick is how the values are stored in comparison to efficiency.

> Each Index of the array contain “buckets”.

> Each of these “buckets” holds one key/value pair combination.

> When there is no entry in a specific bucket, the buckets (each index of the array) all start null.

> The hash table starts each bucket empty and overwrites their value once a key generates a hashCode that corresponds with an index.

<br>

#### Collisions

<br>

> A collision occurs when more than one key hashes to the same index in an array.

> As mentioned earlier, a “perfect hash” will never have any collisions.

> To put this into perspective, the worst possible hash is one that hashes every single key to the same exact index of an array.

> The more keys you have hashed to a specific index, the more key/value pair combos you can potentially have.

<br>

> The hash map needs to be able to handle two keys resolving to the same index.

> If two keys ever ultimately resolved to the same index, then two calls to .Add(key, val) with different keys would overwrite each other.

<br>

> Collisions are solved by changing the initial state of the buckets.

> Instead of starting them all as null we can initialize a `LinkedList` in each one! Now if two keys resolve to the same index in the array then their `key/value` pairs can be stored as a `node` in a `linked list`.

> Each index in the array is called a “bucket” because it can store multiple key/value pairs.

<br>

- Hash maps do this to store values:
  - accept a key
  - calculate the hash of the key
  - use modulus to convert the hash into an array index
  - store the key with the value by appending both to the end of a linked list

<br>

- Hash maps do this to read value:
  - accept a key
  - calculate the hash of the key
  - use modulus to convert the hash into an array index
  - use the array index to access the short LinkedList representing a bucket
  - search through the bucket looking for a node with a key/value pair that matches the key you were given

<br>

#### Bucket Sizes

<br>

> Hash Maps can have any number of buckets.

> If a hash map has only a few buckets it will be densely full and have many collisions.

> If a hash map has more buckets it will be more sparsely populated, there will be less collisions, but there may be a lot of extra empty space.

> It’s possible to compute the “`load factor`” of a hash table.

> The `load factor` tells us something about how full the hash table is.

> A hash table can start with only a few buckets, calculate it’s own `load factor`, recognize when it gets too full and automatically grow and add more buckets to itself to accommodate more data.

<br>

### Internal Methods

<br>

#### Add()

<br>

- When adding a new key/value pair to a hashtable:
  - Send the key to the GetHash method.
  - Once you determine the index of where it should be placed, go to that index
  - Check if something exists at that index already, if it doesn’t, add it with the key/value pair.
  - If something does exist, add the new key/value pair to the data structure within that bucket.

<br>

#### Find()

<br>

> The `Find` takes in a key, gets the Hash, and goes to the index location specified.

> Once at the index location is found in the array, it is then the responsibility of the algorithm the iterate through the bucket and see if the key exists and return the value.

<br>

#### Contains()

<br>

> The `Contains` method will accept a key, and return a bool on if that key exists inside the hashtable.

> The best way to do this is to have the `contains` call the GetHash and check the hashtable if the key exists in the table given the index returned.

<br>

#### GetHash()

<br>

> The `GetHash` will accept a key as a string, conduct the hash, and then return the index of the array where the key/value should be placed.

<br>

## Readings from [Basics of Hash Tables](https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/)

<br>

### Overview

<br>

> Hashing is a technique that is used to uniquely identify a specific object from a group of similar objects.

> Assume that you have an object and you want to assign a key to it to make searching easy.

> To store the key/value pair, you can use a simple array like a data structure where keys (integers) can be used directly as an index to store values.

> However, in cases where the keys are large and cannot be used directly as an index, you should use hashing.

<br>

> In hashing, large keys are converted into small keys by using hash functions.

> The values are then stored in a data structure called hash table.

> The idea of hashing is to distribute entries (key/value pairs) uniformly across an array.

> Each element is assigned a key (converted key). By using that key you can access the element in `O(1)` time.

> Using the key, the algorithm (hash function) computes an index that suggests where an entry can be found or inserted.

<br>

- Hashing is implemented in two steps:
  - An element is converted into an integer by using a hash function. This element can be used as an index to store the original element, which falls into the hash table.
  - The element is stored in the hash table where it can be quickly retrieved using hashed key.

<br>

### Hash function

<br>

> A hash function is any function that can be used to map a data set of an arbitrary size to a data set of a fixed size, which falls into the hash table.

> The values returned by a hash function are called hash values, hash codes, hash sums, or simply hashes.

- It is important to have a good hash function with the following basic requirements:
  - `Easy to compute`: It should be easy to compute and must not become an algorithm in itself.
  - `Uniform distribution`: It should provide a uniform distribution across the hash table and should not result in clustering.
  - `Less collisions`: Collisions occur when pairs of elements are mapped to the same hash value. These should be avoided.

<br>

### Hash table

<br>

> A `hash table` is a data structure that is used to store `keys/value` pairs.

> It uses a hash function to compute an index into an array in which an element will be inserted or searched.

> By using a good hash function, hashing can work well. Under reasonable assumptions, the average time required to search for an element in a hash table is `O(1)`.

<br>

### Collision resolution techniques

<br>

> Separate chaining is one of the most commonly used collision resolution techniques.

> It is usually implemented using linked lists. In separate chaining, each element of the hash table is a linked list.

> To store an element in the hash table you must insert it into a specific linked list.

> If there is any collision (i.e. two different elements have same hash value) then store both the elements in the same linked list.

<br>

### Linear probing (open addressing or closed hashing)

<br>

> In open addressing, instead of in linked lists, all entry records are stored in the array itself.

> When a new entry has to be inserted, the hash index of the hashed value is computed and then the array is examined (starting with the hashed index).

> If the slot at the hashed index is unoccupied, then the entry record is inserted in slot at the hashed index else it proceeds in some probe sequence until it finds an unoccupied slot.

<br>

### Quadratic Probing

<br>

> Quadratic probing is similar to linear probing and the only difference is the interval between successive probes or entry slots.

> Here, when the slot at a hashed index for an entry record is already occupied, you must start traversing until you find an unoccupied slot.

> The interval between slots is computed by adding the successive value of an arbitrary polynomial in the original hashed index.

<br>

### Double hashing

<br>

> Double hashing is similar to linear probing and the only difference is the interval between successive probes.

> Here, the interval between probes is computed by using two hash functions.
