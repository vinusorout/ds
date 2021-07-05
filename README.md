DS Personal learning
# Array:

Static Array: need to specify no of element ahead of time (In JS we cant create static array)
Dynamic Array: at dynamic

* lookup O(1)
* push O(1)
* insert O(n)

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

* insert O(1) // as it doesnt store as per indexing and doesnt need shifting of index like in array
* lookup O(1)
* delete O(1) // as it doesnt store as per indexing and doesnt need shifting of index like in array
* search O(1)

Main CONS(Not big) with Hash Table:
  Hash Collisions
    Some time we get same address for multiple keys and at that point computer need to store both the keys at same address, in this case computer save the next data in a seperate address but link it to the earlier address like a linked list (the linked list is just a example there are other method too which solves this collisions issue while saving a data)
    So at time of collisions the bigo for hash table is O(n)

# Linked List:
Singly:
'a'(Head) --> 'b' --> 'c'(Tail) --> null

Doubly:
'a'(Head) --> <-- 'b' --> <-- 'c'(Tail) --> null

* prepend O(1)
* append O(1)
* lookup O(n)
* insert O(n)
* delete O(n)

# Stacks:
LIFO

* lookup O(n)
* pop O(1)
* push O(1)
* peek O(1) // just to check top item, doesnt delete the top item like pop method

NOTE: Stacks should be build with arrays

# Queues
FIFO

* lookup O(n)
* enqueue O(1)
* dequeue O(1)
* peek O(1)

NOTE: creating queues using Array is not recomnded because with enqueue, you have to shift all the items of array. means O(n)

Queue should be implemented with Linked List.

# Trees

* 0 or more child nodes
* root node
* leaf nodes
* sub tree(part of tree)
* siblings

Binary trees:
* 0, 1 or 2 nodes
* lookup O(log n)
* insert O(log n)
* delete O(log n)

In unbalanced trees (where one side keeps growing like linked list) it becomes O(n) instead of O(log n)

## Breadth First Search BFS O(n)

* Starts with root, move left to right
* BFS takes more memory, as it needs to store all the child nodes of the nodes that it visit.

```js
var currentNode = rootNode;
var list = []; // traversal list, add items in this after visiting each node
var queue = [];
queue.push(currentNode);
while(queue.length > 0){
  currentNode = queue.shift(); // gets the items as per FIFO
  list.push(currentNode.value);
  if(currentNode.left){
    queue.push(currentNode.left);
  }
  if(currentNode.right){
    queue.push(currentNode.right);
  }
}
```

## Depth First Search DFS O(n)

* Top to bottom

    101
  
  33    105

* Inorder: 33, 101, 105

```js
// In order DFS, recursion
function traverseInOrder(node, list) { //current node, list containg our traversed data)
  if(node.left) {
    traverseInOrder(node.left, list);
  }
  list.push(node.value);
  if(node.right) {
    traverseInOrder(node.right, list);
  }
  return list;
}
// final call
var list = [];
traverseInOrder(rootNode, list);
```

* PreOrder: 101, 33, 105

```js
// In order DFS, recursion
function traversePreOrder(node, list) { //current node, list containg our traversed data)
  list.push(node.value); // in pre order we first add value to list, unlike inorder where we go to left first.
  if(node.left) {
    traversePreOrder(node.left, list);
  }
  
  if(node.right) {
    traversePreOrder(node.right, list);
  }
  return list;
}
// final call
var list = [];
traversePreOrder(rootNode, list);
```

* PostOrder: 33, 105, 101

```js
// In order DFS, recursion
function traversePostOrder(node, list) { //current node, list containg our traversed data)
  
  if(node.left) {
    traversePostOrder(node.left, list);
  }
  if(node.right) {
    traversePostOrder(node.right, list);
  }
  list.push(node.value); // in pre order we  add value to list in last, unlike inorder where we go to left first.
  return list;
}
// final call
var list = [];
traversePostOrder(rootNode, list);
```

