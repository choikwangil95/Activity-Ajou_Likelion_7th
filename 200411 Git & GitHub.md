## Git & Github

### 1) Git
Git은 <strong>로컬</strong>에서 관리되는 <strong>버전 관리 시스템</strong>(VCS : Version Control System)이다<br/><br/>

`로컬? / 버전 관리?`<br/>
- 로컬(local) : 내가 개발하고 있는 <strong>개발환경</strong><br/>
- 버전 관리 시스템(VCS) : <strong>코드가 변경된 부분을 모두 기억</strong>해준다는 의미입니다.<br/>

개발을 하면서 코드가 수정될 때마다 파일로 일일이 따로 저장해주거나 수동으로 백업해두기는 매우 번거로운 일인데
어떤 부분이 수정됐는지 쉽게 볼 수 있고 수정된 부분을 이전 버전으로 롤백 하는 등의 기능들을 제공해줌<br/>
코드 수정에 따른 위험성을 줄일 수 있기 때문에 개발자에게 필수적인 시스템임</br></br>

`그니까 나중에 코드 이상하게 됬을때 땅을치고 후회하지 않기위해 사용하는 것`<br/></br>
그러면 코드를 어떻게 관리하는데 ?

#### Git 저장소
Git은 코드를 관리하기 위해 원격 저장소와 로컬 저장소 두 종류의 저장소를 제공<br/>

- 원격 저장소(Remote Repository): 파일이 원격 저장소 전용 서버에서 관리되며 여러 사람이 함께 공유하기 위한 저장소
- 로컬 저장소(Local Repository): 내 PC에 파일이 저장되는 개인 전용 저장소
<br/>

내 컴퓨터에 로컬 저장소를 만드는 방법은 두가지가 있다.<br/>
- 내 컴퓨터에서 폴더를 만들어서 Git 저장소를 새로 만들거나 <br/>
Windows:<br/>
`$ cd /c/user/my_project`<br/>
<br/>
그리고 다음과 같은 명령을 실행한다<br/>
`$ git init`<br/>
이 명령은 .git 이라는 하위 디렉토리를 만든다.<br/>
.git 디렉토리에는 저장소에 필요한 뼈대 파일(Skeleton)이 들어 있다<br/>
이 명령만으로는 아직 프로젝트의 어떤 파일도 관리하지 않는다<br/>
Git이 파일을 관리하게 하려면 저장소에 파일을 추가(add)하고 커밋(commit)해야 한다.<br/>
```
$ git status // 변경된 파일 상태(status) 체크
$ git add . // 변경 된 모든 파일을 추가
$ git commit -m "첫번째 Version을 커밋한다" // 파일을 staging area에 등록
```

- 이미 만들어져 있는 Git 저장소를 Clone해서 로컬 저장소로 복사해는 것<br/>
다른 프로젝트에 참여하려거나(Contribute) Git 저장소를 복사하고 싶을 때 git clone 명령을 사용한다.<br/>
Windows:<br/>
`$ cd /c/user/my_project`<br/>
내가 가져오고 싶은 폴더로 이동 한 다음<br/>
`$ git clone <내가 가져오고 싶은 저장소의 URL>`<br/>
다음과 같이 명령어를 해주면 저장소의 데이터를 모두 가져와서 자동으로 가장 최신 버전을 Checkout 해 놓는다

