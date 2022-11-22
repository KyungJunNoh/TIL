# K8s Component(쿠버네티스 구성요소)
##### Kubernetes를 배포하면 클러스터가 생성됩니다.
##### 클러스터 안에 포함된 구성요소를 설명하겠습니다.
<img src="./img/components-of-kubernetes.svg">

### Control Plane 구성 요소
##### 컨트롤 플레인의 구성 요소는 클러스터에 대한 전역 결정(설정?, 예: 예약)과 클러스터 이벤트 감지 및 응답(예: 배포의 복제본 필드가 충족되지 않을 때 새 Pod 시작)을 내립니다.

#### kube-apiserver 
##### API 서버는 Kubernetes 컨트롤 플레인의 프런트 엔드입니다.

##### <span style="color:red">Kubernetes API 서버의 주요 구현은 kube-apiserver 입니다. kube-apiserver는 수평 확장, 즉 더 많은 인스턴스를 배포하여 확장하도록 설계되었습니다. kube-apiserver의 여러 인스턴스를 실행하고 해당 인스턴스 간에 트래픽의 균형을 맞출 수 있습니다.</span>

#### etcd
##### 모든 클러스터 데이터에 대한 Kubernetes의 백업 저장소로 사용되는 일관되고 가용성이 높은 키 값 저장소입니다.

#### kube-scheduler
##### 할당된 노드가 없는 새로 생성된 팟을 감시하고 실행할 노드를 선택하는 컨트롤 플레인 구성 요소입니다.

##### 일정 결정에 고려되는 요소에는 개별 및 집단 리소스 요구 사항, 하드웨어/소프트웨어/정책 제약, 선호도 및 반선호도 사양, 데이터 지역성, 워크로드 간 간섭 및 기한이 포함됩니다.

#### kube-controller-manager
##### <span style="color:red">컨트롤러 프로세스를 실행하는 컨트롤 플레인 구성 요소입니다. 논리적으로 각 컨트롤러는 별도의 프로세스이지만 복잡성을 줄이기 위해 모두 단일 바이너리로 컴파일되고 단일 프로세스에서 실행됩니다. 이러한 컨트롤러의 일부 유형은 다음과 같습니다.</span>

- ##### 노드 컨트롤러: 노드가 다운될 때 이를 인지하고 대응하는 역할을 합니다. 작업 
- ##### 컨트롤러: 일회성 작업을 나타내는 작업 개체를 감시한 다음 해당 작업을 완료할 때까지 실행하는 팟을 만듭니다. 
- ##### EndpointSlice 컨트롤러: EndpointSlice 개체를 채웁니다(서비스와 포드 간의 링크 제공). 
- ##### ServiceAccount 컨트롤러: 새 네임스페이스에 대한 기본 ServiceAccount를 생성합니다.

#### cloud-controller-manager
##### <span style="color:red">클라우드별 제어 논리를 포함하는 구성 요소입니다. 클라우드 컨트롤러 관리자를 사용하면 클러스터를 클라우드 공급자의 API에 연결하고 해당 클라우드 플랫폼과 상호 작용하는 구성 요소를 클러스터와만 상호 작용하는 구성 요소에서 분리할 수 있습니다. </span>
##### cloud-controller-manager는 클라우드 공급자와 관련된 컨트롤러만 실행합니다. 자체 구내 또는 자체 PC 내부의 학습 환경에서 Kubernetes를 실행하는 경우 클러스터에는 클라우드 컨트롤러 관리자가 없습니다.

<br>

### 노드 구성요소
##### 노드 구성 요소는 모든 노드에서 실행되어 실행 중인 팟을 유지&관리하고 Kubernetes 런타임 환경을 제공합니다.

#### kubelet
##### 클러스터의 각 노드에서 실행되는 에이전트입니다. 컨테이너가 포드에서 실행되고 있는지 확인합니다.

##### <span style="color:red">kubelet은 다양한 메커니즘을 통해 제공되는 PodSpec 세트를 가져오고 해당 PodSpecs에 설명된 컨테이너가 실행되고 정상 상태인지 확인합니다. kubelet은 Kubernetes에서 생성되지 않은 컨테이너를 관리하지 않습니다.</span>

#### kube-proxy
##### kube-proxy는 각 네트워크에서 실행되는 네트워크 프록시입니다.