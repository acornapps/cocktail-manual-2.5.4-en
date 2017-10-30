### 3.1.5 - 1 빌드 추가

도커 이미지에 대한 빌드 작업을 추가합니다. 어플리케이션 다운로드, 빌드, 이미지 빌드로 총 3가지를 선택하여 할 수 있습니다.

##### a\) 서비스 -&gt; 서비스 우측 v 버튼 클릭\(메뉴 활성화\) -&gt; 빌드 관리 -&gt; 빌드 추가![](/assets/빌드 추가2.png)![](/assets/빌드 추가.png)![](/assets/빌드 추가3.png)

| ![](/assets/빌드 추가4.png) | 생성할 빌드의 이름을 넣습니다. |
| :--- | :--- |
| ![](/assets/빌드 추가5.png) | 어플리케이션 다운로드 입니다. **리파지토리의 종류** - git 저장소가 있고, **프로토콜 유형** - HTTP/HTTPS를 지원합니다. **GIT 저장소 유형** - Private/Common을 지원합니다. **리파지토리 URL** - 받고자 하는 git URL을 넣습니다. **리파지토리 ID와 패스워드** - git 저장소에서 소스를 다운로드할 때 필요한 ID와 패스워드입니다. **타겟 프랜치** - 다운로드할 소스의 현재 브랜치정보를 입력합니다. |
| ![](/assets/빌드 추가6.png) | 어플리케이션 빌드입니다. 소스의 컴파일이 필요할 경우 사용됩니다. **커맨드** - 빌드하면서 실행될 작업입니다. **호스트 경로** - 작업이 이루어질 컨테이너 경로와 그와 마운트되는 호스트경로를 작성합니다.  **Working dir** -실제 컨테이너안에서 작업할 경로로 컨테이너 경로와 맞춰줍니다. **이미지** - 빌드시 사용될 이미지 입니다. |
| ![](/assets/빌드 추가7.png) | 앞서 작업된 소스로 도커파일을 만들어 이미지를 만들고 해당이미지를 레지스트리 저장소에 저장하는 단계입니다. |


