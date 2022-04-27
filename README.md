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

## 3.1 TailwindCSS Setup

Tailwind 셋업을 하고 그 설정이 잘 되는지 테스트를 해봄

그럼 맨 먼저 Tailwind CSS를 설치해봄

우리는 Tailwind와 함께 postcss랑 autoprefixer도 사용함

npm install하고 대문자 -D 다음에 tailwindcss postcss autoprefixer를 써줌

터미널에 npm install -D tailwindcss@3.0.11 postcss@8.4.5 autoprefixer@10.4.1 입력

그러고 나면 여기 devDependencies에 보임

됐다면 다음으로 넘어갈 수 있음

여기 보이는 것처럼 우리는 Tailwind 버전 3를 쓰고 있음

터미널에 npx tailwindcss init -p 입력

그리고 enter를 누름

그러고 나면 파일이 두개 생기는데 postcss.config 파일 하나랑 tailwind.config 파일 하나가 생김

postcss.config 파일은 아예 안 건듦

건드릴 필요가 없는게 우리에게 필요한 간단한 설정이 이미 되어있음

그러니 이 파일은 닫고 tailwind.config.js 파일을 열어보면 여기서는 몇가지를 수정해줘야함

우리는 아직 Tailwind가 어떻게 작동하는지 모르는데, Tailwind가 어떻게 작동하는지 모르면 지금 우리가 할 것들이 조금은 헷갈릴 수 있음

그래서 우리가 해야하는 것은 Tailwind에게 어디에서 Tailwind를 사용할 것인지 말해줘야함

Tailwind는 이 파일을 바라보고 있고 이 파일에서 우리는 어느 component 혹은 page에서 Tailwind를 사용할 것인지를 Tailwind에게 말해줘야함

예를 들어서 Tailwind를 Pages에서 사용하고 싶다면, 우리는 Tailwind에게 Pages로 가서 우리가 거기서 Tailwind를 사용한 것을 찾으라고 말해주는 것임

그래서 우리가 해줘야 하는 것은 pages의 슬래쉬( / ) 모든 디렉토리의 모든 파일에서라고 써주고 그다음에는 다양한 확장자명을 명시할 수 있음

이렇게 써준 것의 의미는 Tailwind가 pages 폴더의 모든 폴더의, 모든 파일인데 확장자명이 .js(아마도) 혹은 .jsx 혹은 .ts(타입스크립트) 혹은 .tsx인 파일에서 쓰일 수 있다는 것임

이렇게 쓰면 Tailwind가 pages 폴더의, 모든 디렉토리의 .js, .jsx, .ts, .tsx로 끝나는 모든 파일에서 우리가 Tailwind를 사용한 것을 찾아냄

아직 폴더는 없지만 할거니까 똑같은 것을 components에도 해줌

이 경로에 있는 것들에도 Tailwind를 사용함

다시 한번 여기 이렇게 적는 것은 우리가 이 경로에서 Tailwind를 사용할거라고 Tailwind에게 알려주기 위함임

만약에 항상 .tsx만 사용할거라면 이 앞에꺼는 안써줘도 됨

이렇게만 해줘도 됨

우리의 경우에는 예를 들어서 .tsx만 사용할거라면 이렇게만 해줘도 된다는 것임

방금처럼 이렇게 나열하면 "또는"의 의미임

공식 문서에서는 이렇게 하라고 하는데 이것도 좋기는 함

알아두면 좋음

이것의 의미는 pages 폴더에 있는 모든 폴더의, 그리고 이 확장자 중 하나를 가지는 모든 파일이라는 의미임

이것도 마찬가지로 components 폴더의, 모든 폴더의, 그리고 이 확장자 중 하나를 가지는 모든 파일이라는 의미임

tailwind.config를 닫아줌

이제 금방 한 셋업이 잘 작동하는지 확인해봄

pages 폴더로 가서 index 파일을 열어가지고 코드를 씀

100말고 500으로 함

