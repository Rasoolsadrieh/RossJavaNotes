# Collections

## The problem

-   Array object within Java is limited to work with.
-   Array is immutable and limited set of useful methods.
    -   cannot change the size of the array once initialized
-   Create my own custom version of a data structure
    -   LOT OF WORK
    -   Likley poorly optimized
    -   Difficult to share between other developers

## The solution

-   Insert collection framework! Woo!
-   Called a framework (more akin to library).
-   Provides interfaces and classes
    -   easily manage groups of objs
    -   Designed to store a group of objs and provide a lot of useful methods
-

## Inheritance hierarchy (Collection API)

-   All are interfaces

1. Iterable(I)
2. Collection(I) extends Iterable()
    1. Set(I) extends Collection
    2. List(I) extends Collection
    3. Queue(I) extends Collection

![Inheritance Hierarchy](https://techvidvan.com/tutorials/wp-content/uploads/sites/2/2020/03/collection-framework-hierarchy-in-java.jpg)

### List

-   An ordered collection.
    -   We have it indexed
    -   insertion (default)
    -   sorted order
-   Can contain duplicate elements
-   Primitive automatically converted to corresponding wrapper types
-   Access via index (positional)
    -   get, set, add, addAll, remove
-   Child Classes
    -   ArrayList
    -   LinkedList

### Set

-   Does not allow duplicate values
-   Elements are not stored in order (not guaranteed order)
-   Only inherits methods fromt he collections interface
-   Child Classes:
    -   HashSet
    -   LinkedHashSet
    -

### Queue

-   A data structure that holds the elements prior to processing.
    -   focused around insertion order
    -   Analogous to a line
-   First in first out(FIFO)
-   Last in last out(LILO)
    -   Examples
        -   Spotify
        -   Restaurant
        -   Animation
-   **_ORDER IS IMPORTANT_**
-   We hve to access in the order they were inserted
-   Child Class - LinkedList

## Map

-   **_isn't a true collection_**
-   Key-value pair
    -   {["key1",value1],["key2",value2] }

```java
// Basic operations
Map<String,Integer> map = Map.of("A",3,"B",5,"Z",10)
// Output: {Z=10, A=3, B=5}
// Remember Class.of is immutable

map.get("Z")
// output: 10

map.size()

map.isEmpty()

map.keySet()
// [Z,A,B]

map.values()
// [10,3,5]

map.containsValue(4)
// Output: false


Map<String,Integer> map = new HashMap<>(map);

hashmap.put("F", 5)
// Adds "F" with value of 5

hashmap.put("Z",11) //Returns previous value of "Z"
// Output: 10

```

## Types of Maps

-   **HashMap**
    -   unsorted & unorder
    -   can store key with null value
-   **HashTable**
    -   Synchronized
    -   cannot sotre null value
-   **LinkedHashMap**
    -   insertion order is maintained
    -   slower insertion and deletion
    -   iteration fater
-   **TreeMap**
    -   sorted order is maintained
    -   implements NavigableMap too

![Map Interface](https://4.bp.blogspot.com/-4FG1HxW0My4/WVjr8ftH0TI/AAAAAAAAAIA/_y876G2SqvcMF7tws-LVqSV5DhwWD943gCEwYBhgL/s1600/map-interface-1.png)

-   ArrayList is a collection
-   Collections allow us to mutate objects, rather than having re-create objects to help produce more efficient and clean code
-   Other collections
    -   List
        -   Cares about which position each object is in
        -   Elements can be added in by specifying position
            -   Where it should be added in
        -   If element is added without specifiying position
            -   appended to the end of the list

```java
//Any List generated with List.of() is immutable
List<String> words = List.of("Apple","Banana","Pear")

// To find how many words are present or if it's empty
words.size()
words.isEmpty()

// Used to obtain the value are the specified position in the List
words.get(0)


words.contain("Apple")
words.contain("Grape")

words.indexOf("Banana")

//ArrayList
//LinkedList

```

## ArrayLists

-   Java provides this to add and remove elements to an array without having to create a new array
-   Specify the only types available in the array (generics)
-   ArrayList<String> items = new ArrayList<String>()
    -   Two Methods to building an arrayList from a
    -   conversely can have a collection included with the constructor function to include that collect
    -

```java
// Iterate using an enhanced for loop with an array to add to the ArrayList
String[] cars = {"Audi", "VW", "Buick"}
List<String> carsList = new ArrayList<String>()
for(String car:cars){
    carsList.add(car)
}
// Create a list collection to be added to the new ArrayList
List<String> cars = List.of("Audi","VW","Buick")
List<String> carsList = new ArrayList<String>(cars)

// .add(value) used to end of list
carsList.add("GMC");
// .add(position, value) Will add to list at the specified position
carsList.add(1, "GMC");

List<String> newArray = {"Chevy", "Ford"}
// .addAll(array-of-values) can also be used to add a list to an existing list
carsList.addAll(newArray)

// .set(position, value) will convert the element at position to the provided value
carsList.set(2,"Honda")
carsList.set(2,"Honda")
carsList.set(2,"Honda")

// .remove(position)
carsList.remove(2)

// .remove(value)
carsList.remove("Honda")
```

## Sorting

```java
// List of Integers
List<Integer> numbers = [101,5,42,10123];
List<Integer> numbersAL = new ArrayList(numbers);

numbersAL.sort() // Error: Requires comparator
Collection.sort(numbersAL);; // Collections is a popular way to handle this sort without extra code

```

## LinkedList

-   Slower due to having to search through the entire array one element at a time to see what's linked together
-   _Hashing_ or _Hash Table_

    -   Example could be a Modulus of 13

    -   ArrayList
        -   Insertion and Deletion are slower comapred to LinkedList
        -   Almost constant time access
        -   Use Case:
            -   Very few modifications and access elements based on position
    -   LinkedList
        -   Elements are doubly linked - forward and backword
        -   Iteration is slower than ArrayList
        -   Faster Insertion and Deletion
        -   Use Case:
            -   Many insertions and deletions/modifications would be better

# Set Interface Collection

-   Extends the collection interface
-   Unique things only, does not allow dupes
-   If obj1.equals(obj2) only one of them can be set
-   Does not provide positional access

```java
Set<String> set = Set.of("Audi", "VW", "Buick");
set.add("Apple"); // Exception due to immutable object

Set<String> hashset = new HashSet<>(set)
hashset.add("Audi"); // fails due to duplication
hashset.add(2, "Honda"); // Fails due to lack of positional arugments being allowed
hashset.add("Honda"); // Finally adds Honda to our set
```

## Set use case

-   If you want **_unique_** arrays,
-   **TreeSet**
    -   If you wanted to keep the order **sorted**
-   **LinkedHashSet**
    -   If you wanted to keep the order as **inserted**
-   **HashSet**
    -   If you don't care about sorted or insertion order
    -   Most efficient of the three sets

## TreeSet

-   TreeSets alsos include the NavigableSet interface
    -   few other operations present that aren't commonly in the Collections Interface

```java
TreeSet<Integer> numbers = new TreeSet<Integer>(Set.of(65,43,34,11,99))

// floor floor returns the
numbers.floor(40)
numbers.floor(34) // returns 34, inclusive, so n <= 34
numbers.lower(34) // returns 11 exclusive, so n < 34

// ceiling returns the
numbers.ceiling(43) // returns 43, inclusive
numbers.higher(43) // returns 65, exclusive

//subSet(lowerRange,upperRange)
numbers.subSet(34,65) // lowerRange inclusive, upperRange exclusive
numbers.subset(34,false,65,true) // add booleans to change inclusivity

// HeadSet(Limit) & TailSet(Limit)
numbers.headSet(50)
numbers.tailSet(50)
```

```java
Queue<String> queue = new PriorityQueue<>()

// Add to your queue. Offer for single element, addAll with a list for Multiple Elements
queue.offer("Bat")
queue.addAll(List.of("Zebra","Cat","Monkey"))

// Use poll to pull from the queue and return which element comes next, the natural sort order is imposed on this
queue.poll()
queue.poll()
queue.poll()
queue.poll()



```

# Tips for Collections

-   **Hash** indicates an unsorted & unorderd
-   **Linked** indicates that it's ordered as it is entered
-   **Tree** indicate sorted order, also has Navigable{Set,Tree} implemented as well
