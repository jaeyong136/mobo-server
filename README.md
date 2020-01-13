# PLOT
>
> S.O.P.T 25기 서버 파트 앱잼 프로젝트
>
> <img width="300" alt="KakaoTalk_20191228_220853327" src="https://user-images.githubusercontent.com/56102421/71595790-6647a100-2b80-11ea-87e4-0fec041cfd7a.png">


![node_badge](https://img.shields.io/badge/node-%3E%3D%208.0.0-green)
![npm_bedge](https://img.shields.io/badge/npm-v6.10.1-blue)

* 프로젝트 기간: 2019.12.22 ~ 2019.01.04
* [API 문서](https://github.com/TeamMoBo/mobo-server/wiki)




## 프로젝트 설명

'**Plot**'입니다.

> 영화 친구 찾기로 가장한 소개팅 어플

## Workflow


![workflow](https://user-images.githubusercontent.com/30704569/71724029-24fe0c80-2e72-11ea-9b61-a2b0ca8edd85.png)

## 핵심 기능

### 매칭 알고리즘

> 최다 매칭을 위하여 이분 매칭 알고리즘을 이용하였습니다
> <br></br>이분 매칭 알고리즘에 이용하기 위해 DFS를 이용하는 과정에서 랜덤 순서 & 필터링을 적용하여 최다 매칭이 여러 케이스 일 경우 다양한 경우의 수가 도출 됩니다
> <br></br>간선을 연결 할 때는 완전 탐색을 이용하였습니다.
> <br></br>필터링은 병렬로 계산하기 때문에 매칭은 O(E * V) / 간선 연결에 인원 수 만큼 걸리기 때문에 O(n^2)
> <br></br>따라서 탐색 시간은 O (E * V * n^2) 가 나옵니다.
>
> ![algorithm](https://user-images.githubusercontent.com/30704569/71710762-2d8a1f00-2e41-11ea-8e54-50763ce263ea.png)

### 채팅 서비스

> 클라이언트와의 원활한 소통을 위해 Firebase RealTime Database를 이용한 채팅 서비스를 합니다<br><br/>
> 사용할 쓰는 user의 아이디와 번호를 encryption을 통해 고유한 아이디를 전달합니다<br><br/>
> 채팅방에 쓰이는 고유 번호는 timestamp + 각 유저의 해싱값을 통해 본인만 접근이 가능하도록 암호화 하였습니다.

### 크롤링

> 영화 정보를 KOBIS에서 제공하는 실시간 api와 영화 정보를 제공하는 api와 cheerio를 이용해 크롤링합니다. <br><br/>
> 해당 크롤링 코드는 의존성을 줄이기 위해 Google Cloud Function을 이용하여 Google Cron 서비스로 매일 23시에 DB를 업데이트 합니다.<br><br/>
> 해당 서버 리스 언어는 node 언어로 작성하였습니다.

## Architecture

![architecture](https://user-images.githubusercontent.com/30704569/71710051-ad15ef00-2e3d-11ea-9a95-414fe8cee449.png)


## DB ERD

![DB ERD](https://user-images.githubusercontent.com/56102421/71641982-7928b580-2ce7-11ea-8dc0-fc6213f397bf.png)



## Depenedncy Module
사용 패키지(모듈)은 다음과 같습니다.

```json
"dependencies": {
    "aws-sdk": "^2.596.0",
    "cookie-parser": "~1.4.4",
    "crypto": "^1.0.1",
    "debug": "~2.6.9",
    "express": "^4.16.4",
    "express-generator": "^4.16.1",
    "firebase-admin": "^8.9.0",
    "http-errors": "~1.6.3",
    "jade": "^1.11.0",
    "jsonwebtoken": "^8.5.1",
    "moment": "^2.24.0",
    "morgan": "~1.9.1",
    "multer": "^1.4.2",
    "multer-s3": "^2.9.0",
    "promise-mysql": "^4.1.1",
    "pug": "^2.0.4"
  }
```





## 시작하기

소스 코드는 Windows10 64bit + Visiau Studio Code + Node v10.16.0 + NPM v6.13.4 + Express 4.16.1 환경에서 제작되었습니다.

* Node.js의 Async/Await 도구를 사용해 (Promise) 비동기 제어를 하고 있습니다.



#### 설치하기

* `nodejs`와 `npm`을 을치합니다. (설치 방법 :  [nodejs.org](https://nodejs.org/) 를 참고)
* Node.js 10 LTS 버전을 설치합니다.
* 실행에 필요한 의존성을 설치합니다.

```
npm install
```



#### 실행하기

```
npm start
```

> 13.125.48.35:7935 으로 접속 가능합니다.



## 배포

* [AWS EC2](https://aws.amazon.com/ko/ec2/?sc_channel=PS&sc_campaign=acquisition_KR&sc_publisher=google&sc_medium=english_ec2_b&sc_content=ec2_e&sc_detail=awsec2&sc_category=ec2&sc_segment=177228231544&sc_matchtype=e&sc_country=KR&s_kwcid=AL!4422!3!177228231544!e!!g!!awsec2&ef_id=WkRozwAAAnO-lPWy:20180412120123:s) - 클라우드 환경 컴퓨팅 시스템
* [AWS RDS](https://aws.amazon.com/ko/rds/) - 클라우드 환경 데이터베이스 관리 시스템
* [AWS S3](https://aws.amazon.com/ko/s3/?sc_channel=PS&sc_campaign=acquisition_KR&sc_publisher=google&sc_medium=english_s3_b&sc_content=s3_e&sc_detail=awss3&sc_category=s3&sc_segment=177211245240&sc_matchtype=e&sc_country=KR&s_kwcid=AL!4422!3!177211245240!e!!g!!awss3&ef_id=WkRozwAAAnO-lPWy:20180412120059:s) - 클라우드 환경 데이터 저장소


## 사용된 도구 

* [Node.js](https://nodejs.org/ko/) - Chrome V8 자바스크립트 엔진으로 빌드된 자바스크립트 런타임
* [Express.js](http://expressjs.com/ko/) - Node.js 웹 애플리케이션 프레임워크
* [NPM](https://rometools.github.io/rome/) - 자바 스크립트 패키지 관리자
* [PM2](http://pm2.keymetrics.io/) - Express 앱용 프로세스 관리자
* [vscode](https://code.visualstudio.com/) - 편집기
* [Mysql](https://www.mysql.com/) - DataBase



## 개발자

* [이상윤](https://github.com/syndersonLEE) - 채팅 + 매칭 관련 서비스 전반
* [양희연](https://github.com/hhiyeon) - 메인 + 영화 선택 + 크롤링
* [이다현](https://github.com/leeda66) - 개인 정보 관리 + 결제 페이지
* [이재용](https://github.com/jaeyong136) - 로그인 / 회원가입 및 데이터 수집


[기여자 목록](https://github.com/TeamMoBo/mobo-server/graphs/contributors)을 확인하여 이 프로젝트에 참가하신 분들을 보실 수 있습니다.


## PLOT의 연관 프로젝트

* [Android](https://github.com/TeamMoBo/mobo-android)
* [iOS](https://github.com/TeamMoBo/MoboiOS)
