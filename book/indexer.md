# The comparison table of the indexer design

## The SQL
1. The SQL mainly uses the Indexed Sequential Access Method [ISAM][1]
2. The SQL is searched and sorting by ***B+ Tree***.
3. The SQL stores the data in the ***nodes of the B+ Tree****.
4. The SQL uses the ***B+ Tree*** for range searching.
5. The SQL uses the ***B+ Tree*** for sorting, such as the sorting by time method.

## The QQL
1. The QQL mainly uses the [Hash][2] method.
2. The QQL is searched by key firstly, then using a **B Tree** searching method. (***B Tree*** is not the **B+ Tree**)
3. The QQL doesn't support the range searching directly. 
4. The QQL uses the ***B Tree*** for sorting, such as the sorting by time method.

## Feature
### Searching

The running time of the hash method is O (N) while the running time of the tree method is O (log (N)). 
So the hash method is faster than the tree method.

### Sorting
The SQL is not sorted by the ***B+ TREE*** directly while the QQL is sorted by the **B TREE** firstly then sorted in the memory.

The QQL will cost more memory than the SQL, but the price of memory is cheap.

The QQL uses a full recording traversal method while the SQL uses a tree traversal method.

## Filtering

All the SQL and QQL are filtered by full records filtering.

## Filesystem

Most of the SQL database server uses the ISAM or transaction engine, such as the MyISAM and InnoDB on the MySQL database server.

The SQLite uses a virtual file system for crossing platform.

However, the QQL corpus server uses the blocked filesystem directly for high performance.


[1]: https://en.wikipedia.org/wiki/ISAM "ISM"
[2]: https://en.wikipedia.org/wiki/Hash_table "Hash"
