# <center>GraphQL</center>

## GraphQL(GQL)
페이스북에서 만든 **쿼리 언어**. GraphQL은 요즘 개발자들 사이에서 자주 입에 오르내리고 있음. 하지만 국내에서 GraphQL API를 Open API로 공개한 곳은 드물다.

GQL은 SQL과 마찬가지로 쿼리 언어이지만 둘의 언어적 구조 차이는 매우 크다. 실전에서 쓰이는 방식의 차이도 매우 크다. 이 둘의 언어적 구조의 차이가 활용 측명에서의 차이를 가져왔다.

SQL은 데이터베이스 시스템에 저장된 데이터를 효율적으로 가져오는 것이 목적이고, GQL은 웹 클라이언트가 데이터를 서버로부터 효율적으로 가져오는 것이 목적이다. SQL의 문장은 주로 백엔드 시스템에서 작성하고 호출하는 반면, GQL의 문장은 주로 클라이언트 시스템에서 작성하고 호출한다. 

서버사이드 GQL 애플리케이션은 GQL로 작성된 쿼리를 입력으로 받아 쿼리를 처리한 결과를 다시 클라이언트로 돌려준다. HTTP API 자체가 특정 DB나 플랫폼에 종속적이지 않은 것과 마찬가지로 GQL 역시 어떠한 특정 DB나 플랫폼에 종속적이지 않다. 심지어 네트워크 방식에도 종속적이지 않음!

## REST API와의 비교
REST API는 URL, METHOD 등을 조합하기 때문에 다양한 endpoint가 존재한다. 반면, GQL은 단 하나의 endpoint가 존재한다. 또한, GQL API에서는 불러오는 데이터의 종류를 쿼리 조합을 통해서 결정한다. 예를 들면, REST API에서는 각 endpoint마다 데이터베이스 SQL 쿼리가 달라지는 반면, GQL API는 GQL 스키마의 타입마다 데이터베이스 SQL 쿼리가 달라진다. 

[📌REST API 참고](https://github.com/rkdls8268/TIL/blob/main/BE/nodeJs.md)

_✨GQL API를 사용하면 여러번의 네트워크 호출을 할 필요 없이, **한 번의 네트워크 호출**로 처리할 수 있다.✨_

# Javascript Trend
[📌2016-2019 자바스크립트 트렌드 확인](https://2019.stateofjs.com/overview/)

|field|1위|2위|
|-----|---|---|
|JS flavors|Typescript(압도적)||
|Front End|React|Vue.js|
|Data Layer|Redux|GraphQL✨|
|Back End|Express(압도적)|Next.js|
|Testing|Jest|Mocha|
|Mobile & Desktop|Electron|React Native|
+) Flutter 도 모바일 쪽이라면 눈여겨볼 것👀