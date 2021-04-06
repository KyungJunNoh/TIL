# AWS EC2
- Amazon Web Services 클라우드에서 확장 가능한 컴퓨팅 용량을 제공.

### Amazon EC2의 대표적 기능
Amazon EC2는 확장 가능하고 오류 복원력이 뛰어난 엔터프라이즈급 애플리케이션을 구축할 수 있는 여러가지 강력한 기능을 제공합니다.
- 베어 메탈 인스턴스
- Amazon EC2 플릿을 사용해 컴퓨팅 성능과 비용을 최적화
- 인스턴스 일시 중지 및 다시 시작
- GPU 컴퓨팅 인스턴스
- GPU 그래픽 인스턴스
- 높은 I/O 인스턴스
- 고밀도 HDD 스토리지 인스턴스
- 최적화된 CPU 구성
- 유연한 스토리지 옵션
- 종량 과금제
- 다중 위치
- 탄력적 IP 주소
- Amazon EC2 Auto Scaling
- HPC(고성능 컴퓨팅) 클러스터
- 향상된 네트워킹
- 탄력적 패브릭 어댑터(HPC클러스터를 위한 빠른 상호 연결)
- AWS PrivateLink에서 사용 가능
- Amazon Time Sync Service
- 다양한 운영체제(Amazon 머신 이미지(AMI))
- AWS Marketplace를 통한 다양한 소프트웨어

### 탄력성 있는 웹 스케일링 컴퓨팅

Amazon EC2를 사용하면 몇 시간 또는 며칠이 아닌 몇 분내에 용량을 늘리거나 줄이거나 할 수 있다. 또한 Amazon EC2 Auto Scaling을 통해 EC2 플릿의 가용성을 유지하고 필요에 따라 집합을 자동으로 확장 및 축소하여 성능을 극대화하고 비용을 최소화할 수 있다. 여러 서비스의 크기를 조정하려면 AWS Auto Scaling을 사용하면 된다.

```
여기서잠깐, Auto Scaling이란?
- 애플리케이션을 모니터링하고 자동으로 조정하여, 최대한 저렴한 비용으로 안정적이고 예측이 가능한 성능을 유지한다.
- AWS Auto Scaling을 사용하면 몇 분 만에 손쉽게 여러 서비스 전체에서 여러 리소스에 대해 애플리케이션 규모 조정을 설정할 수 있다.
```

### 통합성
Amazon EC2는 Amazon Simple Storage Service(Amazon S3), Amazon Relational Database Service(Amazon RDS) 및 Amazon Virtual Private Cloud(Amazon VPC) 등의 대부분의 AWS 서비스와 통합되어 있어, 컴퓨팅, 쿼리 처리 및 광범위한 애플리케이션 간 클라우드 스토리지에 대해 완전하고 안전한 솔루션을 제공합니다.

### 안정성
Amazon EC2는 교체 인스턴스를 빠르고 예측 가능하게 실행할 수 있는 매우 안정적인 환경을 제공합니다. 이 서비스는 Amazon의 입증된 네트워크 인프라와 데이터 센터 내에서 실행됩니다. Amazon EC2 서비스 수준 계약은 각 Amazon EC2 리전에 대해 99.99%의 가용성을 보장한다.

### 보안
AWS에서 가장 우선순위가 높은 것이 클라우드 보안이다. AWS 고객은 보안에 가장 민감한 조직의 요구 사항에 부합하도록 구축된 데이터 센터 및 네트워크 아키텍처의 혜택을 누릴 수 있다. Amazon EC2는 **Amazon VPC**와 함께 작동하여 사용자 컴퓨팅 리소스에 보안성 및 강력한 네트워킹 기능을 제공한다.

```
여기서잠깐, Amazon VPC란?
AWS 클라우드에서 논리적으로 격리된 공간을 프로비저닝하여 고객이 정의하는 가상 네트워크에서 AWS 리소스를 시작할 수 있다.
```
