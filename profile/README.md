## 🚀 [2025] 레거시 시스템의 MSA 전환 및 클라우드 마이그레이션
React, 모로리식 방식의 Spring Boot, Django 시스템에 Spring Cloud를 적용하고 Jenkins Pipeline을 적용하여 탄력성과 운영 용이성을 고려한 아키텍처로의 전환을 진행한 프로젝트입니다.
<br />
<br />

🔗[원본 프로젝트](https://github.com/lgcns-mini-project1-group5/cryptory)
에서 전환 이전의 프로젝트를 확인할 수 있습니다.

## 아키텍처 비교
### 🏗️ AS-IS
![변환 후 아키텍처](https://github.com/user-attachments/assets/64e65576-9540-444a-a1ee-01bec1f10cd7)

### 🏢 TO-BE
![변환 후 아키텍처](https://github.com/user-attachments/assets/3d21f106-e925-4a62-b9fe-6a389fd37dd8)

## 🔄️전환 방법
### 📌 레거시 프로젝트 분석


<img src="https://github.com/user-attachments/assets/ed6d6940-1069-498f-9e02-aa15acc223e3"  width="600" height="400"/> | <img src="https://github.com/user-attachments/assets/014b33ba-d254-4edf-986e-c0fea8c47041"  width="600" height="400"/>
---|---|

1️⃣ 데이터 ERD 및 기능 명세서를 바탕으로 기존 프로그램 분석 <br>
2️⃣ 마이크로서비스 전환 대상 서비스 식별 및 분리 &rarr; ( User 서비스, Coin 서비스 ) <br>


---
### 🛠️ Jenkins 기반의 CI/CD 적용

<img src="https://github.com/user-attachments/assets/0e1bd1bb-0ff5-477c-b76d-a031947f97e0"  width="800" height="300"/>

🔐 보안 관리
* 민감 정보: Jenkins Credentials 사용
* 환경 변수: Environment Variables로 관리

📦 CI/CD 과정 <br>
1️⃣ 소스코드 checkout <br>
2️⃣ Dockerfile 기반 이미지 생성 <br>
3️⃣ Amazon ECR로 이미지 업로드 <br>
4️⃣ 배포 단계 <br>
* EC2 배포: `(by sshPublisher)`
* ECS 배포
  *  🗒️ Task Definition 정의
  *  🚀 ECS 배포 실행<br>

5️⃣ 최종 파이프라인을 Github으로 버전관리 <br>
6️⃣ Github webhook을 설정 <br>

---

### ☁️ 클라우드 아키텍처 구성
💻 EC2

* 🛠️ Jenkins (CI/CD 자동화)

💻 EC2 (Spring Cloud 인프라)

* 🔍 Eureka (서비스 디스커버리)

* ⚙️ Config Server (설정 중앙 관리)

* 🚪 Gateway Server (API Gateway 및 로드 밸런싱)

* 📩 RabbitMQ (비동기 메시지 큐)

📦 ECS (Docker 기반 서비스 배포)

* 🏦 Coin-Service (Spring Boot)

* 👤 User-Service (Spring Boot)

* 🐍 Django (백엔드 서비스)

📂 ECR (Docker 컨테이너 이미지 저장소)

🖥️ React 배포

* 🗂️ S3 (정적 웹 호스팅)

* ⚡ CloudFront (CDN 기반 속도 최적화 및 캐싱)

---

### 🌿 Spring Cloud 적용용 
🚀 Spring Cloud Eureka <br>
* 서비스 등록, 등록된 서비스의 조회
* 분산 투명성 제공

🚪 Spring Cloud Gateway <br>
* 단일 진입지점, 로드 밸런싱 제공
* 분산 투명성 제공

📜 Spring Cloud Config <br>
* Git private Repository에서 설정파일 관리
* Git webhook과 연동한 Cloud Bus refresh

## 👩‍💻 팀원
<table>
  <tr>
    <!-- 첫 번째 팀원 -->
    <td align="center" width="25%">
        <img src="https://avatars.githubusercontent.com/gwangbu-desu" alt="Avatar" width="100px"/><br/>
        <a href="https://github.com/gwangbu-desu">김우영</a><br/>
        <img src="https://github-readme-stats.vercel.app/api?username=gwangbu-desu&show_icons=true&theme=transparent" alt="김우영's GitHub stats" width="200px"/>
    </td>
    <!-- 두 번째 팀원 -->
    <td align="center" width="25%">
        <img src="https://avatars.githubusercontent.com/0ssang" alt="Avatar" width="100px"/><br/>
        <a href="https://github.com/0ssang">조영상</a><br/>
        <img src="https://github-readme-stats.vercel.app/api?username=0ssang&show_icons=true&theme=transparent" alt="조영상's GitHub stats" width="200px"/>
    </td>
    <!-- 세 번째 팀원 -->
    <td align="center" width="25%">
        <img src="https://avatars.githubusercontent.com/judymoody59" alt="Avatar" width="100px"/><br/>
        <a href="https://github.com/judymoody59">채민주</a><br/>
        <img src="https://github-readme-stats.vercel.app/api?username=judymoody59&show_icons=true&theme=transparent" alt="채민주's GitHub stats" width="200px"/>
    </td>
    <!-- 네 번째 팀원 -->
    <td align="center" width="25%">
        <img src="https://avatars.githubusercontent.com/HoGyeongC" alt="Avatar" width="100px"/><br/>
        <a href="https://github.com/HoGyeongC">최호경</a><br/>
        <img src="https://github-readme-stats.vercel.app/api?username=HoGyeongC&show_icons=true&theme=transparent" alt="최호경's GitHub stats" width="200px"/>
    </td>
  </tr>
</table>

<br />
<br />

## 🛠️ 기술 스택

- 프로그래밍 언어

<img src="https://img.shields.io/badge/java-007396?style=for-the-badge&logo=OpenJDK&logoColor=white"> <img src="https://img.shields.io/badge/springboot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white"> <img src="https://img.shields.io/badge/django-092E20?style=for-the-badge&logo=django&logoColor=white"> <img src="https://img.shields.io/badge/python-3776AB?style=for-the-badge&logo=python&logoColor=white"> <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=JavaScript&logoColor=white"> <img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=React&logoColor=white">

- 데이터베이스

<img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=MySQL&logoColor=white">

- 컨테이너

<img src="https://img.shields.io/badge/amazonecs-FF9900?style=for-the-badge&logo=amazonecs&logoColor=white"> <img src="https://img.shields.io/badge/docker-2496ED?style=for-the-badge&logo=docker&logoColor=white">

- 이미지 레지스트리

<img src="https://img.shields.io/badge/amazonecr-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white">

- CI/CD

<img src="https://img.shields.io/badge/jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white"> <img src="https://img.shields.io/badge/amazons3-569A31?style=for-the-badge&logo=amazons3&logoColor=white"> <img src="https://img.shields.io/badge/CloudFront-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white">

<br />
<br />