아직 이해가 안돼도 됨

아직 여기에 이 이쁜 색상이 보이지 않아도 걱정하지마

걱정하지말고 일단 해봄

이것이 작동하는 것을 보고 다음 강의에서 알려줌

만약에 타입스크립트를 사용하고 있지 않다면, 이것이 보이지 않을거고 이것도 안보임

이것은 타입스크립트임

그 점 알아둠

만약에 타입스크립트를 사용하고 있다면 이것을 본적이 없었을 수 있지만 NextJS에서는 타입을 이런식으로 import해서 사용함

import type 이렇게 함

이 코드가 잘 되는지 안되는지 테스트하기 전에 styles 폴더의 global.css 파일을 확인해봄

이 global.css 파일은 create-next-app을 할때 함께 생성됨

그리고 _app.tsx 파일에 이미 import가 되어있음

무료 강의에서 설명했던 개념이라 _app이 무엇인지 다시 설명하지는 않음

이것은 공부하고 와야함

그리고 여기에 css를 import하면 이것이 global css가 된다는 것도 알아야함

이제 global.css 파일로 가서 전체 선택을 한 다음에 전부 삭제해줌

이제 우리는 코드 세 줄을 써줄건데 첫번째 @tailwind는 이것이 base가 됨

그리고 다른 하나도 @tailwind인데 components라고 써주고, 마지막은 @tailwind 다음에 utilities라고 해줌

몇가지 짚을게 있는데 아마도 이 자동완성이 안 뜰 수 있음

걱정하지 말아

이 강의 마지막에 그거에 대해서 이야기함

그리고 여기를 보면 문제가 있다고 나옴

이 라인을 보면 이렇게 생긴 밑줄이 그어져있고 "모르는 규칙이다"라고 말하고 있음

이것도 걱정하지 말어

아마 지금이 우리가 이 css 파일을 열어 볼 거의 마지막 순간이 될 것임

이제 이것을 저장해줌

이것이 무엇을 하는건지는 나중에 알아봄

지금 당장은 전체적으로 잘 작동이 되도록 설정을 하는거니까 이 파일을 닫고 콘솔로 가서 npm run을 실행해줌

그럼 모든 script를 알려주는데 우리의 픽은 dev임

그러니까 npm run dev를 해줌

그럼 서버가 localhost:3000에 열리고 여기를 보면 우리한테 정보를 주고 있음

여기 있는 warning은 React 18의 RC 버전을 사용하고 있지 않다면 나타나지 않음

그러니까 이것에 대해서는 걱정하지 말고 만약 React 18 RC버전을 사용하고 있다면 아직 출시되지 않은 버전을 사용하고 있다는 것을 알려주는 정보임

다음으로 넘어감

브라우저로 넘어오면 여기 보임

파란색 텍스트랑 빨간색 배경이 떴음

Tailwind CSS 설정이 완성되서 잘 실행되고 있는것 같아 보임

마지막으로 한번 더 믿어줘

이리로 와서 text-blue-500을 text-black으로 바꿔줌

그럼 여기 보이는 것처럼 업데이트 됐음

자동으로 새로고침이 되었고 모두 다 잘 작동하고 있음

셋업은 여기까지임

이번 시간에 한 것은 Tailwind CSS를 설치하고 npx tailwind init을 사용해 자동으로 두 파일을 생성했음

그 다음에는 여기 content를 수정해서 우리가 이 위치에서 Tailwind를 사용할거라고 Tailwind에게 말해줬음

그리고 나서 global style에 Tailwind를 포함시켜줬음

그리고 테스트를 하기 위해서 이 강의의 첫번째 Tailwind 클래스 두개를 적용해봤는데 아직 이해가 안될수도 있음

bg-red가 무슨 의미인지, 여기에 왜 빨간 것이 있고 왜 나는 없는지 아마 아직 이해가 안될테지만 걱정하지 마

다음 섹션에서 알아봄

Tailwind CSS 투어에서 봄