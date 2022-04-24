# Carrot Market

Serverless Carrot Market Clone using NextJS, Tailwind, Prisma, PlanetScale and Cloudflare.

## 3.0 NextJS Setup

이번 강의에서는 우리의 Next.js 앱을 위한 셋업을 함

왜냐하면 React 18에 대해 이야기 해야하기 때문임

React의 가장 최신 버전인데 이 강의를 어느 시점에 보느냐에 따라 설치 과정에 변경사항이 있을 수 있음

가장 먼저 타입스크립트를 사용할지 말지를 결정해야함

앱에 타입스크립트를 사용하고 싶지 않다면 npx create-next-app@latest라는 명령만 실행해주면 됨

나는 여기에서 실행함

하지만 타입스크립트를 사용하고 싶다면 달라짐

사용했으면 좋겠음

왜냐하면 타입스크립트 사용은 아주 좋은 개발경험이 될거고, 두번째로는 타입스크립트를 Prisma와 Next.js와 함께 사용하면 생산성이 향상되고 실수가 덜 발생하기 때문임

그래서 타입스크립트를 사용함

터미널에 npx create-next-app@latest --typescript 입력함

엔터를 치고 나면 내 프로젝트 이름은 carrot-market이라고 할거고, 그러고 나면 dependencies를 설치하기 시작함

이전에 말했던 것처럼 React 18이 등장했고, 원한다면 지금 당장 테스트 해볼 수 있는 아주 멋진 새로운 features를 가지고 있음

그런데 문제는 아직 공식 출시된게 아니라는 것임

아직 안정적인 버전이 아니고 대중을 위해 출시된게 아니라는 것임

3단계가 있음

첫번째는 Alpha, 그 다음은 Beta, 그 다음은 RC 혹은 Release Candidate라고 부름

Alpha나 Beta 단계에서는 변경사항이 생길 수 있음

그래서 보통은 Alpha나 Beta 단계의 상품은 사용하지 않음

왜냐하면 변경사항이 있을 수 있고, 코드가 바뀌거나 버그가 생기는 등등의 이유 때문임

그래서 그 단계에서는 사용하지 않지만, Beta 단계 이후에는 React팀이 상품의 feature가 완성되고, 더 이상의 변동사항이 없을거라고 판단하면 RC 혹은 release candidate라는 것을 만듦

release candidate는 React의 확정된 버전이고, 이것이 바로 나중에 공식 출시되는 버전의 React가 됨

이것이 바로 지금 React 18이 거치고 있는 일련의 과정임

강의를 녹화하고 있는 지금 이 시점에는 React 18의 안정적인 버전이 공개되지 않았음

지금 React.js 18은 RC, 즉 release candidate 단계에 있음

여기서 포인트는 RC는 나중에 출시될 안정적인 버전과 완전히 동일하다는 것임

조금 더 마무리 작업을 하고 터치가 조금 더 있을 수 있지만 크게 변하는 것은 없음

API도 동일하고 코드도 동일함

그러니 지금 사용할 RC 버전을 사용한다면 나중에 공식 출시될 React 18의 안정적인 버전을 사용하는 거랑 동일함

언제 이 강의를 시청하느냐에 따라서 React 18이 아직 RC 단계에 있을 수도 있고, 이미 정식 출시가 되었을 수도 있음

지금 이 강의를 보고 있다면 이 영상의 위쪽을 확인해봄

거기에 React 18이 공개적으로 출시되었는지 혹은 RC(release candidate) 단계에 있는지 적혀있음

만약 지금도 React 18이 RC 단계에 있다면 계속 따라와주길 바람

아직 알려줄게 더 남았음

만약 React 18이 공식 출시된 상태라면 여기서 더 할 것은 없음

다음 영상으로 감

다시 말하자면 이 강의를 언제 보느냐에 달렸음

이 영상의 상단에 소식을 업데이트함

거기에 React 18이 RC 단계에 있는지 아닌지에 대한 노트가 있음

React 18이 아직 RC 단계에 있다면 이 영상을 계속 봄

왜냐하면 React 18의 RC버전을 사용해봄

만약 React 18이 이미 출시되었다면 이 앱을 생성할때에 이미 React 18로 생성이 되었음

carrot market 코드로 들어가서 package.json을 확인해봄

여기를 보면 dependency가 3개 있음

next, react, react-dom인데 react랑 react-dom은 17버전임

이제 우리는 이것을 React 18의 RC(release candidate) 버전으로 업그레이드 해줌

우리가 해줘야 하는 것은 콘솔로 가서 npm i next@latest (Next.js는 가장 최신 버전으로) 입력함

확실히 가장 최신버전을 사용하기 위해서 이렇게 해주고 react@rc (ReactJS는 RC 버전으로) react-dom@rc (그리고 ReactDOM도 RC 버전으로 설치해줌)

터미널에 npm i next@latest react@rc react-dom@rc 입력

이렇게 하면 모든 것이 가장 최신 버전으로 설치됨

여기를 보면 이제 React 18이 설치되었음

만약 이 파일을 열었을때 React 18이 이미 설치되어 있다면 이 과정을 할 필요가 없음

React 18이 이미 정식 출시가 되었다면 이 과정을 할 필요가 없음

셋업은 여기까지임

지금 나는 git repository를 삭제하고 새로운 레포를 하나 다시 만듦

터미널에 rm -rf .git 입력 후 git init 입력

그리고 이제 깃허브에도 작업을 해줌(https://github.com/new에서 함)

이 레포는 carrot market이라고 부름

여기는 이렇게 썼음

"이 앱은 serverless 당근마켓 클론이고 NestJS, Tailwind, Prisma, PlanetScale 그리고 CloudFlare가 사용됨"

이 놈을 Public(공개)로 만들어주고 README 파일은 추가 안할거고, .gitignore도 안하고 라이센스도 선택하지 않음

그리고 레포 생성 버튼을 눌려주면 끝임

이 레포의 URL을 복사해서 여기에 붙여넣어줌

git remote add origin하고 그 뒤에 복사한 URL을 넣어줌(git remote add origin https://github.com/kko0831/carrot-market.git)

이 README 파일도 바꿔줄 수 있는데 안에 있던 내용은 전부 필요 없고, 제목은 Carrot Market이라고 해준 다음에 작성하고 싶은 내용을 쓰면 됨

이번 영상은 여기까지고 셋업도 여기까지임

가기전에 하나 삭제하고 싶은게 있는데 예를 들어서 이것도 지우고, Home.module.css에게 이별을 고함

pages 폴더에 index랑 app 파일이 있는데, 이것은 괜찮고 api 폴더는 삭제함

이것은 나중에 함

app 파일에서는 아무것도 안바꿈

반면에 index 파일에는 많은 것들이 들어있음

그러니 여기 return에 들어있는 전부를 지움

일단 null을 가지고 있음

나중에 봄

그리고 이 위에 있는 것들도 지움

다 끝났고 이제 시작할 준비가 되었음

이제 우리는 Tailwind 설정을 해줄건데, 그것은 다음 강의에서 이어서 함