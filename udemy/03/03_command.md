## Command Line Summary

전반적으로 정리할 내용들은 MongoDB Official Document에 모두 정리되어 있다.



### Query Selector

- CSS에서 등장했던 것처럼, MongoDB에도 Query Selector라는 개념이 있다.
- Comparison, Evaluation, Logical, Array, Element, Comments, Geospatial 라는 개념들이 존재한다.
- SQL에서도 쿼리를 다양하게 가공하려고 했던 시도가 있던 것처럼, MongoDB도 분명히 그럴 것이란 생각이 든다.



### Projection Operator

- $, $elemMatch, $meta, $slice : 음, 정확히 Projection Operator가 뭐지? 우선 단어 개념 찾기 전에 강사가 어떻게 사용하는지 보고 찾아보자

| Name      | Description                                                  |
| --------- | ------------------------------------------------------------ |
| $         | Projects the first element in an array that matches the query condition. |
| $eleMatch | Projects the first element in an array that matches the specified [`$elemMatch`](https://docs.mongodb.com/manual/reference/operator/projection/elemMatch/#proj._S_elemMatch) condition. |
| $meta     | Projects the available per-document metadata.                |
| $slice    | Limits the number of elements projected from an array. Supports skip and limit slices. |



### Comparison Operator

- SQL에도 있듯 당연하게 비교 연산자가 MongoDB에도 있다.
- 자료형에 맞게 값을 찾게 도와주는 쿼리 (in, nin 등)도 있다.

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [`$eq`](https://docs.mongodb.com/manual/reference/operator/query/eq/#op._S_eq) Equal | Matches values that are equal to a specified value.          |
| [`$gt`](https://docs.mongodb.com/manual/reference/operator/query/gt/#op._S_gt) Greater Than | Matches values that are greater than a specified value.      |
| [`$gte`](https://docs.mongodb.com/manual/reference/operator/query/gte/#op._S_gte) Greater Than Equal | Matches values that are greater than or equal to a specified value. |
| [`$in`](https://docs.mongodb.com/manual/reference/operator/query/in/#op._S_in) In Array | Matches any of the values specified in an array.             |
| [`$lt`](https://docs.mongodb.com/manual/reference/operator/query/lt/#op._S_lt) Less Than | Matches values that are less than a specified value.         |
| [`$lte`](https://docs.mongodb.com/manual/reference/operator/query/lte/#op._S_lte) Less Than Equal | Matches values that are less than or equal to a specified value. |
| [`$ne`](https://docs.mongodb.com/manual/reference/operator/query/ne/#op._S_ne) Not Equal | Matches all values that are not equal to a specified value.  |
| [`$nin`](https://docs.mongodb.com/manual/reference/operator/query/nin/#op._S_nin) Not In Array | Matches none of the values specified in an array.            |





### Logical Query Operators

- 프로그래밍 언어에서 조건문 마냥 활용할 수 있게 논리 연산자를 제공한다.

- 조건문으로 2개 이상의 쿼리를 조합할 때, [ ] 배열을 활용해서 2개의 쿼리 값을 넣고 논리 연산을 진행한다.

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [`$and`](https://docs.mongodb.com/manual/reference/operator/query/and/#op._S_and) | Joins query clauses with a logical `AND` returns all documents that match the conditions of both clauses. |
| [`$not`](https://docs.mongodb.com/manual/reference/operator/query/not/#op._S_not) | Inverts the effect of a query expression and returns documents that do *not* match the query expression. |
| [`$nor`](https://docs.mongodb.com/manual/reference/operator/query/nor/#op._S_nor) | Joins query clauses with a logical `NOR` returns all documents that fail to match both clauses. |
| [`$or`](https://docs.mongodb.com/manual/reference/operator/query/or/#op._S_or) | Joins query clauses with a logical `OR` returns all documents that match the conditions of either clause. |





### Element Operator

- Element Operator는 사용할 수 있는 것이 정확하게 2개다.

| Name                                                         | Description                                            |
| ------------------------------------------------------------ | ------------------------------------------------------ |
| [`$exists`](https://docs.mongodb.com/manual/reference/operator/query/exists/#op._S_exists) | Matches documents that have the specified field.       |
| [`$type`](https://docs.mongodb.com/manual/reference/operator/query/type/#op._S_type) | Selects documents if a field is of the specified type. |





### Evaluation Query Operator

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [`$expr`](https://docs.mongodb.com/manual/reference/operator/query/expr/#op._S_expr) | Allows use of aggregation expressions within the query language. |
| [`$jsonSchema`](https://docs.mongodb.com/manual/reference/operator/query/jsonSchema/#op._S_jsonSchema) | Validate documents against the given JSON Schema.            |
| [`$mod`](https://docs.mongodb.com/manual/reference/operator/query/mod/#op._S_mod) | Performs a modulo operation on the value of a field and selects documents with a specified result. |
| [`$regex`](https://docs.mongodb.com/manual/reference/operator/query/regex/#op._S_regex) | Selects documents where values match a specified regular expression. |
| [`$text`](https://docs.mongodb.com/manual/reference/operator/query/text/#op._S_text) | Performs text search.                                        |
| [`$where`](https://docs.mongodb.com/manual/reference/operator/query/where/#op._S_where) | Matches documents that satisfy a JavaScript expression.      |



### Array Query Operator

- Mongo DB에서 한 개의 Document에서 여러개의 값을 조회할 땐, [ ]을 사용해서 조회하는 형태를 취한다.

| Name                                                         | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [`$all`](https://docs.mongodb.com/manual/reference/operator/query/all/#op._S_all) | Matches arrays that contain all elements specified in the query. |
| [`$elemMatch`](https://docs.mongodb.com/manual/reference/operator/query/elemMatch/#op._S_elemMatch) | Selects documents if element in the array field matches all the specified [`$elemMatch`](https://docs.mongodb.com/manual/reference/operator/query/elemMatch/#op._S_elemMatch) conditions. |
| [`$size`](https://docs.mongodb.com/manual/reference/operator/query/size/#op._S_size) | Selects documents if the array field is a specified size.    |





db.extened.find({genre:{$size:2}}).pretty()



db.extened.find({"meta.aired":2018}).pretty()



db.extened.find({ratings:{$elemMatch:{$gt:8, $lt:10}}}).pretty()