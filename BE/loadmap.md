# Backend LoadMap✨

## 1. Programming Language
* Javascript - Node.js
* Java - Spring
* Go
* Python - Django

## 2. Network

HTTP(HyperText Transfer Protocol): HTML 문서와 같은 리소스들을 가져올 수 있도록 해주는 프로토콜

TCP/IP: 패킷 통신 방식의 인터넷 프로토콜인 IP와 전송 조절 프로토콜인 TCP로 이루어져 있다. IP는 패킷 전달 여부를 보증하지 않고, 패킷을 보낸 순서와 받는 순서가 다를 수 있다. TCP는 IP 위에서 동작하는 프로토콜로, 데이터의 전달을 보증하고 보낸 순서대로 받게 해준다. HTTP, FTP, SMTP 등 TCP를 기반으로 한 많은 수의 애플리케이션 프로토콜들이 IP 위에서 동작하기 때문에, 묶어서 TCP/IP로 부르기도 한다.

DNS(Domain Name System): 사람이 읽을 수 있는 도메인 이름(www.github.com)을 머신이 읽을 수 있는 IP 주소로 변환하는 시스템

Socket: 네트워크상에서 동작하는 프로그램 간 통신의 종착점. 프로그램이 네트워크에서 데이터를 통신할 수 있도록 연결해주는 연결부

## 3. [RESTful API](https://github.com/rkdls8268/TIL/blob/main/BE/nodeJs.md)

## 4. Database
RDB: 키와 값들의 간단한 관계를 테이블화시킨 매우 간단한 원칙의 전산정보 데이터베이스
- key: 테이블의 각 로우에는 저만의 고유 키가 있다. 한 테이블 안의 로우는 다른 테이블의 로우로 연결이 가능한데, 이는 연결된 로우의 고유 키를 위한 컬럼을 추가함으로써 이루어진다.
- index: 속도 향상을 목적으로 데이터 검색을 위해 사용. b-tree 구조
- SQL(Structured Query Language): 관계형 데이터베이스 관리 시스템(RDBMS)의 데이터를 관리하기 위해 설계된 특수 목적의 프로그래밍 언어
- transaction: 데이터베이스의 상태를 변화시키기 위해서 수행하는 작업의 단위

NoSQL: Not Only SQL의 약자로 기존 RDB 형태의 관계형 데이터베이스가 아닌 다른 형태의 데이터 저장 기술을 의미. RDB보다 덜 제한적인 일관성 모델을 이용하는 데이터의 저장 및 검색을 위한 매커니즘을 제공.

Scaling, Sharding...

## 5. Cashing
Redis, memcached

## 6. Authentication

## 7. Distributed System
cap theorm
BASE 원칙