### 강의 목표
- CI/CD 파이프라인의 기본 개념에 대해서 이해한다.
- 기본적인 운영환경(DEV,QA,PROD) 이 어떻게 구성되고 운영되는지 이해한다.
- Jenkins의 기본 개념에 대해 이해한다.
- 실제 운영에서 특히 AWS 기반의 클라우드 환경에서 Jenkins 가 어떻게 활용되는지 알 수 있다.

### 목차
1. CI/CD 란 무엇인가?
2. Jenkins 의 기본 개념과 동작 방식
3. 개발 환경 및 CI/CD 의 기본 동작 이해
4. Jenkins 및 플러그인 설치 실습
5. CI/CD 파이프라인 구축 및 Q&A
6. 실제 운영 환경에서 Jenkins 사용 사례 알아보기(DW ETL Pipeline)   


### 1. CI/CD 란?
- CI(Continuous I ntegration)   
여러 개발자들의 코드베이스(코드 스타일)를 계속해서 통합하는 것
```
CI 왜 필요한가요?
- 10명의 개발자가 열심히 개발 -> 1주일이 지나고.. -> Merge Hell...
- 모든 개발자들이 안심하고 개발하기 위해서 또, 나의 코드와 멘탈의 평안을 위하여..

CI 와 함께라면?
- 10명의 개발자가 열심히 개발
- 커밋!
- 로컬 테스트 통과 실패..
- 커밋!
- 코드베이스 머지
- 만족!

가능한 최대한 많이 빨리빨리 나의 코드를 코드베이스에 안착시키자!

테스트 코드 없는 무서운 버그 더미 코드를 애초에 코드베이스에서 쫓아내자!
```

- CD(Continuous Delivery)   
사용자에게 서비스를 지속적으로 배달한다는 의미 (코드베이스가 항상 배포가능한 상태를 유지하는 것)

```
CD 왜 필요한가요?
- 백엔드 코드 개발
- 프론트와 협업해야하니 배포를 해볼까?
- 저기 배포좀 해주세요...
- 앗 버그..! 다시 배포좀 해주세요.- 데브 서버에 누가 배포했나요? 제꺼 안되는데요;;
- 앗 죄송..
- QA 배포...
- 프로덕션 배포시 초긴장 유지
- 열심히 배포스크립트 작성, AWS 코놀 만지작.. 혹은 베어메탈?!
```

- Continuous Deployment   
코드 베이스를 사용자가 사용가능한 환경에 배포하는 것을 자동화함.

-> 즉, CI/CD 란 각각의 **개발자들이 개발을 하는 개발 환경을 사용자가 사용 가능한 서비스로 전달하는 모든 과정을 지속 가능한 형태**로 또 가능하다면 자동으로 해서 **개발자와 사용자 사이의 격차를 없애는 것**이다.   
-> 이러한 과정에는 **코드를 빌드**하고, **테스트**하고 **배포**하는 활동이 있다.

<img src= "./img/Jenkins_1-1.png">

### 2. 젠킨스의 기본 개념과 동작 방식
- Java Runtime 위에서 동작하는 **자동화 서버**!
- **빌드, 테스트, 배포** 등 모든 것을 자동화 해주는 자동화 서버!   

기본개념
- Java Runtime Environment 에서 동작
- 다양한 **플러그인**들을 활용해서 각종 자동화 작업을 처리할 수 있음
- 일련의 자동화 작업의 순서들의 집합인 **Pipeline** 을 통해 CI/CD 파이프 라인을 구축함 

Plugin
- 정~~~말 많은 플러그인들이 존재
- 대표적인 플러그인들
  - Credentials Plugin
  - Git Plugin
  - Pipeline (핵심 기능인 파이프라인 마저도 플러그인!)
  - 처음에는 그냥 Recommend 해주는 것을 깔면 어지간한건 다 깔려있다.

```
Credentials Plugin
- Jenkins 는 단지 서버일 뿐이기 때문에 배포에 필요한 각종 리소스 ( 가령 클라우드 리소스 혹은 베어메탈에 ssh 접근 등) 에 접근하기 위해서는 여러가지 중요 정보들을 저장하고 있어야 한다.
- 이런 중요한 정보(AWS token, Git access token, etc ...) 들을 저장해 주는 플러그인

Docker plugin and Docket Pipeline
- Docker agent 를 사용하고 jenkins 에서 도커를 사용하기 위함

Pipeline
- 파이프라인이란 CI/CD 파이프라인을 젠킨스에 구현하기 위한 일련의 플러그인들의 집합이자 구성
- 즉 여러 플러그인들을 이 파이프라인에서 용도에 맞게 사용하고 정의함으로써 파이프라인을 통해 서비스가 배포됨
- Pipeline DSL(Domain Specific Language) 로 작성   

Pipeline 을 구성하는 요소
- 파이프라인이란 CI/CD 파이프라인을 젠킨스에 구현하기 위한 일련의 플러그인들의 집합이자 구성.
- 즉 여러 플러그인들을 이 파이프라인에서 용도에 맞게 사용하고 정의함으로써 파이프라인을 통해 서비스가 배포됨
- 두가지 형태의 Pipeline syntax가 존재(Declarative, Scripted Pipeline) 우리는 최신이자 더 가독성 좋은 문법을 가진 Declarative Pipeline syntax를 사용

Pipeline
- Stages Section : 어떤 이들을 처리할 건지 일련의 stage 를 정의함
- Steps Section : 한 스테이지 안에서의 단계로 일련의 스텝을 보여줌

```
<img src = "img/Jenkins_1-2.png">   

