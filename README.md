# 🌐 Node.js 백엔드 학습 프로젝트

이 레포지토리는 Node.js를 활용한 백엔드 개발 학습 내용을 정리한 것입니다. 서버 개발의 기초부터 데이터베이스 연동, API 개발, 미들웨어 관리 등 다양한 핵심 기술을 다룹니다. 비동기 처리, RESTful API 설계 등 백엔드 개발에 필수적인 개념을 배웠습니다.

## 📘 주요 학습 내용

### 1. ⚙️ Node.js 기본 설정 및 환경 구축
- Node.js 설치 및 프로젝트 초기 설정 방법을 학습했습니다.
- `npm init`을 통해 패키지 관리자를 설정하고, 필요한 모듈을 설치하여 백엔드 프로젝트의 기본 구성을 완료했습니다.

### 2. 🧩 모듈 시스템
- `require`와 `module.exports`를 통해 **모듈화**를 구현하고, 코드 재사용성을 높이는 방법을 학습했습니다.
- CommonJS 및 ES6 모듈 시스템의 차이점을 이해하고 프로젝트에 맞게 선택했습니다.
```javascript
// math.js
const add = (a, b) => a + b;
module.exports = { add };
```
### 3. 🌐 서버 구축 (HTTP)
- Node.js에서 **내장 HTTP 모듈**을 사용하여 간단한 웹 서버를 구축했습니다.
- 요청(Request)과 응답(Response)의 흐름을 이해하고, 다양한 HTTP 메서드(GET, POST, PUT, DELETE)를 처리했습니다.
```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});

server.listen(3000, () => {
  console.log('Server running at http://localhost:3000/');
});
```
### 4. 📡 Express.js 프레임워크
- **Express.js**를 활용하여 더욱 효율적인 서버 개발을 구현했습니다.
- 라우팅, 미들웨어 관리, 정적 파일 제공 등을 통해 서버 개발의 유연성을 높였습니다.
```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello World!');
});

app.listen(3000, () => {
  console.log('Server running at http://localhost:3000/');
});
```
### 5. 📊 RESTful API 설계
- **RESTful API**를 설계하여 클라이언트와 서버 간의 데이터 통신을 구현했습니다.
- HTTP 메서드와 상태 코드를 기반으로 직관적이고 표준화된 API를 설계했습니다.
```javascript
app.get('/api/users', (req, res) => {
  res.json([{ name: 'Alice' }, { name: 'Bob' }]);
});
```
### 6. 🛠️ 미들웨어 (Middleware)
- **미들웨어**를 사용하여 요청 처리 과정을 중간에 제어하고, 로깅, 인증, 에러 처리 등을 구현했습니다.
- `app.use()`를 통해 전역 및 개별 라우트에 미들웨어를 적용하는 방법을 학습했습니다.
```javascript
app.use((req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();
});
```
### 7. 💾 데이터베이스 연동 (MySQL)
- **MySQL**을 Node.js 서버와 연동하여 데이터를 저장하고 관리하는 방법을 배웠습니다.
- **Sequelize** ORM을 사용하여 데이터베이스와의 상호작용을 더욱 효율적으로 처리했습니다.
```javascript
const mysql = require('mysql');
const connection = mysql.createConnection({
  host: 'localhost',
  user: 'root',
  password: 'password',
  database: 'test'
});

connection.connect();
```
### 8. 🔄 비동기 처리
- **콜백 함수**와 **Promise**, **async/await**를 활용하여 비동기 처리의 핵심 개념을 학습했습니다.
- 서버 요청 처리 중 발생할 수 있는 **비동기 이슈**를 해결하는 방법을 이해했습니다.
```javascript
const fetchData = async () => {
  const data = await getDataFromAPI();
  console.log(data);
};
```
### 9. 🔒 보안 및 인증
- **JWT (JSON Web Token)**를 이용한 사용자 인증 및 권한 관리 방법을 학습했습니다.
- **AWS S3**를 활용하여 파일 업로드 및 관리를 구현하고, 소셜 로그인을 통해 사용자 인증 과정을 개선했습니다.
```javascript
const jwt = require('jsonwebtoken');

app.post('/login', (req, res) => {
  const token = jwt.sign({ userId: 1 }, 'secret');
  res.json({ token });
});
```
