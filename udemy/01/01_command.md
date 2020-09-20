## Command Line Summary

- Mongo DB CLI 에서 자바스크립트 명령어를 활용해서

- `db.products.find().pretty()`: 데이터베이스에 저장되어있는 모든 데이터를 가독성 높게 가공해 조회한다.

- `db.products.insertOne({title:"T-shirt", seller:{name:"max", age:29}})` : 데이터 삽입하기

- `db.products.deleteMany({})` : 데이터베이스 내용물 전부 삭제하기

- `db.stats()` : 사용하고 있는 데이터 베이스 이름, 그리고 데이터베이스에 저장된 데이터와 관련한 다양한 정보를 띄워줍니다.

### One to Many Relationship

- MongoDB에서 1:N / N:M 관계 설정하는데 있어서 빠질 수 없는 내용은 Reference라는 내용이다.

- Reference는 하나의 Document에 저장되는 데이터를 기능이나 분류에 맞게 분리(split)해서 사용하는 것인데, MongoDB에서 Depth 등을 깊게 파고 들어갈 필요가 없고, 코드의 가독성을 높이기 때문에 종종 사용된다.

- 아래의 N:M 관계에서도 동일하다.

### Many to Many Relationship
