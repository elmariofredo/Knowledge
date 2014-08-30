# Tree Structure

##❯ Parent References

  Tree structure pattern where each record has parent reference like this:

```
db.categories.insert( { _id: "MongoDB", parent: "Databases" } )
db.categories.insert( { _id: "dbm", parent: "Databases" } )
db.categories.insert( { _id: "Databases", parent: "Programming" } )
```

  The Parent Links pattern provides a simple solution to tree storage but requires multiple queries to retrieve subtrees.

  References:
    http://docs.mongodb.org/manual/tutorial/model-tree-structures-with-parent-references/

##❯ Child References

  Tree structure pattern where each record store array of node child id's like this:

```
db.categories.insert( { _id: "MongoDB", children: [] } )
db.categories.insert( { _id: "dbm", children: [] } )
db.categories.insert( { _id: "Databases", children: [ "MongoDB", "dbm" ] } )
```

  The Child References pattern provides a suitable solution to tree storage as long as no operations on subtrees are necessary. This pattern may also provide a suitable solution for storing graphs where a node may have multiple parents.

  References:
    http://docs.mongodb.org/manual/tutorial/model-tree-structures-with-child-references/

##❯ Array of Ancestors

  Tree structure pattern where we store array of ancestors along with parent node like this:

```
db.categories.insert( { _id: "MongoDB", ancestors: [ "Books", "Programming", "Databases" ], parent: "Databases" } )
db.categories.insert( { _id: "dbm", ancestors: [ "Books", "Programming", "Databases" ], parent: "Databases" } )
db.categories.insert( { _id: "Databases", ancestors: [ "Books", "Programming" ], parent: "Programming" } )
```

  The Array of Ancestors pattern is slightly slower than the Materialized Paths pattern but is more straightforward to use.

  References:
    http://docs.mongodb.org/manual/tutorial/model-tree-structures-with-ancestors-array/

##❯ Materialized Paths

  Tree structure pattern where as in **Array of Ancestors** are stored ancestor but as comma delimited string without parent node like this

```
db.categories.insert( { _id: "Books", path: null } )
db.categories.insert( { _id: "Programming", path: ",Books," } )
db.categories.insert( { _id: "Databases", path: ",Books,Programming," } )
```

  References:
    http://docs.mongodb.org/manual/tutorial/model-tree-structures-with-materialized-paths/

##❯ Nested Sets

  The Nested Sets pattern identifies each node in the tree as stops in a round-trip traversal of the tree. The application visits each node in the tree twice; first during the initial trip, and second during the return trip. The Nested Sets pattern stores each tree node in a document; in addition to the tree node, document stores the id of node’s parent, the node’s initial stop in the left field, and its return stop in the right field.

```
db.categories.insert( { _id: "Books", parent: 0, left: 1, right: 12 } )
db.categories.insert( { _id: "Programming", parent: "Books", left: 2, right: 11 } )
db.categories.insert( { _id: "Languages", parent: "Programming", left: 3, right: 4 } )
```

  The Nested Sets pattern provides a fast and efficient solution for finding subtrees but is inefficient for modifying the tree structure. As such, this pattern is best for static trees that do not change.

  Reference:
    http://docs.mongodb.org/manual/tutorial/model-tree-structures-with-nested-sets/
