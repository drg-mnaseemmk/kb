# Cypher
Cypher is Neo4j's query language. It has some similarities to SQL, but getting comfortable with it requires some effort on your part. You can start off with the [Get started with Cypher](https://neo4j.com/docs/developer-manual/current/get-started/cypher/) page on the Neo4j documentation. Some basic ideas, relevant to healthbase, are covered in this article.

## Basic example
How do we find all practitioners who work at a specific hospital?

```
MATCH p=(n:hospital {healthbase_id: 'H:100151'})<-[r:WORKS_AT]-(m) RETURN p;
```

Let's break this down. The MATCH part of the query specifies what it is that we are looking for. This is a pattern, usually specified like this:  
```
(node1)<-[r]-(node2)
```
This indicates that we want a relationship `r` between `node1` and `node2`. Note that the direction of the arrow matters; it must match the direction of the relationship we want.

We can modify this pattern with filters. Nodes have labels (such as `hospital` or `healthsystem`) as well as properties (such as `healthbase_id` or `name`). Relationships too have labels (such as `WORKS_AT`) and attributes to them(such as `score1`). In this case we are looking for a node of type hospital with healthbase_id 'H:100151' which has a WORKS_AT relationship directed towards it. We haven't set a filter on `m` in this case.

##   Filter by score
Modifying the above query, let's restrict it to give us only strongly affiliated physicians.
```
MATCH p=(n:hospital {healthbase_id: 'H:100151'})<-[r]-(m:physician) WHERE r.score1 > 90 RETURN p LIMIT 300;
```
The `WHERE` clause allows us to specify that we need only relationships that have a score1 greater than 90. We also set a `LIMIT` on the number of relationships to return.


## Check if a relationship property is present
You can further restrict the query to show you only relationships that fall into a certain therapeutic area by making sure they have the diagnosis code you want. You can use the `exists` function to do this.
```
MATCH p=(n:hospital {healthbase_id: 'H:100151'})<-[r]-(m:physician) WHERE r.score1 > 90 and exists(r.dx_R13) RETURN p LIMIT 10;
```

## Path to any depth
In all of the above examples, we were only looking for direct connections. Neo4j also allows us to run queries that span across relationships. Take this for instance -
```
MATCH p=(n:healthsystem {healthbase_id: 'HS:E416011702'})<-[:OWNED_BY*..]-(m) RETURN p LIMIT 300;
```
In this case, we are trying to get all `OWNED_BY` relationships to healthsystem ID 'HS:E416011702', no matter what depth. This will give you many results, so we set a LIMIT on it to be safe.

## Limits on depth
We can set limits on the depth too. This is recommended so as to not crash the server by looking for nodes that are too far away in the graph. You do this by specifying an asterix and two dots, like so `[*..4]`.
```
MATCH p=(n:healthsystem {healthbase_id: 'HS:E416011702'})<-[*..4]-(m) WHERE m:hospital OR m:healthsystem RETURN p LIMIT 300;
```

## Shortest path
Given two entities, how do you find the most direct relationship between them? You can do this by using the `shortestPath` function.
```
MATCH path=shortestPath((cs:healthsystem { healthbase_id: 'HS:E222529464' })-[*..10]-(ms:asc { healthbase_id: 'ASC:07C0001051' }))
RETURN path;
```
Neo4j comes with many such builtin [functions](https://neo4j.com/docs/developer-manual/current/cypher/functions/).