Pipeline Syntax   
- Post section   
스테이지가 끝난 이후의 결과에 따라서 후속 조치를 취할 수 있다.
- 여러 slave node 를 두고 일을 시킬 수 있는데, 이처럼 어떤 젠킨스가 일을 하게 할 것인지를 지정한다.
- 젠킨스 노드 관리에서 새로 노드를 띄우거나 혹은 docker 이미지등을 통해서 처리할 수 있음


Steps
- Steps 내부는 여러가지 스텝들로 구성
- 여러 작업들을 실행가능
-  플러그인을 깔면 사용할 수 있는 스텝들이 생겨남   
(간단히 말하자면, 플러그인 아래에 사용할 수 있는 스텝(기능)들이 있는데 그 스텝들을 사용할려면 플러그인이 필요함)
https://www.jenkins.io/doc/pipeline/steps/

젠킨스 설치하기
- yum update -y
- Jenkins 패키지 추가   
  sudo wget -O /etc/yum.repos.d/yum.repos.d/jenkins.repo http://pkg.jenkins.io/redhat/jenkins.repo&&   
  sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key   
- Install java, docker, git   
  sudo yum install -y java-1.8.0-openjdk jenkins git docker   
- 자바 버전 8 로 설정   
alternatives --config java   
service jenkins start

### 개발 환경 및 CI/CD 의 기본 동작 이해
개발 환경의 종류
- 개발자가 개발하는 **Local 환경**
- 개발자들끼리 개발 내용에 대한 통합 테스트를 하는 **Development 환경**
- 개발이 끝나고 QA 엔지니어 및 내부 사용자들이 사용해 보기 위한 **QA 환경**
- 실제 유저가 사용하는 **Production 환경**
- 쉽게 DEV, QA, PROD 환경으로 부르자

개발 프로세스   
1. 개발자가 자신의 PC에서 개발을 진행한다.
2. 다른 개발자가 작성한 코드와 차이가 발생하지 않는지 내부 테스트를 진행한다.
3. 진행한 내용을 다른 개발자들과 공유하기 위해 git과 같은 SCM에 올린다. => 흔히 dev 브랜치
4. Dev브랜치의 내용을 개발 환경에 배포하기 전에 테스트와 Lint 등 코드 포맷팅을 한다.
5. 배포하기 위한 빌드과정을 거친다.
6. 코드를 배포한다.
7. 테스트를 진행한다.
8. 위 모든 과정을 DEV,QA,PROD 환경에서 모두 하고 각각에 맞는 환경에 배포한다.

여러 배포 환경의 관리
- 인프라를 모듈화 하여 어떤것이 변수인지 잘 설정하고 이를 잘 설계하는것!
- 가령 APP_ENV 처럼 현재 배포하고자 하는 것이 무슨 환경인지 설정하고 앱 내에서 사용하는 다양한 변수들을 APP_ENV 에 맞게 잘 가져다 쓰는것이 핵심.
- 서비스 내부의 변수 뿐만 아니라 클라우드 리소스를 많이 활용해서 개발하는 요즘에는 클라우드 리소스 내에서 인프라별 키관리가 매우 중요해서 aws system manager 의 parameter store 와 같은 키 관리 서비스를 사용하는 것을 추천

예시 배포 환경
1. 웹사이트 코드를 작성한다.
2. 웹사이트 코드를 린트, 웹팩 빌드 해서 AWS S3 bucket 에 html 파일을 업로드 한다.
3. Node.js 백엔드 코드를 typescript 작성한다.
4. 위 코드를 javasript compile 하고, 테스트 코드를 돌려서 도커 이미지를 만들어 ECR 에 올린다.
5. 업로드한 ECR 이미지로 ECS 서비스를 재시작 한다(rolling deploy) => continuouse deploy


---
### 모르는 용어 노트   
Continuous : 지속적인, 끊김없는   
쿠버네티스 :    
QA :   
프로덕션(production) : 제작, 생산  
베어메탈 : 하드웨어 상에 어떤 소프트웨어도 설치되어 있지 않은 상태  
Docket agent :  
Pipeline syntax :    
Declarative :    
Scripted Pipeline :    
slave node :   
Production :   
APP_ENV :   
parameter store :   
AWS S3 bucket : 데이터 가용성 및 보안과 성능을 제공하는 객체 스토리지   
ECR(Elastic Container Registry) 이미지 : 도커 이미지를 저장하는 프라이빗 레포지토리     
ECS(Elastic Container Service) 서비스 : 도커 컨테이너 기반으로 서비스 운용을 가능하게 해주는 간단한 서비스   
countinuouse deploy :   