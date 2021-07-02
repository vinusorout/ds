DS Personal learning
# Array:

Static Array: need to specify no of element ahead of time (In JS we cant create static array)
Dynamic Array: at dynamic

lookup O(1)
push O(1)
insert O(n)
```js
strings = ['a', 'b', 'c'];
strings.unshift('x'); // => ['x', 'a', 'b', 'c'] O(n)
strings.splice(2, 0, 'new'); // => ['x', 'a', 'new', 'b', 'c'] // splice 2(go to index 2), 0(delete next 0 elelemnts), then insert 'new' O(n)
// last parameter is optional
```
delete O(n)
```js
strings = ['a', 'b'];

```

# Hash Tables
Maps, Dictionary etc
Objects is JS are Hash Tables
key, Value pairs

Every Hash DS uses a hash function internally like md5 hash function, it convert the key as per the hash and store its value at this hash memory. Now while retrieving it use this same hash values, this makes it very fast. Unlike arrays where we have ordered indexes.

insert O(1) // as it doesnt store as per indexing and doesnt need shifting of index like in array
lookup O(1)
delete O(1) // as it doesnt store as per indexing and doesnt need shifting of index like in array
search O(1)

Main CONS(Not big) with Hash Table:
  Hash Collisions
    Some time we get same address for multiple keys and at that point computer need to store both the keys at same address, in this case computer save the next data in a seperate address but link it to the earlier address like a linked list (the linked list is just a example there are other method too which solves this collisions issue while saving a data)
    So at time of collisions the bigo for hash table is O(n)

# Linked List:
Singly:
'a'(Head) --> 'b' --> 'c'(Tail) --> null

Doubly:
'a'(Head) --> <-- 'b' --> <-- 'c'(Tail) --> null

prepend O(1)
append O(1)
lookup O(n)
insert O(n)
delete O(n)

# Stacks:
LIFO

lookup O(n)
pop O(1)
push O(1)
peek O(1) // just to check top item, doesnt delete the top item like pop method

NOTE: Stacks should be build with arrays

# Queues
FIFO

lookup O(n)
enqueue O(1)
dequeue O(1)
peek O(1)

NOTE: creating queues using Array is not recomnded because with enqueue, you have to shift all the items of array. means O(n)
Queue should be implemented with Linked List.

