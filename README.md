Download Link: https://assignmentchef.com/product/solved-cs1332-homework4-hashmap
<br>
You are to code an ExternalChainingHashMap, a key-value hash map with an external chaining collision resolution strategy. A HashMap maps unique keys to values and allows <em>O</em>(1) average case lookup of a value when the key is known.

The table should <strong>not </strong>contain duplicate keys, but <strong>can </strong>contain duplicate values. In the event of trying to add a duplicate key, replace the value in the existing (key, value) pair with the new value and return the old value.

You should implement two constructors for this HashMap. As per the javadocs, you should use constructor chaining to implement the no-arg constructor.

<h2>Capacity</h2>

The starting capacity of the ExternalChainingHashMap using the default constructor should be the constant INITIAL CAPACITY defined in ExternalChainingHashMap.java. Reference the constant as-is. Do <strong>not </strong>simply copy the value of the constant. Do <strong>not </strong>change the constant. Do <strong>not </strong>regrow the backing array when removing elements.

If adding to the table would cause the load factor (LF) to <strong>exceed </strong>(greater than, not greater than or equal to) the max load factor constant provided in the java file, the table should be resized to have a capacity of 2<em>n </em>+ 1, where <em>n </em>is the current capacity before adding the parameterized element. See the javadocs for specific instructions on when to resize. There is a method called resizeBackingTable that you should use for resizing.

<h2>Hash and Compression Functions</h2>

You should <strong>not </strong>write your own hash functions for this assignment. Instead, use the hashCode() method that every Object has. For the compression function, mod by table length first, then take the absolute value (it must be done in this order to prevent overflow in certain cases). As a reminder, you should be using the hashCode() method on <strong>only the keys </strong>(and not the ExternalChainingMapEntry object itself) since that’s what is used to look up the values. After converting a key to an integer with a hash function, it must be compressed to fit in the array backing the HashMap.

<h2>External Chaining</h2>

Your hash map must implement an external chaining collision policy. That is, in the event of a collision, colliding entries are stored as a chain of ExternalChainingMapEntry objects at that index. As such, if you need to search for a key, you’ll need to traverse the entire chain at the hashed index to look for it. See ExternalChainingMapEntry.java to see what is stored and what methods are available for use; do <strong>not </strong>use Java’s LinkedList to handle the chaining functionality.

<h2>Adding</h2>

When adding a key/value pair to a hash map, add the pair to the front of the chain in the correct position. Also remember that keys are unique in a hash map, so you must ensure that duplicate keys are not added. Each index of the table should point to an ExternalChainingMapEntry that represents the head of a linked list. That linked list contains all elements that collide at that index.

<h2>Removing</h2>

When removing a key/value pair from a hash map using external chaining, you can safely remove the item unlike in open addressing techniques such as linear probing where you must use a DEL marker. Removing from a chain is very similar to removing from a Singly-Linked List, treating the first table entry as the head, so refer to your notes and homework assignments from earlier in the course if you need a refresher. As usual, if the entry you are removing is the only entry at that index, you should make sure to null out that spot rather than leaving it there.