### Qus
* If you know a solution is not far from the root of the tree: BFS
* If the tree is very deep and solutions are rare: BFS (DFS will take a lot of time as tree is deeper)
* If the tree is very wide: DFS (BFS will need too much memory)
* If solutions are frequent but located deep in the tree: DFS
* Determining whether a path exists between two nodes: DFS
* Finding the shortest path: BFS


# Sorting
Elementary Sorts: Bubble, Insertion, Selection

## Bubble Sort:

* least efficient O(n ^ 2)
* Doesnt required any other memory so space complexity is O(1)
* compare two elements and sorts
* in first iteration move the largest no to last
* in second iteration move the second largest no to second last position
* let say ---> 2, 3, 1, 5, 4 (first compare 2, 3 no change)
* second compare 3,1 ->> change it to 1, 3
* third compare 3, 5 --> no change
* fourth compare 5, 4 --> change it to 4, 5
* First iteration result --> 2, 1, 3, 4, 5
* First compare 2, 1 --> change it to 1, 2
* Second compare 2, 3 --> no change
* third compare 3,4 --> no change
* fourth compare 4, 5 --> no change
* Second iteration result --> 1, 2, 3, 4, 5

```js
var arr = [3,2, 1,5,4];
function bubbleSort(input){
	for(let i = 0; i < input.length; i++) {
		for(let j =0; j < input.length - 1; j++) { (Nested Loops)
			if(input[j] > input [j+1]) {
				var temp = input[j];
				input[j] = input[j+1];
				input[j+1] = temp;
			}
		}
	}
}
bubbleSort(arr);
```

## Selection Sort

* Search the smallest element from the entire array and swap it to with the first
* Then second smallest and swap it with second, and so on
* least efficient O(n ^ 2)
* Doesnt required any other memory so space complexity is O(1)

```js
var arr = [3,2, 1,5,4];
function selectionSort(input){
	for(let i = 0; i < input.length; i++) {
    let min = i;
    let temp = input[min];
		for(let j = i+1; j < input.length - 1; j++) { (Nested Loops)
			if(input[j] < input[min]) {
				// update j if current is lower than what we had earlier
        min = j;
			}
		}
    input[i] = input[min];
    input[min] = temp;
	}
}
selectionSort(arr);
```

## Insertion Sort

* It is also least efficient, but work best when you already have nearly sorted list.
* Starts with first and as we see smallaest next, move that to first place or the place where it best fit and shift the next items.

```js
var arr = [3,2, 1,5,4];
function insertionSort(input){
	for(let i = 0; i < input.length; i++) {
		if(input[i] < input[0]) {
			// move no to the first position
			input.unshift(input.splice(i,1)[0]);
		} else {
			// find where no should go
			for (let j = 1; j < i; j++) {
				if(input[i] > input[j-1] && input[i] < input[j]) {
					input.splice(j, 0, input.splice(i,1)[0]);
				}
			}
		}
	}
}
insertionSort(arr);
```

## Merge Sort

* Divide and Conquer
* faster than elementary sorts
* O(n * log n)
* Space complexity is O(n) as we need to store the items


```js
var arr = [3,2, 1,5,4];
function mergeSort(array) {
	if(array.length === 1) {
		return array;
	}
	// split array into left and right
	const length = array.length;
	const middle = Math.floor(length / 2);
	const left = array.slice(0, middle);
	const right = array.splice(middle);
	return merge(
		mergeSort(left),
		mergeSort(right)
		);
}

function merge(left, right) {
	const result = [];
	let leftIndex = 0;
	let rightIndex = 0;
	while(leftIndex < left.length && rightIndex < right.length) {
		if(left[leftIndex] < right[rightIndex]) {
			result.push[left[leftIndex]);
			leftIndex++;
		} else {
			result.push(right[rightIndex]);
			rightIndex++;
		}
	}
	return result.concat(left.slice(leftIndex)).concat(right.slice(rightIndex));
}
mergeSort(arr);
```

## Quick Sort

* Divide and Conquer
* faster than elementary sorts
* O(n * log n)
* Space complexity is O(n log n) better than Merge
* Quick sort divide the list as per pivot value(genarrally last value in array is considered as pivot value)
* element smaller than pivot consider in left list and greater are consider in right array.




