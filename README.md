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

## 4.0 Introduction

이번 강의에서는 Tailwind란 무엇인지 그리고 왜 Tailwind가 다른 CSS 프레임워크랑 다르고 더 좋다고 생각하는지에 대해 알아봄

Tailwind CSS는 유틸리티 우선 CSS 프레임워크임

여기서 유틸리티라는 것의 의미는 Tailwind가 아주 많은 클래스네임을 가지고 있다는 뜻임

우리는 그것을 유틸리티라고 부름

그러니까 Tailwind CSS는 아주 큰 CSS 파일이라고 보면 됨

아주 크고 클래스네임을 아주 많이 가지고 있는 CSS 파일임

우리가 개발자로서 하는 것은 각 클래스네임을 가져다가 조합을 해서 아름다운 무언가를 만드는 것임

클래스네임은 예를 들어 여기 flex가 있는데 flex라는 클래스네임임

그래서 이 클래스네임을 컴포넌트에 사용한다면 그 컴포넌트는 display: flex를 가지게 됨

또 예를 들어서 pt-4를 사용한다면 그 컴포넌트는 padding-top: 4를 가지게 됨

그런데 이 숫자는 픽셀이 아님

이거에 대해서는 나중에 알아봄

이렇게 사용해주면 끝임

클래스네임을 만들어서 그것을 가져다가 css 영역에 다시 써줘야하는 일은 하지 않아도 됨

예를 들어서 텍스트를 가운데 정렬하고 싶다면 text-center를 적어주면 됨

이 모든 클래스네임은 다 개별적임

각각의 기능이 있음

display: flex를 해주는 클래스네임이 있고, padding-top: 4를 해주는 클래스네임이 있고, text-align: center를 해주는 클래스네임이 있음

이것을 함께 사용하면 flex container에 padding-top이 4만큼 있고, 텍스트 가운데 정렬이 되도록 할 수 있음

그것을 이 멋진 demo에서 확인해볼 수 있음

여기에 추가되는 클래스네임에 주목해줌

여기에 클래스네임이 추가되면 변화가 생김

rounded-full이라는 클래스네임을 네모에 추가하고 있음

높이 24, 너비 24의 네모에 적용해보면 rounded-full의 효과가 무엇인지 알 수 있음

그럼 새로고침을 해서 처음부터 봐보면 여기 사람 사진이 있는데 여기에 rounded-full을 주면 이렇게 변함

그리고 mx-auto를 주면 수평 가운데 정렬이 되고, font-medium을 주니까 중간크기의 폰트가 적용되고, 이 여자분의 이름에 text-sky-500을 주면 텍스트의 컬러가 바뀜

text-center를 하면 텍스트가 가운데 정렬이 됨

클래스네임을 추가하고 조합하는 것이 전부임

아주 멋진 아이디어임

모든 클래스네임을 여기에 써줘야 하는 것은 맞지만, 한번 익숙해지면 이것이 얼마나 생산적인지 여러분이 느낄 수 있음

예시를 하나 더 보여주고 싶은데 예를 들어 여러분이 이런 것을 만들고 싶다면 div를 만들기만 하면 됨

그리고 클래스네임 bg-white를 주면 됨

그럼 배경색이 white가 됨

그럼 끝임

여기 보면 그림자가 있는데 박스에 그림자를 주고 싶다면 클래스네임에 shadow라고 넣어주면 됨

아주 간단함

만약 테두리가 이렇게 둥글었음 좋겠다면 클래스네임에 rounded를 넣어주면 됨

여기 w-96이라는 것이 있는데 96 픽셀은 아니고 다른 것임

어쨌든 너비를 96만큼 주게 됨

그럼 이렇게 보임

이렇게 심지어 너비를 위한 클래스네임까지 있음

얼마나 간단한지 봄

색상도 봐봄

이 흰색 배경의 색상 컨테이너를 만들고 그 안에 색상표를 넣고 싶다고 가정했을때, 우리는 여기에 grid라고 써주기만 하면 되고 그러면 display: grid가 추가됨

여기에 열을 10개를 만들기 위해서 grid-cols-10이라는 클래스네임을 써줬고, 열 사이 간격을 2만큼 주기 위해서 gap-2를 넣었음

정말 심플함

그리고 나서 네모네모를 원한다면 aspect-square만 추가해주면 됨

그리고 배경색을 넣고 싶다면 bg-다음에 배경색을 써주면 됨

색상명을 추측하거나 자동완성 하는 방법에 대해 알려줄거니까 걱정하지마

여기 50부터 900까지 숫자가 있는데 이것은 색의 채도를 의미함

하지만 아주 만들기 쉬움

여기 보이는 것처럼 클래스를 조합하기만 하면 됨

조합만 잘해주면 UI가 만들어짐

여기 또 봄

이것을 serif 폰트로 만들고 싶다면 font-serif라는 클래스를 사용하면 됨

여기는 sans 폰트를 쓰고 싶다면 클래스 font-sans를 사용하면 됨

내가 제일 좋아하는 것은 shadow임

shadow를 좋아하는 이유는 그림자를 넣으면 사이트가 아주 예뻐짐

그런데 그림자는 만들기가 아주 어려움

그림자를 만드는 방법을 기억하기가 어려움

box-shadow에다가 x, y, blur 등등을 설정해줘야하기 때문임

그 대신에 Tailwind CSS에는 shadow-sm이라는 클래스네임이 있음

이것을 쓰면 이렇게 생긴 작은 그림자가 만들어짐

아주 심플함

클래스네임을 기억하기 어렵다는 것도 알고 나중에 어떻게 하면 더 수월하게 할 수 있는지 알려줌

아무튼 클래스네임 만으로 스타일을 준다는 것은 정말 쉬운것 같음

shadow라고 쓰면 이런 그림자가 생기고 shadow-xl 혹은 shadow-2xl이라고 하면 이런 그림자가 생김

Tailwind에 대해 이야기 했던게 Tailwind는 여러분을 제한하지 않는다는 것이었음

제한이라고 하면 다른 CSS 프레임워크에는 각각의 스타일이 있음

아주 예쁜 스타일이긴 하지만 각자 고유한 스타일이 있어서 많은 사람들이 똑같은 프레임워크를 사용하다보면 어느 웹사이트를 갔을때 어떤 프레임워크로 만들어졌는지 알 수 있게 됨

특히 Bootstrap이나 Ant Design이 그럼

Bootstrap으로 만들어진 웹사이트를 가면 그것이 Bootstrap으로 만들어진 것인지 알아볼 수 있음

다 똑같은 버튼을 사용하고 비슷비슷하게 생겼음

Tailwind CSS에는 정해진 스타일이 없음

서로 다른 클래스네임만 있음

클래스네임들을 원하는대로 조합함

예를 들어 이런 디자인이 이런거를 만든다고 했을때 디자인이 모두 다름

이것이 Tailwind CSS로 만들어졌는지 알아볼 수 없음

이것도 마찬가지임

사람들이 많이들 사용하는거니까 이것은 그럴 수 있음

하지만 이것을 선택했다고 가정하면 이것을 비교한다면 완전히 다른 디자인에 완전히 다른 바이브임

내가 이것을 클릭하면 클래스네임이 바뀜

여기 It's tiny라는 부분이 있는데 이것은 나중에 다룸

여기 있는 예시에서 배운 것들을 가지고 지금은 일단 Tailwind CSS를 써봄

그리고 나서 나중에 It's tiny가 무슨 말인지 알려줌

Tailwind CSS는 아주 많은 클래스네임을 가지고 있는 큰 파일임

그 모든 것을 유저에게 쓰라고 넘기지는 않음

그 많은 것을 다 가져다 쓰라고 하지는 않음

그래서 just-in-time compiler에 대해서도 나중에 알아봄

그것도 아주 좋음

또 흥미로운거 하나는 이것을 가지고 반응형 디자인을 만드는 것이 정말 쉬움

여러분이 응용할 수 있는 클래스네임 혹은 medium, large, x-large, 2x-large 화면 각각에만 해당하는 클래스네임을 제공함

나중에 이것을 다시 볼거니까 잘 모르겠어도 걱정하지 말고 이 클래스네임은 라지 사이즈 화면에만 적용됨

여기 grid-cols-1이라고 써있는건 기본적으로는 열을 하나만 가진다는 것인데 라지 사이즈 화면이 되면 열을 두개를 가지게 됨

여기서 예시를 확인해볼 수 있음

지금은 열이 두개가 있는데 모바일 화면으로 다시 돌아간다고 하면 열이 한개만 보이게 됨

반응형 디자인에 대해서 다시 이야기할거니까 걱정하지 말고 hover 같은 state도 있고 이것도 다 살펴볼거니까 걱정마

다크모드에 대해서도 알아봄

Tailwind에 대한 소개 내용이었음

Tailwind가 얼마나 멋지고 얼마나 생산적인 개발자로 만들어주는지 알아봤음

이런 effect랑 transforms, 이미지 filter도 있음

그리고 마지막으로 World-class IDE Integration에 대해 이야기하고 마쳐볼까함

왜냐하면 Tailwind CSS는 엄청 많은 클래스네임을 가진 큰 파일이기 때문에, 지금 아마 이 클래스네임을 기억하기 아주 어려울거라 생각하고 있음

이 클래스네임을 봄

각각 다 무엇인가를 하고 있는 아이들이지만 이것을 다 기억하기는 어려움

그래서 우리가 원하는 것은 이렇게 자동완성이 되도록 하는 것임

이런 자동완성을 원한다면 vscode로 가서 Extensions로 가서 Tailwind CSS IntelliSense라는 extension을 설치해줌

Tailwind Labs가 만든 Tailwind CSS IntelliSense가 여기 있음

이것만 설치해주면 됨

이것을 설치하면 Tailwind를 사용할때 여기 이 나이스한 컬러를 볼 수 있음

아주 나이스한 자동완성도 사용할 수 있게 됨

이렇게 text-cen까지만 써도 자동완성이 제공됨

그리고 또 클래스네임에 마우스를 올리면 Tailwind CSS 파일에 있는 클래스네임을 보여줌

다시 한번 말하자면 Tailwind CSS는 아주 큰 CSS 파일임

그래서 이렇게 text-center라는 클래스네임을 사용하면 text-align: center를 사용한 것이 됨

정말 간단함

클래스네임 text-center를 쓰면 text-align: center가 적용됨

또 이렇게 flex라는 클래스네임을 쓰고 마우스를 그 위로 올리면 이것이 바로 Tailwind가 가지고 있는 클래스네임임

정말로 클래스네임을 엄청 가지고 있는 파일임

정말 간단함

여기 쓰인 text-black은 text-black이라는 클래스이고 이 색상을 가지고 있음

여기 이거에 대해서는 나중에 또 이야기함

Tailwind CSS의 홈페이지를 확인해봄

클릭하면서 확인해볼 수 있는 데모들이 있고 아주 좋은 예시들임

그리고 Tailwind CSS IntelliSense를 설치함

그럼 vscode에서 자동완성을 제공받을 수 있고, 마우스를 위에 올리면 사용하고 있는 클래스네임을 확인할 수 있음

이것이 Tailwind CSS를 더 잘 이해할 수 있도록 도와줌

다시 한번 말하지만 Tailwind는 단지 아주 많은 클래스네임을 가진 CSS 파일임

엄청 많음

마우스를 위에 올리면 클래스네임도 볼 수 있음

그리고 grid 같은 것을 쓰면 여기 grid를 쓰고 있다고 나오는데, 좋은 것은 금방 우리가 설치한 extension 덕분에 flex랑 grid가 서로를 상쇄시킨다는 것을 알 수 있음

둘 중 하나를 골라야함

여기 실수하고 있다고 알려주기까지 함

아주 좋음

자동완성도 되고 마우스를 올려놓으면 클래스네임의 실제 css도 보여주고 실수를 했을때에도 알려줌

그러니까 Tailwind CSS IntelliSense를 꼭 설치하길 바람

홈페이지의 demo도 꼭 확인함

이해하는데 아주 도움이 많이 되니까 클릭을 해봄

다음시간에는 Tailwind CSS에 대해 더욱 익숙해져봄

여기까지가 Tailwind 소개였음

## 4.1 Test Drive part One

이번 강의랑 아마도 다음 강의에서까지 우리는 이 아름다운 UI 컴포넌트를 Tailwind CSS로 만들어봄

자동완성과 함께 Tailwind CSS를 사용할때에 작업흐름이 어떤지 보여주려고 함

사이즈에 대해서도 조금 다룰거고, Tailwind CSS를 사용하면 작업속도가 얼마나 빨라지는지도 알 수 있음

하나 주의할 것이 있음

만약 여러분이 Tailwind CSS를 처음 사용하는 거라면 바로 사용을 시작하기 어려울거라는 점임

클래스네임도 조금 알아야하고 사이즈랑 숫자도 좀 알아야 하기 때문임

Tailwind를 막 시작하는 시점에는 많은 사람들이 문서랑 코드를 왔다갔다 하고 그것은 지극히 정상적인 것임

그러니 처음부터 엄청 쉬울거라는 기대는 하지마

하지만 사용할수록 점점 더 쉬워짐

주로 필요한 클래스네임은 몇 개 안되기 때문임

예를 들어서 margin, padding, flex, (아마도) grid, background color, text color 같은 것들만 알면 됨

이런 것만 가지고도 우리가 하려는 것을 만들 수 있음

엄청나게 많은 것을 기억할 일은 없음

조금만 알면 됨

문서에도 다 적혀있음

그리고 지금 보게 될 자동완성 기능 덕분에 클래스네임을 추측해볼 수도 있음

그러니까 당황할 필요 없음

시작을 하기가 너무 어렵고 클래스네임이랑 숫자들을 잘 모르겠더라도 Tailwind를 써보는만큼 사용하기 더 쉬워짐

그러니까 이 컴포넌트를 만드는 것부터 시작을 해봄

이 디자인은 전설적인 Denys Sergushkin이라는 사람이 만들었음

아무튼 컴포넌트 만들기를 시작해봄

div 태그로 시작하고 모든 것이 다 div로 이루어짐

text 신경 안쓸거고 span 태그나 HTML5, 좋은 코드 이런것들 신경 안씀

모든 것은 div로 씀

포인트는 Tailwind CSS를 연습해보는 것임

우리는 1, 2, 3, 4개의 div가 필요하니까 div 태그를 만들어서 4개를 만들어주고 이제 첫번째 컴포넌트를 만들어봄

그것은 바로 wrapper 컴포넌트임

여기부터 시작해봄

bg-까지만 써주면 색상이 엄청나게 많이 보임

색상 옵션이 엄청 많음

slate-400을 선택해봄

그 다음에는 padding을 함

여기 보이듯 위-아래랑 좌-우에 padding이 있음

Tailwind에는 옵션들이 있음

예를 들어 p를 쓰고 대쉬(-) 다음에 10 같은 숫자를 써줌

곧 숫자에 대해서도 알아볼거니까 염려마라

이렇게 하면 사방으로 padding을 10만큼 줌

(마우스를 올려보면) padding이 사방에 적용된 것을 알 수 있음

혹은 pt라고 하면 이것은 padding-top을 줌

pb라고 하면 padding-bottom을 줄거고 (pl은) padding-left, (pr은) padding-right임

만약에 px라고 하면 padding을 좌우로 줌

x축으로 padding을 줌

혹은 py라고 하면 수직방향으로 padding을 줌

여기 보면 padding-top이랑 padding-bottom이 들어갔음

이제 숫자에 대해서 이야기 해봄

여기 padding 10은 padding으로 10 픽셀을 주는 것이 아님

이것은 rem 단위로 되어있음

단위가 다르고 이것은(2.5rem) 40px랑 동일함

rem은 우리의 document 폰트 사이즈를 기준으로 하고 그렇기 때문에 브라우저에 따른 사이즈를 달리 가질 수 있게 해주기도 함

크기가 우리의 화면을 보고 그에 따라 달라짐

그래서 rem을 사용하면 반응형 디자인을 하기가 아주 용이함

이렇게 하면 40px 값을 얻을 수 있음

이제 사이즈 값에 대해 알아봄

뒤에 있는 숫자를 없애보면 0부터 1, 2, 3, 4, 5 이렇게 쭉 있는데 16부터는 4씩 커짐

16, 20, 24 등등 80이 될때까지 4씩 증가함

여기를 보면 (60 이후에는) 8씩 증가해서 80, 그리고 96까지임

이제 1의 단위이고 그리고 여기를 보면 자동완성을 통해서 픽셀값은 얼마인지 확인할 수 있음

아주 중요함

우리의 경우에는 위아래에 padding을 10, 즉 40픽셀을 줌

그리고 이거는 5만큼 줌

이것이 되는지 봄

아무것도 보이지 않음

왜냐하면 아직 박스가 하나도 없기 때문임

그럼 박스를 만들어봄

멀티플 커서를 만듦

아무것도 안 보임

그러니까 전체에 padding을 줘봄

전체에 10정도 줘봄

아닐수도 있는데 사이즈에 대해서는 너무 신경쓰지마

연습과정일 뿐임

이제 전부 둥글게 만들어줌

이렇게 rounded라고 써주면 다양한 rounded를 볼 수 있음

여기를 보면 이것을 선택하면 border-radius: 1rem이 적용될거라고 알려줌

1rem은 16픽셀이고, 16px는 우리 document의 폰트 사이즈임

우리는 -lg를 해줌

-xl를 해볼까

-2xl로 해줌

그런데 여기까지 지웠는데도 자동완성이 뜨지 않는다면 ctrl+space를 눌러봄

그럼 자동완성이 로드됨

3xl를 해볼까

이제 margin-bottom을 함

그런데 우리는 margin-bottom을 해줄 필요가 없음

container에서 설정해줄 수 있음

그리고 나서 space를 써줄 수 있음

space는 요소 사이에 margin을 만들어줌

예를 들어 space-y-5라고 해줌

이렇게 하면 자식요소에 margin을 줄 수 있음

그래서 space-y-5를 하면 hidden 되어있지 않은 모든 자식요소에 margin-top과 margin-bottom을 줌

아주 멋진 helper function임

여기를 보면 어떤 것은 그냥 CSS 속성인데 다른 것은 helper function임

예를 들어 이것도 마찬가지임

space-y-5를 사용하면 모든 자식요소에 자동으로 margin-top이랑 margin-bottom을 줌

그래서 이 페이지의 "검사"로 들어가서 보면 각 요소가 margin을 갖게 된 것을 알 수 있음

마지막 요소에도 margin-top이 있는데 첫번째 요소에는 없음

아주 멋짐

다른 것은 다 margin-top이 있음

그런데 첫번째 요소는 아님

아주 좋음

원한다면 flex를 쓰지 않아도 됨

대신 grid를 쓰면 됨

grid만 써주면 끝임

gap-5라고 해볼까

이것은 단순 CSS의 display: grid이고 그 다음은 gap임

이런 것을 보여주고 싶었음

이제 그림자를 해봄

이 디자인에는 그림자가 아주 많음

그리고 나는 금방 padding을 좀 더 줘야 한다는 것을 깨달았음

여기를 14, 혹은 20으로 고쳐봄

그리고 이것은 10으로 고침

여기 그림자도 줘봄

이것을 다 선택함

이제 저기에 그림자가 생겼음 

그럼 맨 첫번째 친구를 작업해봄

첫 타자는 이 친구임

Select Item, Grey Chair, Tooly Table, Total이라고 쓰여있음

그리고 여기에는 의자의 가격을 써줌

이것을 그대로 복사해서 두개로 만들고 그 다음에는 Total을 위한 div 태그를 만들어줌

최종가격을 위한 span 태그를 만들어줌

그리고 이제 Checkout 버튼을 만들어줌

그럼 div 태그를 써주는데 semantic 이런 것은 일단 신경쓰지마

button 같은 다른 태그는 사용하지 않음

다 div로만 함

여기에는 Checkout이라고 써줌

이것이 우리의 마크업 코드임

이제 스타일을 만들러가봄

Select Item은 다른 친구들보다 좀 더 크고 검정색임

그리고 가장 먼저 폰트를 입혀볼까

여기에 font라고 써봄

font라고 쓰면 옵션이 많이 나오는데 semibold로 함

그럼 여기 보이는 것처럼 더 커짐

그 다음에는 텍스트 크기를 좀 더 키워봄

text-라고 씀

Grey Chair라고 쓰여있는 두 부분에는 텍스트에 회색 색상을 입혀줌

gray는 500정도 줘볼까

아주 좋음

이 둘의 부모요소는 flex 컨테이너가 되어야함

그럼 가격들이 오른쪽 끝으로 가게 됨

거의 다 해감

이제 첫번째 Grey Chair에 margin-bottom을 줘봄

그런데 생각해보면 Grey Chair를 Select Item이랑 아래의 Grey Chair랑도 떨어뜨려야하니 위아래 margin을 의미하는 my로 고쳐줌

내 생각에는 이것은 여기까지 하면 될것 같음

Total 부분을 해봄

Total은 이 부분에 있는데 margin-top이 필요해보임

여기를 보면 경계선이 있는데 걱정하지마

border 유틸리티도 있음

이제 이 부분을 해봄

이제 border를 해줌

전체 테두리를 설정해줄때에는 border 다음에 아무것도 안 씀

-t(위쪽 테두리), -b(아래쪽 테두리), -l(왼쪽 테두리) 또는 -r(오른쪽 테두리)를 써줌

우리는 border-t를 해줄거고 0, 2, 4, 8 중에서 선택할 수 있음

각각 8px, 6px, 4px, 0px를 의미함

이것처럼 숫자가 어떤 경우는 rem 기반이고 어떤 경우에는 px 기반임

그리고 여기에 자동완성이 되는 것이 아주 큰 도움이 됨

우리는 border-t-2를 씀

이렇게 생각할수도 있음

이거 너무 보기 좋지 않음

내가 만약 3.7px의 테두리를 가지고 싶다면 어떻게 할건데

걱정하지 마라

그것도 가능함

우리도 원한다면 값을 직접 명시한 클래스네임을 만들 수 있음

정말 멋짐

우리 이제 거의 다 했음

그리고 이것을 flex로 만들어줌

그럼 총 합계 금액이 저 오른쪽으로 갔음

여기 이 세개의 가격은 굵은 글씨니까 아주 빠르게 bold 처리를 해줌

이제 거의 다 왔음

첫번째 아이템이 거의 다 완성이 되어가고 있음

내 생각에는 Select Item이 아주 보기 좋음

이제 Checkout 버튼을 해줄 시간임

여기에 Checkout을 꾸며줘봄

className이라고 써준 다음에 여기에 margin-top을 아마 5정도 아주 작게 넣어줌

문제 없고 그리고 이것을 배경이 파란색인 버튼으로 만들어줌

줄바꿈을 해줄 필요는 없음

padding을 전체적으로 10만큼 줌

5로 해볼까

그리고 둥글게 만들어봄

그럼 다 했음

여기 이것을 우리가 만들어버림

예시랑 같이 봄

이것을 좀 더 작게 만들어줘도 됨

하지만 지금 보듯이 아주 잘 되고 있는 것을 알 수 있음

박스가 그리 크지 않기 때문에 padding을 수정해봄

그 다음에는 checkout 버튼을 해줌

이것을 어떻게 바꿔주냐면 w- 뭐라고 해줄건데 어떨때는 예를 들어 11 이나 20 같은 특정한 숫자를 선택할 수도 있지만 또는 원한다면 상대적인 사이즈를 선택할수도 있음

예를 들어 여기 이 사이즈를 살펴보면 이것은 50%의 너비를 줌

그러니까 우리는 20rem이라는 절대 수치를 적용할수도, 50%를 적용할수도 있음

우리는 50%를 적용해봄

이 친구의 클래스네임을 확인해보면 width: 50%라는 값을 가지고 있음

이러면 결과가 어떤지 확인해봄

이렇게 됐고 그 다음에는 양 옆의 margin을 auto로 해줌

그럼 다 됐음

여기까지가 우리의 첫번째 Tailwind CSS 테스트였음

다음 강의에서는 다른 컴포넌트를 만들어봄

이것이 좀더 둥글어야겠음

이것을 rounded-full로 변경해줌

## 4.2 Test Drive part Two

오늘의 마지막 카드로 가봄

이번에 할 것은 재미있음

왜냐하면 몇몇 element는 아마 상대적으로(relative) 배치되어있음

어쩌면 절대적(absolute)일 수도 있고 한번 봄

그러면 top부분과 bottom부분에서부터 시작해봄

그러면 여기에 div와 span을 만들어 주고, top 부분은 똑같이 Profile이라고 씀

bottom부분은 아주 많은 것들을 가짐

div가 있을 거고 그 안에 다음 두 가지를 포함한 또 다른 div가 들어감

그 두 가지는 바로 orders를 포함한 span과 숫자를 포함한 span임

숫자는 340으로 함

그 다음에는 프로필 사진을 만들건데 진짜 사진 말고 그냥 원으로 만듦

그리고 여기도 위에랑 똑같이 해줌

Spent랑 우리가 쓴 돈을 써주면 그럼 끝임

이것은 접어두고 이것도 접어둠

두개의 span이 들어간 div를 한개 더 만들고 그 안에는 Tony Molloy랑 이 사람은 미국에 사니까 여기에 미국이라고 써주면 다 됐음

마크업은 여기까지고 이제 우리 카드를 만들어봄

먼저 파란 배경에 흰색 글씨 여기부터 해봄

이렇게 하면 됨

classname은 bg blue로 blue 500이 마음에 드니까 이것으로 계속 함

지금 보면 우리 카드가 padding이 있어서 이상해 보이니까 이 부분은 지워줌

대신 padding은 이쪽에 붙여줌

여기에는 overflow hidden을 넣음

그리고 우리 Profile 글자를 흰색으로 해야함

text white라고 className을 주고 그리고 크기는 아마 text 2xl정도로 하면 좋을 것 같음

이것이 우리가 원하던 것임

Profile은 완성함

여기 보면 아래쪽에 공간이 조금 있음

그러니까 padding을 조금 더 넣어줘도 좋을 것 같음

여기서 해봄

padding bottom, pb라고 하고 적당한 숫자를 골라볼건데, 14면 될 것 같음

그럼 얘는 닫아두고 아래 부분을 봄

여기에도 className을 만들어주고 rounded라는 것을 사용함

자동완성이 나오지 않으면 컨트롤 스페이스를 누르면 됨

그러면 rounded xl을 줌

당연히 아직은 rounded가 보이지 않는데 왜냐하면 이 부분을 Profile 위에 올려줘야 하기 때문임

그러면 이제 position relative를 씀

이 위치에 relative를 쓰면 됨

보다시피 간단하지

그리고 마이너스를 쓴 다음에 음수 값을 줌

마이너스 top 숫자는 14로 함

그런데 예뻐보이지는 않음

배경색을 bg white로 넣음

14는 너무 많은 것 같으니까 마이너스 5정도면 괜찮음

rounded는 2xl로 바꿈

이거랑 비슷하지

아마도 rounded가 2xl보다 큰게 나을 것 같음

이제 padding을 줄건데 6정도로 함

거의 다 왔음

그럼 이 Orders와 Profile 사진이랑 사용한 Money가 나온 div를 가지고 className에 flex를 써줌

그리고 justify between도 써줌

그러면 이제 아바타도 만들어봄

일단 height하고 width는 24px로 해봄

너무 큰 가

아직 모르겠음

그리고 배경색 bg는 red로 함

숫자는 400으로 함

이번에는 rounded full을 사용해 볼건데 이것은 사각형을 원으로 만들어주는 역할의 className임

이제 container로 가서 items end 이렇게 해줌

그런 다음에 이 container를 옮겨줄건데 relative로 만듦

여기에는 마이너스를 쓸건데 이것이 아마 우리가 거의 처음으로 본 음의 값임

-top 이렇게 씀

이런식으로 음수 값을 쓸 수 있음

-10으로 붙여봄

어떻게 됐는지 확인해봄

다시 여기로 와서 마이너스 16정도로 해봄

나쁘지 않음

이제 Orders랑 Spent도 고쳐줌

Orders랑 Spent를 둘 다 열어주고 두 component들 모두 className으로 flex랑 flex column을 가짐

items center까지 씀

여기를 한번 확인해봄

Orders는 작고 회색임

Spent도 마찬가지지

Orders와 Spent 둘 다 작고 회색으로 만듦

text small이라고 하면 되겠지

그리고 text gray도 함

잘 됐음

그 다음에는 숫자 차례임

숫자들의 className은 조금 굵어야 하니까 font-medium으로 함

어때 보여

거의 다왔음

이제 여기 Tony Molloy부분을 고쳐줘야 하는데, 왜냐하면 우리가 이 부분을 relative하게 움직일거니까 Tony Malloy부분도 relative 해야함

그러니까 이쪽에도 똑같이 className을 붙여넣기 해줌

그리고 flex container로 flex direction은 col로 하고 그리고 items center까지 함

거의 다 왔음

우리 Tony Malloy에게 margin top을 더 줌

10px는 너무 많음

5px는 나쁘지 않음

두꺼운 글자랑 작은 글자는 간단히 끝냈음

className으로 text를 조금 더 크게 만듦

font medium으로 하고 그리고 미국 글자는 더 작아져야함

text gray 400은 너무 회색이니까 500으로 함

여기에서 문제는 absolute한 값을 적어줬다는 것임

그래서 이렇게 개체들을 움직이는 대신에 우리가 할 수 있는 것은 마이너스 margin top을 16만큼 줘봄

여기 넣었던 margin top은 지우고 -mt-10을 넣어줌

나쁘지 않음

마이너스 margin bottom은 5로 함

이제 다 됐음

이제 우리는 profile card를 만들었음

당연히 멋진 이미지와 아이콘 같은 것은 아직 없지만 충분히 멋짐

마음에 듦

괜찮은 것 같음

좀 더 통통하게 만들고 싶다면 여기로 와서 x 숫자를 조정해줄 수 있음

우리 예시와 조금 더 비슷해졌음

괜찮은 것 같음

이번 영상에서 무엇을 배웠지

tailwind는 아주 강력해서 relative(상대적인) 움직임부터 음의 값까지 사용할 수 있게 해줌

예를 들면 margin top을 마이너스 2.5rem으로 할 수도 있음

이것은 꽤 멋짐

flexbox를 조금 더 연습해 봤고 어떻게 원을 그리는지도 배웠음

이렇게 size를 이용하면 아주 간단했지

정말 멋진 것 같음

## 4.3 Test Drive part Three

이번 영상에서는 바로 이 component를 만들면서 Tailwind CSS의 테스트 드라이브를 마무리 해봄

원래 여기 두 가지를 만들려고 했었지만, 우리가 계속 하던 padding, margin 그리고 font size 이런거라서 굳이 둘 다 할 필요는 없을 것 같음

그 대신에 모두 합쳐서 이 화면으로 만들려고 함

그리고 rings와 input에 대해 얘기해 볼 기회도 가짐

이것을 배우면 참 멋있고 좋을 것 같음

지금쯤이면 tailwind CSS에 조금 익숙해지고 있으면 좋겠는데, 만약 복잡하거나 className을 기억하기 어렵더라도 걱정은 하지마.

이번 섹션 전체에서 계속 해봄

react component를 만들면서 Tailwind CSS로 스타일을 만들게 됨

지금 하고 있는 것과 같은 작업이겠지만 이제 캐럿마켓 UI를 만듦

그러니까 지금 복잡하게 느껴지거나 기억이 잘 안난다고해도 걱정마

TailwindCSS를 사용할수록 점점 쉬워지고 나아짐

그리고 보다보면 우리가 하는 것은 padding, margin, font, flex, grid 다 이런 것들임

그럼 시작해봄

우리의 markup을 만들어봄

먼저 span을 만들고 그 안에 화살표를 넣음

이모지에서 찾아봄(Mac:커맨드+컨트롤+스페이스바, Windows: 윈도우+마침표)

여기에 있는 화살표로 함

그리고 div를 만들어서 여기에 별모양이 있으니까 이모지에서 또 찾아봄

4.9를 써주고 그리고 하트를 위한 span도 만들어줌

이것이 우리의 top바가 됨

나는 의자 사진이 없으니까 아쉽지만 대신에 사각형을 넣어줌

이제 div를 열고 span안에다 Swoon Lounge라고 써줌

혹시나 모를까봐 Chair라고도 써줌

또 div를 하나 만들어서 여기에서는 input을 받아봄

input의 type은 radio로 함

3개를 만듦

그 다음에는 버튼이 필요함

여기까지 모두를 새로운 div 안에 넣음

그리고 마이너스와 플러스 Button들이 들어있는 div를 만듦

수량이 들어갈 span도 만듦

이 모든 div다음에 또 다른 div가 필요함

다음에는 div나 button 중 아무거나 만들어서 Add to cart까지 써줌

이제 다 있음

우리의 markup은 완성했음

버튼도 있음

필요한 것은 다 가지고 있음

우리 페이지가 여기에서 끝남

끝까지 표시되지가 않음

이것은 minimum height라는 className으로 해결할 수 있음

container로 와서 여기에는 height랑 width 둘다 가능함

다음 옵션은 full이나 screen인데 우리의 경우에는 screen이 필요함

이제 맨 아래까지 표시되지

그럼 header를 만들어봄

아주 쉬움

flex나 아마 shadow정도면 됨

같이 해봄

그리고 여기 하트는 그림자가 필요함

작은 shadow(md)로 할까

padding은 2정도면 괜찮을 것 같고 rounded는 md로 함

여기 잘 보면 있음

그리고 이 두 개에게 space를 x좌표로 3만큼 줌

보다시피 둘 사이에 간격(space)이 생겼음

그리고 Tailwind는 아주 멋진 helper function(도와주는 기능)이 있음

우리가 margin right, margin left 이런 모든 것을 직접 계산하지 않아도, 아주 간단하게도 space-x-3 이런식으로 적으면 알아서 계산을 해줌

엄청 심플하지

이 container에게 margin bottom을 줌

mb를 5정도로 하고 이제 이미지를 만듦

아쉽게도 우리는 이미지를 갖고 있지 않음

next.js에서 이미지를 사용하는 것은 일반적으로 img태그를 사용하는 것과 다르기 때문에 나중에 다룰거고 지금은 bg zinc로 함

나는 zinc가 좋음

그리고 height는 86으로 함

86은 없나봄

80은 있는 것 같음

너무 큼

나쁘지 않음

이제 다 됐음

이것은 div니까 width를 설정하거나 할 필요가 없음

다음으로는 space와 font를 설정할 차례임

이미지는 5만큼의 margin bottom을 가짐

이름인 Swoon Lounge는 className에 font medium을 줌

margin bottom은 1.5정도면 되겠음

Chair는 ClassName으로 text-xs(extra small), 색상은 text-gray-500임

그 다음에는 input이 들어간 space가 필요함

이 input은 수량과 함께 top, bottom space가 필요함

margin top을 2만큼 줌

margin bottom을 5로 함

여기로 와서 확인해봄

나쁘지 않음

이 div가 className flex, flex column이어야 하는 것을 잊어버렸음

우리의 Swoon Lounge가 있음

Swoon lounge가 좀 더 큰 text style을 가지면 좋겠음

text....lg 아니면 xl로 함

나쁘지 않음

margin bottom은 필요 없음

그러면 수량 버튼을 먼저 만들고 그 다음에 radio 버튼을 만듦

수량은 아주 쉬움

이제 이 두개를 flex로 바꾸고 싶음

이제 이 녀석한테 집중해볼까

className을 줌

padding을 2.5정도로 하고 가끔은 .5값이 있는데 없을때도 있음

1.5는 있는데 10.5는 없음

10.5는 안 나옴

8.5도 없고 여기에는 1.5, 2.5정도가 있음

이렇게 함

둘 다 background를 blue 200으로 함

어때보이는지 확인해봄

하지만 걱정하지마

이번에는 aspect라는 것을 줌

이렇게 하면 width를 10처럼 정해줘야함

aspect-square는 aspect-ratio라는 새로운 css property로 우리를 도와줌

이것을 지우고 한번 비교해볼까

사각형부분을 잘 봄

저장하고 이제 보면 정사각형이 아니게 됐지

하지만 aspect square를 사용하면 정사각형으로 변함

width도 꼭 같이 줘야함

이 안에 font를 medium으로 설정함

그리고 text는 xl로 색상은 이렇게 gray로 함

우리가 원하는만큼 멋지지는 않지만 꽤 괜찮음

그냥 font medium도 지워줘도 될 것 같음

꽤 괜찮음

다시 한 번 spacing을 사용함

여기로 와서, 둘 사이에 space를 주고싶다고 하자!

이렇게 space, x축방향으로.... 5만큼!

이제 모서리를 둥글게 해주면 다 될 것 같음

이 쪽의 padding은 필요없을 것 같으니 지움

그리고 버튼 크기만 줄여주면 다 될 것 같음

w8로 함

이제 가격하고 Add to cart 부분을 만들어봄

rings부분은 지금하기에는 너무 복잡할 수 있어서 나중에 함

450이랑 Add to cart를 할 차례인데 그냥 flex container니까 어렵지는 않음

flex, padding, background 이런 것들을 이용해서 두 개를 떼어놓으면 됨

이것은 className font medium으로 함

text는 크게 2xl로 함

잘 되나 봄

거의 다 됐음

여기는 justify-between이어야함

마지막으로는 padding을 3정도만 줌

나쁘지 않음

top과 bottom은(px) 2로 하고 좌우(py)는 5로 함

아직 충분하지가 않음

그러면 text를 좀 작게 만듦

이제 마지막 component까지 모두 끝났음

다시 한번 보면 우리가 하는 것은 flex를 이용함

그리고 space, margin, padding도 있었고 font medium, text 2xl 같은 것들까지 하면 이제 다 한 것임

이 코드들이 좀 무섭게 보일수도 있지만 우리가 클론할 캐럿마켓 화면을 켜서 들여다보면 디자인의 대부분은 spacing, margin 이런 것들임

그러니까 별로 걱정할 것은 없음

다음 영상에서는 TailwindCSS의 아주 멋진 기능인 rings에 대해 배워봄

보다시피 Tailwind CSS는 이렇게 class들을 가지는데 합쳐서 사용하면 아주 유용해짐

또 우리에게 지름길을 주는 helper class도 존재함

예를 들면 여기에 사용한 space 같은 것임

다시 한번 말하자면 이 space라는 애는 자식 component의 좌우 margin을 알아서 계산해줌

여기 아래에 있는 component들에게 margin right와 left를 줌

덕분에 우리는 space-x-5 이렇게만 쓰고 계산을 하지 않아도 됨

이런 것들이 될건데 radio 버튼에 스타일을 넣으면서 알아봄

## 4.4 Modifiers

이번 영상에서는 아주 멋진 기능인 modifier에 대해서 배울건데, 그 전에 여기 button 3개 먼저 만듦

이것이 더 쉬울 것 같아서 radio는 지우고 그냥 button으로 만들었음

width와 height는 5로 하고 rounded는 full로 함

그리고 첫번째 button의 background는 bg-yellow-500임

이제 저장하면 이것이 우리의 button이 됨

두번째 button의 색깔은 indigo로 해봄

세번째는 teal로 함

위에 space-x-2를 썼기 때문에 각 button들 사이에 자동으로 space가 생겼음

margin right이나 margin left에 생각할 필요가 없음

이제 Tailwind CSS와의 작업을 환상적이게 만들어주는 기능을 소개함

여태까지 우리가 한 것으로 봤을때 Tailwind는 꽤 멋짐

className만 썼는데 만들어졌음

우리가 직접 className을 만들고 기억하고 할 필요가 없음

Tailwind className과 자동완성을 사용하면 굉장히 생산적으로 만들 수 있었음

하지만 우리가 이제 배울 modifier라는 Tailwind기능은 우리를 한 수 위로 데려다 줌

이제 해볼 것은 여기에 있는 Checkout button을 바꾸고 싶음

이 button을 바꿈

먼저 이 부분을 열어주고 div를 button으로 바꿔줌

이제 내 마우스 커서가 button 위에 올라왔을 때 button의 색상이 변하면 좋겠음

원래 CSS할 때는 이런 식으로 만들었음

이것이 일반적인 CSS에서 사용하는 방법임

하지만 Tailwind CSS에서는 modifier라는 것을 이용할 수 있음

modifier는 바로 이런 것임

예를 들어 hover를 하고 싶으면 이 condition(조건)이 발생했을 때 실행될 property를 적어줌

예를 들어 지금 이 checkout button 위에 마우스를 hover할때, background color는 teal 500으로 함

이 부분은 위에서 사용한 bg blue와 같은 property임

차이점은 앞에 hover가 붙은 classname임

보다시피 이것은 classname임

Tailwind CSS는 아주 많은 class를 가진 아주 큰 CSS 파일이라고 한 적이 있음

예를 들면 이것은 classname이 hover: bg-teal-500임

그러니까 이 코드를 save한 다음에 넘어와서 확인해보면 잘 작동되는 것을 볼 수 있음

보다시피 hover할때 색상이 잘 변함

아주 간단하게 만들어냈음

이런 것이 modifier고 아주 강력함

우리는 hover와 같은 state를 타겟으로 하고 싶을때 modifier를 사용할 수 있음

또 예를 들면 viewports를 타겟으로 할 때도 modifier를 사용할 수 있음

예를 들면 mobile only, 큰 screen only임

화면 방향이나 인쇄시 인쇄 스타일에 따른 스타일을 조절할 수 있음

hover 다음에 일반 css 속성을 써줌

예를 들어봄

마우스를 hover하면 text를 검정색으로 바꾸고 싶음

이제 두가지 일이 일어남

첫번째 클래스가 선택되었으니 마우스 hover시에 background color가 teal이 될거고, 두번째 클래스도 똑같이 마우스 hover시에 text color가 black이 됨

보다시피 아주 완벽하게 작동됨

이것이 바로 modifier임

다시 한번 button을 보면 active라는 것도 있음

active는 내가 버튼을 클릭했을때 발생함

예를 들어 active modifier를 한번 사용해봄

여기로 와서 이렇게 active라고 써줌

내가 버튼을 누를때 background를 yellow 500으로 하고 싶음

이것이 active가 됨

이쪽으로 와서 클릭을 하면 active가 실행됨

한 가지가 더 있는데 바로 focus임

버튼에 focus가 가있을 때 text 색상을 red 500으로 함

오직 focus가 됐을 때만임

Focus가 일어난다는 것은 이렇게 선택창 초점이 나타날 때를 말함(tab으로 이동 중)

지금 우리의 button들에 focus해보고 있음

이제 확인 해보면 focus가 되니까 text가 red로 변했음

text말고 bg(background)를 바꿈

그러면 됐음

바로 이 멋진 것이 modifier임

이것이 바로 Tailwind CSS를 더욱 강력하게 만들어줌

아직 훨씬 더 많은 modifier들이 남아있음

정말 유용해서 소개해주고 싶은 것이 아주 많음

특히 group modifier나 sibling modifier 같은 것이 있음

모두 이 예시에서 다루게 됨

이번 강의에서 다 한다는 것은 아니고 지금의 이 UI 안에서 다룸

여기에 모두 적용시킴

우리 button 스타일을 이렇게 표현하고, button의 각 stage를 다르게 표현할 수도 있었음

className으로 우리의 button이 크고 작은 화면 크기에 따라서 어떻게 생겨야 하는지도 정할 수 있음

이 모든 것을 className으로 함

이 modifier라는 기능이 정말 판을 뒤집어 놓은 기능이라 소개하고 싶었음

꼭 다른 modifier에 대해서도 알려줌

예를 들면 다크모드가 있음

그것도 같은 방식으로 작동함

여기에 dark라고 쓰면 다크모드를 켰을때 해당하는 property가 적용됨

보다시피 syntax자체는 정말 이해하기 쉬움

여기는 condition부분이고 이쪽은 앞의 condition이 true일때 실행될 property임

버튼에 마우스를 hover하면 background가 teal색이 되겠고, 버튼에 focus가 가면 background는 red가 됨

그리고 마우스를 위에다 올리면 classname도 볼 수 있었음

이것이 우리가 사용중인 classname이고 focus가 되면 이러한 일들이 일어남

우리가 생각할 수 있는 모든 조합들이 존재하고 있음

modifier에 대해서 더욱 많이 알아봄

## 4.5 Transitions

지난 영상에서는 modifier가 얼마나 멋진지, 덕분에 Tailwind CSS가 얼마나 강력한지 봤음

그래서 이번 영상부터는 더 많은 modifier에 대해 배워봄

전에도 말했듯이 지금 하는 것들의 목적은 이것을 다 외우는게 아님

그냥 TailwindCSS로 무엇을 할 수 있는지 한바퀴 투어를 시켜주고 싶음

그래서 나중에 프로젝트나 회사에서 TailwindCSS를 사용해 디자인을 하고 싶을때 좀 더 편하게 느낄 수 있음

할 수 있는 것에 제한이 없다는 것도 알게 됨

이 섹션은 just in time compiler를 다루면서 마무리하게 될건데, 이것을 보면 TailwindCSS가 무한하다는 것을 알 수 있음

이제는 누구나 좋아할 것 같고 정말 멋진 것 같은 ring utility에 대해 배워봄

ring utility는 그 자체로 modifier는 아니지만 modifier와 함께 사용해서 멋진 효과를 낼 수 있음

우리의 button으로 가봄

button 3개를 만들었지

색상은 각각 yellow, indigo, teal로 했었음

이제 focus에 대해 아니까 user가 이 버튼을 누를 수 있게 하고, 버튼이 눌려졌다는 것을 볼 수 있게 함

react나 state 같은 것들을 쓸 필요는 없음

대신에 focus modifier와 ring utility라는 것을 사용함

먼저 여기 yellow button부터 봄

그리고 이 button이 ring을 가질거라고 말해줘야함

말 그대로 2만큼 ring 이렇게 써줌

확인해보면 벌써 border처럼 생긴 ring이 만들어졌음

이 ring은 굉장히 커스터마이즈하기 쉬움

이번에는 이 ring이 2만큼의 offset을 가진다고 함

이제 확인해보면 border가 조금 멀어졌음

여기 보이지

멋지게 살짝 공간이 생겼음

이제 이 코드 위에 마우스를 올려놓고 보면 이것이 하는 일이 box shadow를 만드는 거라는 것을 알 수 있음

우리가 여기에 보는 것은 기본적으로 box shadow임

border처럼 보이지만 이 사이 공간 등 많은 것을 마음대로 바꿀 수 있기 때문에 분명 많은 디자이너들이 좋아함

offset 8로 하면 아주 멀고 1로 하면 이정도임

다시 한번 여러분이 어떤 생각을 할지 앎

이런 생각을 함

만약 내 offset이 7이 되기를 원하면 어떡하지

7은 없음

만약 6이나 24이길 원한다면 어떡해

그래서 우리가 just in time compiler에 대해 배움

이것은 Tailwind 버전3에서 나온거라 정말 기대됨

일단은 offset 2로 해둠

이제는 ring의 색상을 바꿔봄

ring이라고 쓰고 이번에도 yellow로 함

ring-yellow-500이라고 써줌

이제 border 같은 것이 생겼음

이것은 button을 눌렀을때, 즉 button에 focus가 생겼을때만 발생시켜야함

그것이 우리가 원하던 거였음

이렇게 classname을 써주는 대신에 ring을 만들어주는 이 ring-2 classname을 button이 focus됐을때만 발생하도록 함

중요한 것은 내가 이 쪽의 code를 건드리지 않았음

이쪽에 focus하라고 하지 않았음

그럴 필요가 없음

여기도 똑같음

ring-yellow에 focus를 써주지 않았음

그 이유는 이 classname 위에 마우스를 갖다대면 알 수 있는데, 이 classname은 오직 CSS variable만 세팅한다는 것을 알 수 있음

이쪽도 똑같음

CSS variable만 세팅함

가끔 다른 classname들이 여러 variable을 쓰는 것을 볼 수 있음

예를 들어 이 ring-yellow-500은 ring opacity라는 variable을 정의하고 ring opacity(투명도)로 나눈 ring color값을 정의하고 있음

그 말은 우리가 ring 색상의 opacity까지 변경할 수 있다는 것임

그러니 위의 (opacity) variable을 조정하면 아래의 ring color도 바뀌겠지

왜냐하면 color값은 opacity의 영향을 받음

여기로 와서 ring opacity값을 0, 5, 10... 마음대로 바꿀 수 있음

이것이 하는 일은 단지 다른 variable을 세팅하는 거였음

보다시피 Tailwind는 정말 멋진 아키텍쳐임

단지 variable을 세팅함으로써 아주 멋진 일들을 가능하게 해줌

그러니까 이 classname에 focus를 붙일 필요도 없고 이쪽도 마찬가지임

ring-2 classname에만 focus를 붙이면 됨

여기서 모든 variable들을 가져오고 밑에서 그것을 사용하고 있음

그러면 잘 되는지 확인 해봄

여기로 와서 클릭하면 우리의 ring이 나왔음

ring을 보여주고 싶었던 이유는 코드를 봤을때 더 감명받았으면 했음

왜냐하면 이것들이 단지 여러개의 variable의 합이라는 것이 멋짐

이것이 Tailwind의 힘을 보여주는데 오직 variable을 바꾸는데에만 사용하는 classname이 있음

그리고 이 모든 variable을 가지고 값을 적용시키는 classname도 존재함

즉 여기 보이는 variable들은 모두 변경이 가능함

예를 들어 bg-yellow를 들여다보면 bg-yellow는 어떤 색을 bg-opacity라는 값으로 나눈 값을 가지고 있는데 그 bg-opacity가 바로 variable임

그 말은 우리가 이 classname도 찾아서 사용할 수 있음

직관적으로 classname을 찾아낼 수 있다고 전에도 말한 적 있음

그럼 bg-yellow-500이 이런 variable들을 쓴다는 것을 알게 됐으니 이 variable들을 modify 할 수 있음

background opacity를 써보면 bg opacity 설정 값이 100까지 있음

여기서는 50정도로 하면 좋을 것 같음

이제 달라진 것이 보이지

이것이 다른 classname을 찾아내서 더 많은 커스터마이징을 하는 방법임

TailwindCSS에서 사용할 수 있는 많고 많은 classname을 내가 다 보여줄 필요가 없음

그냥 마우스 커서만 올리면 알 수 있음

그러면 어떤 것을 바꿀 수 있는지 볼 수 있음

이번에는 transition을 추가해봄

이 button에 transition을 넣음

클릭했을때 이렇게 나오기보다는 transition이 있는 것이 좋을 것 같음

그러면 transition property를 사용해야겠음

여기 보면 여러가지의 transition효과가 있음

transition이 없을 때는 none, 모두에게 주려면 all, color에만 적용할 때, opacity에만, shadow 그리고 transform도 있음

그럼 transition colors를 선택하고 어떤지 확인함

colors를 선택하고 코드를 확인해보면, 이것은 대부분의 color와 관련된 variable을 가져다가 transition을 주고 있음

font나 background, border, text decoration color를 바꿀 수 있고, svg(벡터 이미지)의 fill과 stroke도 조절할 수 있음

아주 유용함

다른 것도 확인해봄

Transition all을 하면 모든 것에 transition효과가 적용됨

그냥 transition이라고만 하면 color, bg, box shadow, opacity, transformation 등에 적용됨

보다시피 고를 수가 있음

우리는 그냥 transition으로 함

box shadow를 바꿀건데 어쨌든 transition으로 감

이제 확인해 보면 아름다운 transition 효과가 나타났음

우리는 1초도 안 걸려서 transition이라고 써주기만 했음

보다시피 Tailwind는 이렇게 작은 helper들이 있어서 우리 app을 전문적으로 보이게 해줌

주어진 그대로 사용하기만 하면 됨

물론 transition도 커스터마이징할 수 있지만 딱히 그럴 필요도 없음

이 Transition이나 여기 shadow가 있는 box같은 것이 Tailwind의 장점인데 이것을 스스로 만들려면 힘듦

여기 transition안을 보면 자체적으로 function을 사용하고 있음

cubic bezier 그리고 필요한 value도 있음

그러면 이제 transition을 이용해 멋지고 섹시한 button들을 만들어봄

여기로 와서 두 줄에 모두 붙여넣기하고, color는 yellow에서 indigo와 teal로 바꿈

이제 모두 멋진 transition이 적용됐음

이제 진짜로 modifier를 다뤄볼거고 이것이 시간을 많이 절약해줌

사용하기에 정말 간단하고 시간을 많이 절약해줘서 개발자들이 좋아하는 기능임

## 4.6 Modifiers for Lists

이번 영상에서는 list를 다룰때 우리의 인생을 더 편하게 만들어 줄 modifier를 공부함

react 개발자로써 아주 많이 사용하게 됨

예를 들면 여기 list가 있음

array.map은 아주 자주 함

modifier를 사용하면 시간과 에너지를 아낄 수 있음

먼저 여기에 ul태그를 만들어줌

그리고 우리의 item들을 ul안에 넣음

그 다음에 아주 간단한 array를 하나 만듦

그리고 이 array를 map한 다음에 우리의 html을 return 해줌

key는 index로 하면 다 됐음

react를 사용하면 아주 흔하게 보게 되는 array.map 형태임

이제 만약에 첫번째 child의 외관만 바꾸고 싶다면 어떨까

이런 일은 빈번하게 일어남

첫번째 child에게만 border를 추가하고 싶을 수도 있음

우리는 일단 background 색을 먼저 바꿔봄

그러려면 먼저 이렇게 first라고 쓰고, bg 그리고 blue 50으로 함

그러면 이렇게 바로 적용됨

아주 간단했음

또 예를 들자면 last도 있겠지

똑같이 bg-blue-50으로 함

아주 잘 작동됐음

우리가 아는 것을 사용하고 있음

classname한 줄로 last child와 first child를 설정함

onlychild일 때 사용하는 only라는 modifier도 있음

이것이 onlychild라면 bg red 500으로 해봄

그런데 only는 어디에도 적용되지 않았음

왜냐하면 여기에는 여러 child가 있음

만약 여기 array의 숫자들을 한개만 남겨준다면 only child가 되겠지

이제 target으로 설정할 수 있고, list에 item이 하나라면 그것을 style 할 수 있음

당연하게도 이것은 child selector를 사용함

여기에 마법은 없음

그냥 CSS property들을 사용하고, CSS selector들을 사용하는 것뿐임

하지만 이것을 class에 넣음으로써, 아주 간단하게 사용할 수 있음

여기에도 보면 background의 opacity를 조절할 수 있지

이전 영상에서 봤던 것처럼 variable을 이용함

only도 해봤으니까 계속 가봄

이제 first, last나 only는 지우고, odd와 even(홀수,짝수)을 사용함

주로 list가 있으면 첫번째 항목의 배경을 다른 것과 다르게 표현할 경우가 많음

배경색을 다르게 해서 list처럼 보이게 함

그러니까 odd를 설정해봄

bg-blue-500으로 하고 even은 bg-yellow-500으로 함

개발자로서 이것은 아주 간단함

className을 지정해서 이것들을 target 할 수 있음

odd는 1,3,5 even은 2,4...임

지금은 그냥 투어만 하는거라고 했지

이것을 다 기억하고 있을 필요는 없음

무엇을 할 수 있는지 알려주는 것뿐임

또 다른 멋진게 있는데 바로 empty임

empty는 잘 모를 수도 있지만 Tailwind 기능이 아니고 그냥 CSS selector임

하지만 Tailwind를 이용해서 더 간편하게 사용할 수 있음

그럼 list를 A,B,C,D,E... 아무렇게나 만들어봄

그런데 이번에는 d를 빈 값(empty)로 해봄

이제 우리의 친구들에게 map을 써줌

여기에는 그냥 li로 함

그리고 우리의 친구(c)와 key로는 index(i)도 써줘야함

그리고 이 모든 것을 ul안에다 넣음

a,b,c와 empty(빈 값)이 있음

여기 li에 bg-red-500 classname을 넣음

그리고 vertical(세로)로 padding도 2만큼 줌

잘 보면 a,b,c가 있고 빈 값이 하나 있음

이것도 array를 구성하지만 글자가 없음

여기에 써줬음

이 자리에 empty가 들어감

이렇게 empty를 사용하면 비어있는 element에 색상을 넣을 수 있음

다시 한번 이것은 Tailwind의 마법이 아님

이것은 그냥 empty라는 pseudo selector를 이용하는건데, 있는지 몰랐을 수도 있지만 Tailwind를 이용해 사용할 수 있음

이렇게 멋지니까 보여주고 싶었음

이제 list에 값이 채워져있지 않아도 style 할 수 있음

주로 값이 empty일때 background color를 바꾸기보다는 그 empty한 값을 숨겨줄 수 있음

그럴때 사용할 수 있는 className으로는 hidden이 있음

이제 array에 빈 item이 있어도 그냥 hidden 으로 숨겨줄 수 있어.

이것이 내가 자주 쓰는건데 대부분의 경우에 비어있는 값의 색을 바꿔줄 일은 없음

empty hidden을 한다면 이것은 display none이랑 똑같음

이번 영상에서 배울 것은 여기까지임

별게 없어서 여기까지만 함

list에서 사용하는 utility를 보여주고 싶었음

다시 말하지만 이것은 tailwindCSS라서 할 수 있는 기능들이 아니지만, Tailwind가 className을 가지고 있어서 우리가 편리하게 사용할 수 있음

Tailwind의 특별한 기능이 아니고 CSS 기능임

그러면 다음 영상에서는 form에 관한 modifier들을 배움

input이 필요한 경우와 필요하지 않은 경우 이 모든 것과 group selection에 대해서도 배움

예를 들면 이런 질문을 하나 해봄

우리가 마우스를 이 container 위에 얹을 때를 어떻게 부르면 좋을까

예를 들면 이 Tony Molloy의 색상을 바꾸고 싶음

우리는 마우스를 위에 올렸을 때 button의 색상을 바꾸는 방법은 알지

하지만 마우스를 이 group 전체에 올렸을때에 이 글자의 색상을 바꾸려면 Tailwind에게 어떻게 말하면 될까

내가 원하는 것은 이런거임

Tony 글자에 마우스를 올려서 색상을 변하게 한다는게 아님

그건 이미 어떻게 하는 지 알고 있지

나는 내 마우스를 이쪽 프로필이나 아무 곳에 올려놓으면, 이 text의 color를 target으로 하고 싶음

그것이 group selection이 됨

## 4.7 Modifiers for Forms

form을 시작하기 전에 아주 멋진 group modifier에 대해 배워봄

저번 시간에 말했던 것은 마우스를 이 group 위 아무 곳에나 올리면 이름 text의 글자색이나 avatar의 배경색을 바꾸고 싶다고 했음

예를 들어 마우스를 여기에 올리면 avatar가 바뀜

마우스를 여기에 올려도 아바타가 바뀜

만약 일반적인 CSS에서 이것을 하려면 다음과 같이 해야함

group을 만들어주고 마우스를 hover 했을때 아바타를 target함

group 위에 마우스가 올라가면 avatar의 스타일을 바꿈

이제 이것을 어떻게 만들 수 있는지 보여줄건데 당연히 이런 CSS는 작성하지 않음

classname을 사용함

이것이 Tailwind CSS의 핵심임

먼저 우리가 target하고 싶은 그 group 안에 어떤게 포함되는지 Tailwind에게 알려줘야함

예를 들어 계속 말하지만 나는 이 card 전체를 target으로 하고 싶음

이것을 target으로 해서 내가 card 전체에 마우스를 올리면 avatar를 어떻게든 변화시키고 싶음

스텝1은 Tailwind에게 무엇이 target하려는 group인지 말해줘야함

우리의 경우에는 card의 container가 됨

한번 지워보면 사라짐

여기까지의 div가 card의 container임

그래서 이 자리에 group이라고 씀

그냥 group이라는 classname임

아주 간단함

스텝2는 그 group에 마우스를 hover 했을때 변화할 것을 정해줘야함

먼저 classname을 이용해 group을 정해줬으니까, 이제 변화시킬 item을 지정해주면 되는데 내 경우에는 여기 있는 avatar였음

이것이 avatar임

한번 지워서 확인해봄

이제 Tailwind에게 group은 알려줬고, 우리가 modify하고 싶은 item도 찾았음

이제 Tailwind에게 알려줄 것은 group 위에 hover가 되었을때 background color를 red 300으로 바꾼다고 함

잘되나 봄

여기로 와서 보다시피 아주 아름답게 작동함

마우스를 위에 올리면 잘 변하고 있음

원한다면 classname위에 마우스를 올려서 확인하면 group이라는 classname이 hover 상태일때 뒤에 있는 이 classname이 적용된다고 나와있음

아주 간단함

다시 한번 이것은 제일 먼저 group이라는 classname을 찾아가서 그 group이 마우스 hover 상태일때 이 classname이 적용됨

다시 한번 우리가 할 것은 뭐가 group인지 select 해주고, 그 안에서 group이 hover일때 어떻게 할지 정해줄 수 있음

색상의 transition도 할 수 있는거 잊지마

이제 확인해보면 아름다운 transition까지 보이지

너무 간단하고 이것처럼 복잡한 hover 상태에도 CSS를 직접 쓸 필요도 없음

당연히 이것이 group으로 할 수 있는 다가 아님

group을 입력하고 자동완성을 보면 우리가 할 수 있는 아주 많은 것들이 나옴

group이 first child일때, last child일때, only, odd, even일때 이것은 이미 이전 영상에서 해봤음

group이 필요할때 어떻게 할지도 정할 수 있음

예를 들면 input group이 필요할 때가 있을 수 있음

이 모든 것이 바로 group modifier임

이것을 설명하기 가장 쉬운 방법은 hover였음

아주 간단했음

우리가 할 건 group을 정해준 다음에, 그 group 안에서 group이 hover 상태일때 아니면 group이 first item이거나 무엇이든지 background color를 바꾸든지 무엇이든 할 수 있음

그럼 이제 form에 대해서 얘기해봄

selector를 form이랑 같이 사용하면 최고임

Tailwind CSS와 함께 form을 만들고 red label도 보여주고 아니면 필수 입력 input을 보여줄 수도 있고 그 input이 valid한지 아닌지 이런 것들을 아주 간단하게 할 수 있음

일단 여기에서 영상을 잠깐 멈추고 빠르게 form을 만들어서 옴

form이 완성되면 돌아옴

여기에 방금 말한 form을 만들어왔음

다른 것은 다 지웠는데 걱정하지마

나중에 다시 복원함

지금은 이것이 우리의 form이고 Tailwind CSS에서 사용할 수 있는 modifier들을 봄

기억할 건 이것은 Tailwind가 없이도 사용할 수 있는 CSS feature들임

지금부터 해볼 것도 이미 CSS에 존재하는 것들임

Tailwind가 마법을 부리는 것은 아님

우리가 그 전에 원에다가 ring을 그렸었는데 그것은 일반적인 CSS에는 존재하지 않음

ring이라는 property는 없음

그거야말로 Tailwind가 우리에게 주는 helper임

box shadow라는 기능을 활용해서 멋진 ring을 만들어줌

지금부터 할 것들은,

TailwindCSS가 없어도 사용할 수 있는 기능들이야.

CSS가 가지는 selector를 TailwindCSS가 활용함

그래서 우리가 할 것은 예를 들어 form 안에 input이 focus 되어있을때 생성되는 pseudo selector에 대해 봄

이렇게 Username이나 Password에 focus가 갈때 pseudo selector는 true가 됨

그것을 form에 적용해봄

예를 들어서 form안에서 (within) focus가 되면 색상을 bg-blue-100으로 바꿈

우리가 이 3가지 input에 focus하면 form에 변화가 생김

focus일때 아닐 때(blur) 이것이 첫번째로 해볼거였음

이제 우리 input 안에서 사용할 수 있는 것도 살펴봄

input안에서는 이런 것을 할 수 있음

예를 들어 input이 필요할때 border를 만들어줌

border를 2만큼 줌

그리고 border의 색상도 바꿔줌

border color를 yellow로 500정도로 함

보다시피 required input이 표현됐음

엄청 간단하고 쉽지

required를 지우면 모두 사라짐

또 말하지만 이것은 Tailwind 마법이 아님

확인해보면 required selector를 이용하고 있고 이것은 일반 CSS feature임

하지만 Tailwind로 아주 편리한 방법으로 사용할 수 있음

이번에는 invalid를 해볼까

만약 invalid일때는 background를 red 500으로 함

required이기 때문에 default값으로 invalid값이 됨

input에 무엇인가를 입력하면 더 이상 required 상태가 아니기 때문에 invalid가 아니게 됨

다시 말하지만 이것은 일반 CSS에서도 쓸 수 있음

Tailwind를 꼭 쓸 필요는 없음

Tailwind가 더 편리하게 해주기는 함

계속 해봄

여기에는 placeholder shown이라는 것도 있는데, placeholder를 보이고 있는지 아닌지에 따라 input을 커스터마이즈하게 해줌

만약 여기에 placeholder shown을 쓰고 placeholder가 shown일떄 bg color를 teal 500으로 함

지금은 value가 들어가있으니까 아무일도 일어나지 않았지만, 지워보면 보다시피 placeholder가 보일때의 input 스타일을 바꿀 수 있음

placeholder 자체를 스타일 할 수도 있음

원한다면 placeholder의 text를 red 500으로 바꿀 수도 있음

placeholder의 색상이 바뀌었고, 입력 text의 색상은 그대로 black임

많은 것을 해봤음

다시 한번 말하지만 이거 외울 필요는 없음

걱정말고 이런게 존재한다는 것만 알면 됨

우리는 input을 disabled(비활성화)할 수도 있음

예를 들어 여기를 disabled로 바꿔봄

disabled를 하면 클릭이 불가능해짐

여기는 클릭이 되는데 여기는 안 됨

그럼 disabled를 다른데도 쓸 수 있겠지

이번에는 disabled 되었을때 투명하게 만들어봄

disabled된 input은 보이지 않게 됐음

왜냐하면 disabled 시켰음

다시 required로 바꾸고 이제 좀 변화를 줘봄

이것이 required일때 background color를 yellow로 함

500으로 함

이번에는 invalid일때 background color를 red 500으로 함

valid일때도 해볼까

valid일때는 배경색을 teal 500으로 함

valid로 만들어봄(value를 입력함)

required도 해봤고 invalid도 됐고 valid도 확인했음

app을 만들때 주로 background color만 변경하지는 않겠지

대신에 우리는 border를 바꿔봄

왜냐하면 사람들이 입력하는 input이 원래 border를 가지고 있고 invalid일때는 red border를 가지잖아

이런 것들을 할 수 있음

Tailwind를 이용해서 이런 모든 것들을 할 수 있다는게 참 좋은 것 같음

또 말하지만 Tailwind라서 할 수 있는 것은 아님

Tailwind없이도 할 수 있는 CSS지만 이렇게 할 수 있다는 것을 보여주고 싶었음

Tailwind를 사용하면 거의 모든 것이 이미 만들어져있고 일일히 CSS 코드를 칠 필요가 없음

내 생각에 최고인 것은 이제 배워볼 peer modifier임

잠깐 녹화 멈추고 좀 지우고 왔음

이제 이것이 내 form임

background color도 지웠고 input과 submit만 남아있음

이 input도 좀 괜찮아보이게 만들었음

이제 peer modifier를 보여줄건데 이것은 사람들이 아주 많이 쓰는 패턴을 implement 해줌

그러면 여기에 user를 위한 에러 메시지도 넣을 수 있음

만약에 user가 이것을 submit하면 invalid인지 아닌지 말해줄 수 있음

그럴 경우에 input invalid같은 경고창을 띄울 수 있음

이제 설명해봄

먼저 label을 만들어봄

예를 들면 이렇게 써봄

이제 이 label을 input이 invalid 할때만 보여주고 싶음

지금 상태는 invalid함

값을 넣으면 이 input은 더 이상 invalid가 아니어야함

그러니까 이 안내문을 숨겨줘야함

이것을 하기 위해 사람들은 어떤 로직을 생각함

이런 것을 하려면 react.js가 필요하다고 생각할 거니까 state를 가지고 무엇인가 어떻게 해야함

정답은 NO임

우리에게는 peer modifier가 있음

이것은 굉장히 멋진 기능임

peer modifier는 이 input의 상태에 따라서 여기 span의 스타일을 변화시킬 수 있음

peer modifier는 이 span의 style을 바꿀 수 있게 하는데, 그 조건이 이 input의 state임

앞에서 했던 group modifier 기억나

우리는 group으로 가서 class로 group을 써줬어야 했음

그리고 item으로 가서 group이 hover일때 어쩌구저쩌구 했지

이번에는 먼저 peer를 label 해줌

이쪽으로 와서 이것이 우리의 peer라고 써줌

다음으로 여기 span에 와서 peer modifier를 사용해봄

peer라고 씀

peer에 관련된 이렇게 많은 옵션들이 있음

예를 들면 peer가 invalid일때로 해봄

그때는 text-red-500으로 함

input이 우리의 peer라서 여기에 peer라고 표시해줬음

그 다음 그 옆에 있는 item에는 peer가 invalid일때 무엇인가를 해달라고 했는데 이 물결표시를 사용했음

CSS의 멋진 기능임

peer를 받아서 이것이 invalid일때 sibling에 대해서 이 class를 실행해줌

잘 되는지 확인해봄

우리는 input의 state에 따라서 CSS를 modify하고 있음

또 말하지만 이것은 Tailwind라서 할 수 있는게 아님

그냥 Tailwind로 이용할 수 있는 멋진 API임

peer를 지정해 주고 peer invalid를 써주면 됨

많은 사람들이 이 sibling selector의 존재를 몰랐음

어떻게 사용하는지도 몰랐음

하지만 아주 쉽게 활성화 할 수 있지

아주 사용하기 쉬움

이것을 더 멋있게 만들 수 있는데 peer 앞에 와서 default로 hidden을 써줌

default값으로는 hidden이고 만약 peer가 invalid라면 그때 보이도록 설정을 해주면 됨

visible이 아니어서 적용이 안 됐나봄

block이라고 써줘야함

이것은 react.js기능처럼 보이지만 사실은 아니었음

만약에 react.js로 이것을 만들려고 했다면 if else하고 이것저것 해야했음

하지만 여기서는 input의 state만 정해주면 Tailwind가 hide를 조정해줌

여기 보면 default로는 display none이 되어있음

여기 이 peer가 invalid일 때 display block으로 바뀜

peer가 invalid일때 text color도 바뀔거고, 이번에는 다른 것을 이용해서 같은 작업을 해봄

이번에는 peer invalid 대신에 peer valid를 써봄

peer가 valid할때 text color를 teal로 바꾸고 Awesome username이라고 띄워줌

지금은 invalid하고 글자를 써보면 Awesome username으로 바꿨음

이것을 javascript도 아니고 CSS만 가지고 했음

또 말하지만 이것은 Tailwind의 기능이 아니고, CSS의 sibling selector를 아주 기깔나는 방법으로 사용했음

이 부분이 sibling을 select함

당연히 peer는 peer selector보다 앞쪽에 위치 해야함

왜냐하면 그것이 peer selector가 작동하는 방법임

peer가 제일 먼저 오고 그 다음으로 다른 것들이 와야함

만약에 앞뒤를 바꿔서 해본다면 전혀 작동하지 않지

peer가 먼저 와야함

이것은 CSS가 만들어진 방식 때문에 생기는 한계점임

input 뒤에 따라오는 follower들은 볼 수 있지만, 그 이전 순서를 볼 수는 없는데 CSS가 top to bottom으로 작동하기 때문임

반대로 갈 수는 없음

위에서 아래로만 볼 수 있음

당연히 이렇게 peer valid만 가능한 것은 아니고 다른 것들도 되겠지

지루하니까 peer valid는 그만하고 바꿔봄

우리가 가진 이 모든 옵션들을 봄

이것 말고 hover는 어떨까

이것은 amber 색상으로 함

이것도 CSS로 열심히 만든 것 같지만 아니지

classname만 가지고 이것을 다 했음

여기까지가 우리 form selector의 마지막임

우리 selector의 마지막 순서를 만나봄

그것도 꽤 멋있어서 보여주고 싶음

그 다음으로는 반응형 디자인(responsive design), 다크모드도 Tailwind CSS로 만들어봄

스포일러 하자면 다크모드는 지금 한 것만큼 간단함

## 4.8 More Modifiers

이번 비디오에서는 JS없이 구현할 수 있는 또 다른 종류의 UI패턴을 보여줄건데, 저번 영상에서 input값의 상태에 따라 label을 숨기거나 보여주거나 했던 것과 같은 방식임

JS를 사용하지 않고 CSS로만 가능했었음

이번 영상에서도 똑같음

여러분들이 많이 써보지 않았을 HTML 태그를 보여줄건데 아마 존재하는지도 몰랐음

예전에 정말로 많은 사람들이 구현했던 패턴임

그건 'details'임

HTML의 details 태그는 두 부분으로 나뉘는데, 하나는 summary 부분으로 summary 태그를 쓰는데 여기는 바로 details 태그의 제목을 쓰는 부분임

화면에서 직접 보면 좀 더 이해가 감

그럼 여기서는 무엇을 할거냐면, 내가 제일 좋아하는 음식이 무엇인지 물어봄

그럼 이것이 바로 이런 화면을 만들어 내는게 보이지

이것이 그냥 됨

클릭할 수 있는 화살표가 있고 클릭하면 움직임

이미 다 만들어져있음

자바스크립트는 필요없음

그냥 HTML과 브라우저가 동작함

그럼 이제 details 태그의 다른 부분은 뭐냐면 바로 content임

여기서는 div, span 아무거나 상관없음

span으로 함

그리고 내 최애 음식이 김치라고 해봄

그러면 여기 김치라고 적음

그럼 다 됐음

그럼 이제 김치라고 보이지

내가 클릭하면 숨고, 다시 클릭하면 보이고 숨고 보임

이것은 tailwind도 CSS도 아니고 그냥 보통의 HTML임

우리가 자주 안 쓰는 태그일뿐임

많은 사람들이 이것을 JS나 리액트로 구현할 필요가 없는데도 구현하고 있음

그럼 여기 이 화살표를 클릭하면, 텍스트가 선택되어지는데 좀 별로임

그러니까 이것을 disable 시켜봄

여기 summary 태그에다가 className에 select-none이라고 적어주면 됨

그럼 이제 여기를 클릭해도 선택 안 되는게 보이지

커서도 바꾸고 싶음

cursor:pointer로 바꿔줌

그럼 마우스를 올리면 커서가 생기지

그럼 여기도 똑같이 해줌

지금처럼 선택되는 방식은 별로임

그럼 select-none을 details 태그에도 줌

그 전에 아마 잘 모를 멋진 modifier 하나를 보여줌

selection이라는 것임

여기다가는 배경색으로 indigo 컬러를 줌

대충 500정도로 줌

600으로 함

selection은 선택되었을때의 배경색을 지정하게 해줌

나도 이 selector를 까맣게 잊고 있었음

유저가 글자를 선택했을때 색상을 변경하고 싶다면 이것을 사용하면 됨

글자 색깔을 흰색으로 바꿀 수도 있음

선택하면 글씨만 흰색이 됨

멋지긴 하지만 이런게 있다는 것은 기억만하고 지워버림

selection을 여기로 옮겨줌

그리고 open이라는 state도 있음

open일때 어떻게 할지 전부 바꿀 수 있는데 open일때 글씨를 흰색으로, 배경색은 다시 indigo로 함

그럼 open state일때만 변함

여기 [open] state 보이지

그럼 이제 잘 됨

이렇게 하면 보이고 안 보이고 보이고 안 보임

정말 하기 쉽지만 정말 쓸모 있음

그리고 JS는 전혀 필요없음

HTML로 전부 가능하고, open selector로 약간의 CSS를 수정하는 정도임

충분히 멋진 것 같음

그럼 이제 마지막으로 list를 해봄

ul 태그를 적어주고 li 태그도 적어줌

hi라는 목록을 3개 만들어줌

리스트의 모습도 바꿔볼 수 있음

className에 list-decimal이라고 해줌

list-disc라고 하면 잘 바뀜

마커의 모양도 바꿔줄 수 있음

여기 왼쪽에 있는 이 부분이 마커임

className에 marker:text-teal-500을 줘볼까

잘 바뀌지

그러면 decimal이라고 해주면 숫자들의 색깔도 잘 바뀜

그리고 이것은 Tailwind의 마법이 아님

그냥 단지 CSS 속성들일 뿐임

마우스를 위에 올려보면, 여기 속성이 보이지

거의 다 왔음

input type='file'이라고 해봄

file selector를 알려주고 싶음

보통 HTML에서 파일 선택화면은 이렇게 나옴

버튼이 여기 있고 직접 커스텀하기 좀 까다로움

그 대신 이번에는 file modifier를 사용해봄

우선 className에 file:border-0부터 넣어봄

그럼 이제 테두리가 사라졌음

한가지를 더 해봄

className에 file:rounded-md를 추가해봄

내가 왜 file modifier를 사용했는지 궁금함

그 이유는 우리가 이 버튼을 바꿀거라서 그런건데 뭐가 다른지 보여줌

file:bg-purple-400을 주면 여기 버튼색만 변경되는게 보이지

하지만 file:selector가 없으면 전체 input을 변경함

서로 다른 개체, 다른 selector임

꽤 멋진 것 같음

여기 있는 selector를 봄

CSS에 존재하는지 몰랐겠지만, 실제로 존재함

이것이 바로 Tailwind CSS의 좋은 점인데, CSS 사양들을 잘 따라가고 있음

계속 추가하고 있고 우리는 그냥 className으로 사용하면 됨

CSS selector를 검색해서 자세한 사양을 볼 필요가 없음

Tailwind CSS에 클래스명으로 들어가 있다는 것은 이게 작동한다는거니까(믿고쓰는 Tailwind!), Tailwind에서 전부 테스트해보고 작동하는지 확인했기 때문에 그냥 쓰기만 하면 됨

정말 최고임

이것이 존재하는지도 몰랐겠지만 이제 알게 됐음

file-selector-button 속성이었음

그럼 rounded를 좀 크게 해봄

padding은 file:p-1로 해볼까(변경됨)

px-5가 좋겠음

그리고 file:text-white도 줌

그리고 이제 내가 엄청 멋지다고 생각하는 것을 보여줄건데, 그것은 바로 여러 modifier들을 중첩시킬 수 있음

지금 현재 내가 원하는 것은 마우스를 여기 Choose File 버튼 위에 올리면 버튼을 변경하고 싶음

그걸 위해서는 hover selector가 필요하겠지

그럼 한번 해봄

우선 색깔을 transition 해줌

그럼 이제 커서를 포인터로 바꿈

그리고 tailwind CSS에서 커서는 정말 다루기 쉬움

cursor-pointer를 쓰면 됨

여기서는 file selector를 추가하고, transition에도 file selector를 추가함

그럼 보다시피 커서가 변하고 있지

그리고 또 커서에 재밌는 옵션들이 많음

다양한 종류의 커서들이 있음

사용하기 매우 쉬움

예를 들어 나는 cursor-wait가 제일 좋음

이러면 너의 브라우저와 컴퓨터에 따라 다르게 로딩화면을 보여줌

엄청 멋진 것 같음

여기서는 curser-pointer라고 적어주고, 이제 파일이 hover 상태일때의 색상을 바꿔봄

마우스가 hover일때 파일 버튼의 배경색과 글자 크기, 글자 색상을 바꿔봄

그럼 우선 file: 이라고 적고 여기에 modifier를 하나 더 추가함

바로 hover임

드디어 text를 바꿀 수 있음

배경이랑 같이 purple-400으로 함

그리고 file:hover:를 한번 더 함

그리고 이번엔 border를 줌

보다시피 file:hover:text 같이 많은 selector들을 한번에 사용하고 있음

그럼 이것이 이런 클래스네임을 만들어냄

file:hover:text에다가 :hover::file selector가 붙어있음

내가 말했듯이 TailwindCSS는 일종의 거대한 CSS파일임

거의 모든 종류의 클래스네임들을 찾을 수 있음

이것이 그 중 하나임

file:hover:text-purple-400:hover::file-selector-button이라는 클래스네임이 실제로 있음

그럼 이것을 저장하고 이제 잘 작동함

어쨌든 잘 되고 있음

여기까지 file selector였음

file selector를 배웠고, 이제 selector 여러개를 같이 쓸 수 있다는 것을 알았음

file에 hover를 같이 쓸 수 있음

다크모드를 사용할 때는 darkmode:file:hover:text-purlple처럼 더 좋음

그럼 다크모드일때 파일 버튼에 커서를 올렸을때만 적용됨

그럼 이것을 지우고 내가 보여주고 싶은 멋있는 몇가지만 더 보여줌

그럼 우리는 이 부분은 끝을 봄

lorem ipsum 어쩌구 저쩌구 적어주고, 어떻게 하는지 까먹었음

이것으로 됐고 여기에 first-letter라고 적어줄텐데, 아주 귀여운 modifier라고 생각함

우선 className이라고 적고, 멋진 first-letter selector를 적어줌

그리고 글자크기를 아주 크게 text-2xl로 해줌

더 크게 해줘야 할 것 같음

7xl이라고 해줌

잘 됨

이것은 first-letter라는 실제 CSS selector임

내가 볼 때는 엄청 멋진 것 같음

이것으로 글자를 바꿀 수 있음

예를 들어 Hello Everybody라고 치면 그 다음  first-letter라고 하고 :hover selector를 더해주면, 보다시피 selector를 중첩하고 있음

한번에 묶어주고 있음

그 다음 text-purple-400이라고 해줌

잘 되지

첫 글자만 바뀜

그리고 또 first-line이라는 selector도 있음

이렇게 하면 first-line을 선택할 수 있음

내가 여러분에게 보여주고 싶었던 모든 selector를 보여준 것 같음

물론 다른 selector들도 있지만 예시를 보여주기 힘들거나 별로 실용적이지 않은 것들임

이쯤이면 다 한 것 같음

file selector를 보여주고 싶었고 first-letter select를 보여줬고, 그것들을 한번에 묶는 방법도 봤음

그럼 이제 우리의 예전 디자인으로 돌아가볼건데, 왜냐하면 이제 반응형 디자인에 대해 얘기해봄

모바일 화면을 어떻게 하는지부터 본 다음에 우리 앱을 수정해봄

점점 큰 화면에 적용해볼 수 있도록, 그리고 지금 배운 modifier들을 어떻게 적용시키는지 얼마나 쉽게 할 수 있는지도 알려줌

modifier들은 다 배워봤음

## 4.9 Responsive Modifiers

이 비디오에서는 Tailwind CSS에서의 반응형 디자인에 대한 얘기를 시작해봄

얼마나 쉽게 반응형 디자인을 만들 수 있는지 알게 됨

우선 첫번째로 우리가 해야할 것은 반응형 디자인에 대한 우리의 생각 또는 웹이나 어플을 만드는 방식을 뒤집어보는 것임

그 이유는 사람들이 웹사이트를 만들때 Desktop 버전부터 생각하기 때문임

보통은 먼저 Desktop 버전부터 생각한 다음 그것을 모바일 버전에 적용시킴

처음 CSS를 작성할때는 Desktop에 맞춰서 작성한 다음에 모바일 버전에 맞춰 그것을 변경함

우리는 이제 그것을 뒤집어봄

사실은 Tailwind CSS가 그것을 애초부터 뒤집었음

여기 작성한 클래스랑 모든 것들이 모바일에 우선 적용됨

전부 모바일에 먼저 적용됨

그러고나서 큰 화면을 위해 디자인을 변경함

마치 매트릭스처럼 뒤집음

모두가 우선 Desktop 버전을 디자인하고, 그 다음에 모바일 버전에 적용시킴

Tailwind CSS를 사용할때는 우리는 따로 모바일 화면을 위한 선택자를 가지지 않음

모든 클래스네임이 모바일에 우선 적용되고, 그 다음에 보다 큰 화면들을 위한 선택자가 있음

그래서 이번 강의와 다음 강의에서 하게 될 것은 우리 디자인을 화면 사이즈에 맞게 수정하는 것임

예를 들어 여기를 보면 무척이나 못 생겼음

왜냐하면 내가 일부러 한건데, 우리는 모바일 버전으로 시작했음

모바일 버전에서는 모든게 예뻐 보였지만 여기서는 별로지

보다 큰 화면에 있을 때는 지금 보이는 것처럼 하나 밑에 하나 있는 방식 말고 열이 옆쪽으로 3개정도 있었으면 좋겠음

위아래로 정렬된 디자인 말고 좌우로 정렬된 디자인을 원함

그것이 우리의 첫번째 코드가 됨

여러 다른 CSS modifier들을 살펴봄

여기에 sm, md, lg, xl, 2xl 등등 우리가 살펴볼 것들이 있음

이것들이 반응형 디자인을 위한 modifier들임

한번 봄

sm부터 시작함

그럼 이제 무엇을 할거냐면 여기로 와서 첫번째 요소의 클래스네임을 보고 배경을 위한 modifier를 추가해볼건데 sm:이라고 적고 bg-red라고 해줌

왜 내가 계속 빨간색을 고르는지 모르겠지만 bg-red-400이라고 함

그럼 보다시피 아무것도 변경이 안 되고 있음

그러니까 제대로 작동하고 있고, 마우스를 올리면 미디어 쿼리가 보이지(@media)

우리에게 아주 좋은 소식임

보다시피 잘 작동중이고 그럼 이것을 크게 만들어봄

우리가 작은 화면에 맞게 적용시켜봄

이제 이것을 더 크게 해보면 어떻게 될지 궁금함

다시 배경이 하얀색이 될까

다시 돌아가지 않음

그 이유는 가장 최근의 설정들이 적용되기 때문임

첫번째 설정은 모바일에서의 하얀색 배경임

그 다음에 작은 화면에서 혹은 그 이상일 때는 bg-red-400이 적용됨

그러니까 작은 화면들뿐만 아니라 그 이상에 대해서도 적용이 됨

그래서 이런 것도 가능한데 작은 화면의 스타일을 아주 큰 화면까지 쭉 적용시킴

그것도 괜찮음

하지만 내가 보여주고 싶은 또 다른 modifier인데 그것은 바로 md임

md:bg-teal-400를 넣어봄

그리고 한번 봄

모바일 우선이기 때문에 여기서 배경은 흰색이고, 그 다음은 작은 화면으로 바꿈

잘 됨

작은 화면은 보다시피 매우 폭이 좁음

여기서 여기까지 밖에 안 됨

여기서부터는 이제 중간 크기 화면이 되고 계속해서 해봄

그럼 md를 사용했고 이제 lg modifier를 해봄

lg:bg-indigo-400를 줌

그럼 어떻게 작동하는지 보면 모바일 화면에서는 먼저 이렇게 그 다음 sm, md, lg 모두 잘 됨

그럼 lg 다음에는 xl을 해줌

bg는 무엇으로 해볼까

teal은 이미 줬고 색깔 이름을 잘 모르겠음

yellow-400으로 함

되는지 봄

그리고 2xl도 있는데 이것이 가능한 가장 큰 화면임

2xl:를 적어주고 그 다음에는 핑크색으로 함

잘 됨

이제 우리는 큰 화면도 다루고 있음

보다시피 보게 될 화면은 다음 선택자에 의해서 결정됨

내 말의 의미는 sm: 선택자를 지정하면, 이것이 작은 화면에서만 적용되는게 아님

이 말의 뜻은 sm크기의 화면에서부터 배경색을 red-400으로 해달라는 것임

예를 들어서 여기 써준 이 선택자들이 없다면 여기 있는 것을 전부 지워봄

그럼 sm 화면에서부터라는 조건이 참이 돼서 배경색이 빨간색이 됨

sm 크기의 화면에서 '부터' 작동함

sm크기부터 무한대까지 작동함

빨간 배경색이 됨

그 이후의 단계들은 직접 조정함

작은 화면에서 빨강색이었다가 md 크기에서는 초록색, lg 크기에선 파란색임

이것이 Tailwind CSS에서의 반응형 디자인과 반응형 modifier의 기초임

사고를 뒤집어야함

처음에는 모든 클래스네임들이 디폴트로 모바일에 적용됨

그 다음 큰 화면에 적용함

큰 화면에서 시작해서 모바일로 내려가면서 적용하는게 아님

그럼 여기까지가 기초 소개였음

모바일에서 시작해서 점점 큰화면으로 적용함

큰 화면에서 시작해서 모바일에 적용시키는게 아님

모바일만을 타겟으로 하는 클래스네임은 없음

또 하나 기억해야할 것은 반응형 modifier들은 그 다음 modifier들에 의해 정지돼야함

그러니까 md 선택자를 정의하지 않으면 sm 선택자의 화면이 lg 선택자까지 나옴

그럼 여기서 다시 md 선택자를 지워봄

이렇게 md 선택자가 없으면, sm 화면이 lg 화면까지 쭉 다 나옴

선택자들의 시작점은 있지만 끝점은 정의되어 있지 않음(무한까지)

sm 선택자 뒤에 다른 선택자를 써놓지 않으면, 화면이 xl 크기가 될 때까지 쭉 적용됨

그럼 다시 해봄

여기 우리의 sm 선택자 화면이 더 큰 화면에서도 나오지

그 다음 xl 크기가 되면 sm 선택자 화면에 나오지 않음

여기도 똑같이 지워주면 이번에는 sm 화면이 더 큰 화면에까지 쭉 나옴

나는 이런 방식으로 사고하는 것을 좋아함

상한선이 정해져 있지 않음

단지 최소 너비만 줌

sm 화면을 위한 최대 너비(max-width)는 존재하지 않음

먼저 모바일에 적용되는 무엇인가를 작성하고나서 작은 화면부터 매우 큰 화면까지 적용되는 무엇인가를 추가할 수 있음

진짜 좋은 것 같음

큰 화면에서 작은화면으로 내려가는 것보다 더 좋은 방법임

그렇게 하면 큰 화면부터 중간 화면 순서로 작성할거고, 결국 모바일에는 적용이 안 됨

Tailwind CSS의 방식대로 하게 되면 모바일 화면에서 시작해서 상한선 없이 큰 화면에 적용시키게 됨

이것이 내가 좋아하는 부분임

우리가 전에 했던 상태로 돌려놓고 다음 영상에서 봄

sm, md, lg 사용하기 정말 쉽지

그리고 지난 시간에 봤던대로 서로 중첩시켜서 사용할 수도 있음

예를 들어 sm:hover:bg-pink처럼 쓸 수도 있음

sm에서 마우스를 올리면 이제 스크린이 sm사이즈일때만 마우스를 올리면 작동하는 조건을 가짐

미디어 쿼리 조건과 hover 선택자를 합쳐서 이런 CSS 효과를 가져옴

## 4.10 Responsive Modifiers part Two

이번 영상에서는 우리 화면을 수정해서 큰 화면에서 더 멋져보일 수 있게 바꿔봄

그럼 우선 여기 이 화면보다 큰 화면을 타겟으로 시작해봄

여기에는 행 세개 말고 세개의 열(column)이 있었으면 좋겠음

이것은 큰 화면에 속하니까, 우리가 할 것은 큰 화면일 때 grid에 열 세개를 더 추가하는 것임

여기 보다시피 grid 속성을 사용했고 grid-gap을 주고 있기 때문에 일반적으로 CSS에서 grid를 사용하면 모든 것이 다 행(row)이 되버림

열(column)이 되지 않음

그러면 이제 Tailwind CSS에서 grid에 열(column)을 만드는게 얼마나 쉬운지 보여줌

그냥 grid-columns라고 적고 열 갯수를 적으면 끝임

엄청나게 편함

3개로 함

이때 모바일에 먼저 적용된다는 것을 잊지마

그것은 내가 원하는게 아니니까 lg 사이즈 화면에만 적용해줌

잘 적용됐지

큰 화면부터 그 이상까지 grid column 3개가 있음

이 부분은 별로 좋아보이지가 않음

그럼 lg말고 xl부터 변해야겠음

그럼 xl사이즈부터 모든 것이 잘 변함

여기 lg 사이즈 화면에서는 열을 2개만 가지고 싶음

그러니까 lg:grid-cols-2라고 해줌

그럼 열 2개가 생겼음

이번에는 이 마지막 열이 끝부분에서 열 2개 크기를 차지하도록 해봄

그럼 마지막 열로 가봄

여기 있는 이 마지막 div임

그리고 column span이라는 속성을 사용해줌

이것은 grid에 존재하는 속성임

이번에도 그렇지만 Tailwind의 마법이 아님

그러면 열 2개 자리를 차지한다고 해줄거고(col-span-2), 그럼 이렇게 보이지만 화면 크기가 lg일때만 이렇게 보여야함

화면 크기가 lg일때만, 마지막 칸이 열 2개 자리를 차지함

모바일에서는 칸 1개 자리를 차지함

이렇게 늘려보면 잘 바뀜

그럼 이제 보다시피 화면을 더 키워도 여전히 자리를 2개만큼 차지하고 있음

왜 계속해서 자리 2개를 차지하는걸까

왜냐하면 내가 lg라고 적었음

내가 전에 말했듯이 lg 선택자를 막아줄 xl이나 2xl 선택자가 없음

다시 잘 떠올려봄

우리는 모바일 크기에서부터 큰 화면으로 적용시키고 있음

거기에는 상한이 없음

lg는 여기서 단지 최소 너비로 작동할뿐임

그러니까 xl 사이즈가 될때 lg 속성을 막아줘야함

xl 사이즈일때 우리는 col-span을 다시 1로 만들고 싶음

다시 해보면 당연히 모바일에서는 column span이 1이겠지

그리고 다시 화면을 키우면 column-span이 2개가 됐음

그리고 xl에서 lg의 속성을 취소시켜줌

우리가 여기서 속성들을 서로 취소시키고 있다는 것을 잘 이해했으면 좋겠음

lg 다음에 xl을 이렇게 취소시킴

우리가 이 xl을 쓰지 않는다면, column-span이 lg 크기부터 그 이상까지 쭉 적용됨

그것은 우리가 원하는게 아님

작은 화면에서는 2개였다가 화면을 키우면 3개가 되고 있음

아주 잘 작동하고 있음

물론 아직 그다지 예뻐 보이지는 않음

여기 xl 화면에서 보면 이렇게 길어보이는게 좀 별로임

보다시피 너무 긺

그럼 그 대신에 이것들을 가운데 위치시켜볼 수 있음

이것은 media query가 필요없을 것 같고, 그냥 place-items를 해줌

이것은 Tailwind에 있는 기능이 아니라 훌륭한 grid의 속성임

그리고 내 생각에는 아주 잘 작동하는 것 같음

하지만 보다시피 다른 것들이 전부 좀 이상하게 보임

모바일에서는 이 속성이 별로 좋아보이지 않음

화면을 키우면 여기서는 괜찮아 보이고, 더 키우면(xl) 여기서는 꼭 필요함

그 말은 이 속성에 xl 선택자를 붙이면 된다는 소리임

그럼 끝임

그럼 이제 모든 화면 크기에서 전부 괜찮아보임

잘 작동함

물론 아직 이것도 좀 별로임

하지만 보다시피 더 큰 화면에 적용시켜 나가는 좋은 과정이었음

우리가 다 적용시킴

lg의 속성을 취소하려면 xl 속성이 있어야 한다는 것을 기억함

그리고 속성을 추가하고 화면 크기를 조절해가며 확인했을때, 작은 화면에서 잘 작동하지 않으면 속성에다가 xl 선택자를 추가해주면 됨

그럼 잘 동작하는 것을 볼 수 있음

그럼 이제 아까 못생겼다고한 두 녀석들을 처리해봄

왼쪽부터 먼저 해줌

다시 코드를 펼치고 여기서 하려는 것은 기본적으로 전부 다 flex로 만들어버리고 싶음

그리고 여기 있는 것들 전부 크기를 골고루 나눠줘야함

그럼 이제 모바일에서 먼저 테스트 해봄

내가 여기다가 flex를 주면 어떻게 될까

그리고 flex-column이랑 justify-between도 줘봄

어떻게 되지

아무 일도 안 생김

그럼 이제 이 스타일은 추가해도 괜찮고, 이 이상의 크기까지 쭉 적용될거라는 얘기임

이것이 별로 안 좋아보인다는 것은 알지만 이것이 최선임

이 정도면 괜찮은 것 같음

그럼 이 두번째 칸은 어떻게 해야할까

보다시피 padding-bottom이 너무 작음

좀 더 키워야할 것 같음

그럼 다시 모바일에서 보면 여기 이 파란 프로필은 괜찮아 보이니까 패딩을 수정할 필요는 없음

더 큰 화면에서도 볼 때는 괜찮고, 이제 이 화면에서가 문제임

여기는 xl 화면이니까 xl을 선택하고 padding bottom을 넉넉히 60쯤 줌

64로 함

너무 큼

하지만 바꿨음

이것이 바로 내가 반응형 디자인을 할때 생각하는 방식임

내가 따르고 있는 과정임

우선 모바일을 먼저 한 다음, 거기서 확장시켜나가면서 어떤 것을 변화시켜야하는지 봄

만약에 모든 화면 크기에서 잘 작동하는 속성이 있다면 여기 flex-column justify-between처럼 이렇게 그냥 넣음

모바일에서도 큰 화면에서도 잘 작동함

일종의 반응형 디자인을 가지게 됐음

그리고 단 한줄의 CSS 코드도 필요 없었음

내가 볼 때는 Tailwind CSS에서 반응형 디자인을 할 수 있는 이 방법이 너무 멋진 것 같음

왜냐하면 사람들은 보통 반응형 디자인한테 고통받음

왜냐하면 우선 이런 수치들을 기억해야하고 그런 것은 전혀 재밌지가 않음

예를 들어 lg나 xl의 정확한 수치를 기억해야하는건데 별로 좋아하지 않음

다들 이 문법을 종종 까먹음

그냥 클래스명을 읽고 뭐가 일어날지를 아는게 훨씬 더 쉬워보임

이것을 읽으면 lg 화면에서 col이 자리를 2개 차지할 거라는 것을, 그리고 매우 큰 화면에서는 1개 차지할 거라는 것을 알 수 있음

내 생각에는 이것이 알기 매우 쉬운 것 같음

그리고 그것이 끝이 아님

이제 알려주려는 것은 또 다른 일종의 미디어 쿼리임

그리고 이번에는 디바이스의 방향에 관한 것임

지금 보여줄만한 좋은 예시는 없지만, 일단 여기 있는 파란 프로필 배경화면의 색상을 현재 디바이스의 방향이 가로인지 세로인지에 따라 바꿔봄

그럼 개발자 도구에서 장치 시뮬레이터를 열어봄

아이폰을 선택하고 이것을 돌려봄

우리가 화면을 이렇게 보고 있다면, 배경 색상을 노란색으로 바꾸고 싶음

다시 방향을 바꾸면 색상이 초록색이나 뭐 그런 것으로 바뀜

그럼 무엇을 할거냐면 이렇게 landscape라고 선택해줌

엄청 쉽지

그리고 bg-teal-500이라고 해줌

그럼 됐음

이것이 landscape였음

테스트 해봄

잘 됨

엄청나게 간단하지 않아

단어에 커서를 올려서 속성을 한번 보면 @media (orientation:landscape)임

그러면 portrait에도 똑같이 해줌

bg-indigo-600이라고 해줌

그럼 이제 다 됐음

파란색은 지워주고 여기에서 보면 잘 됨

다 됐음

portrait하고 landscape를 배워봤음

이제 dark mode를 해볼 차례임

## 4.11 Dark Mode

그럼 이제 할건 뭐냐면, 다크 모드를 한번 들여다봄

그리고 다크 모드는 Tailwind CSS에서 만들기 엄청 쉬움

약간의 차이가 있다면 다크모드를 어떻게 활성화시킬지에 따라 고를 수 있는 설정 옵션들이 몇개 있음

기본값으로 다크 모드는 컴퓨터의 환경 설정에 따라 활성화하게 되어있음

그러니까 유저가 PC나 모바일을 다크 모드로 설정해놨다면 브라우저도 다크 모드가 됨

그것이 기본값임

내 경우에는 컴퓨터의 기본값이 다크모드로 설정되어있음

그러니까 다크 모드 선택자들을 여기에 적으면 반영되는 것이 바로 보임

나중에 어떻게 바꿀 수 있는지 봄

다크 모드를 하기 위해 해야하는 것은 dark 선택자를 적어주는게 전부임

dark 선택자를 적고 그 뒤에 원하는 것을 아무거나 적음

예를 들어 여기 bg-white니까 다크모드일 때는 bg-black을 해줌

보다시피 바꾸자마자 반영이 됨

브라우저의 기본값이 다크모드이기 때문임

그럼 우선 모든 것을 다크모드 색상으로 바꿔봄

예를 들어 여기 select Item태그도 다크모드에서는 text-white로 바꿔봄

회색 의자의 가격들은 다크모드일때 text-gray-50으로 해봄

그리고 여기 이 가격들도 똑같이 해줌

다크모드 일때 둘 다 똑같이 됨

잘 됨

무척 간단함

50을 100으로 변경해줌

그게 더 나을 것 같음

이것도 100으로 바꾸고 나쁘지 않음

그럼 다 됐음

이것이 다크 모드임

무척이나 간단함

컬러도 바꿔줄 수 있음

그럼 버튼 색상을 바꿔봄

다크모드에서는 bg-black으로 해봄

그리고 border 색상은 흰색으로 함

그리고 또 dark: 선택자를 적고, border 1px를 줄거니까 그냥 border라고만 적음

이렇게 border라고만 적으면 border 1px를 주게 되있음

그럼 이제 쿼리를 한번 봄

미디어 쿼리가 있고 prefer-color-scheme: dark라고 되어 있지

이것은 CSS 속성인데, CSS가 다크모드인지 아닌지를 알게 해줌

저장하면 보다시피 이제 이것이 내 버튼임

그리고 내가 말했던 것처럼 여러 modifier를 중첩시킬 수 있음

예를 들어 다크모드에서는 hover일때 이 초록색을 적용하고 싶지 않음

그럼 그냥 hover라고 하는 대신에 앞에 dark:를 추가해서 중첩해봄(나중에 고침)

dark:hover가 아니고 dark:hover:bg-black임

왜냐하면 라이트 모드의 속성을 막아야 하기 때문임

그냥 hover는 라이트 모드용이고, dark:hover는 다크 모드용임

다른 선택자를 취소해야함

그럼 이제 저장해보면 잘 됨

마우스를 올려도 배경이 변하지 않지

여기에 있는 hover:text-black도 막아버려야함

그럼 dark:hover:text-white라고 해줌

그럼 다 끝났음

여기서 원한다면 살짝 수정해서 더 나아지게 할 수도 있음

여기를 다시 원래대로 dark:hover:text-black으로 함

그냥 지워주면 됨

dark:bg-white로 바꿔줌

그럼 이렇게 됨

이것이 우리의 다크 모드 카드임

그리고 이것이 지금 활성화 되어있는 이유는 Tailwind CSS의 다크모드 쿼리가 기본값으로 브라우저의 설정을 따라가기 때문임

여기에 모드를 바꿀 수 있는 Mac OS 메뉴가 있는데, 여기서 모드를 변경하면 이것이 어떻게 바뀌는지 볼 수 있음

그냥 자동으로 작동함

다시 한번 이것은 브라우저의 설정을 따라가기 때문에 일어남

그런데 가끔씩 어떤 웹사이트들은 다크모드를 선택할 수 있는 어떤 아이콘들을 가지고 있는데 이 사이트들은 브라우저 설정을 따라가지 않음

모드를 수동으로 바꿀 수 있는 아이콘들을 가지고 있음

직접 전환할 수 있음

Tailwind는 그 기능이 제공됨

하지만 그 기능을 사용하려면 우선 tailwind.config.js로 가서, 컴퓨터의 다크모드 설정을 따라갈건지 아니면 리액트나 JS로 직접 토글시킬 것인지를 설정해줘야함

어떤 웹사이트들은 직접 클릭해서 원하는 모드를 보여줄 수 있는 버튼 같은 것을 가지고 있고, 어떤 사이트들은 그냥 기본 설정 그대로 보여줌

그래서 이것을 설정하려면 여기에 darkMode라고 씀

기본값으로 darkMode 설정은 이렇게 'media'로 설정 되어있음

설정이 media로 되어있으면 다크모드 설정은 환경설정을 따라감

하지만 이것을 'class'로 바꾸면 매우 달라짐

class로 바꾸는 순간 브라우저와 컴퓨터가 다크모드임에도 불구하고, 다크모드가 활성화되지 않고 있음

그럼 다시 코드 파일로 돌아가서, dark모드 선택자에 커서를 올려보면 설정이 바뀌어있음

Tailwind가 어썸하기 때문임

vscode의 Tailwind 플러그인이 tailwind.config.js의 설정을 따라감

이제 속성을 살펴보면 media query가 없어졌음

media로 변경하고 다시 속성을 살펴보면, 환경설정이 다크모드로 되어있는 경우를 위한 미디어 쿼리가 생겼음

이것을 class로 바꾸면 보다시피 화면이 바뀜

그리고 그게 바로 여기 이 변경된 속성임

그럼 이게 무엇을 말하는걸까

만약 수동으로 다크모드를 활성화한다면, 다크모드 선택자가 하는 것은 보다시피 단지 부모 요소 중에서 다크모드(.dark)를 찾는 것뿐임

그게 전부임

dark라는 클래스네임을 어떤 요소의 부모에 넣는다면, 예를 들어 이 버튼의 부모에 넣으면 이 버튼에 한해 다크모드를 수동으로 활성화할 수 있음

그럼 이번에는 모든 요소의 부모에 dark 클래스네임을 넣어봄

이 칸 세개의 부모 요소에 dark 클래스네임을 넣어줌

그럼 보다시피 넣자마자 자식 요소들의 다크모드가 활성화되지

이것이 수동으로 하는 방식임

그 말은 예를 들어 우리가 네비게이션 바의 어디인가에 버튼을 만들고, 유저가 버튼을 클릭하면 html 태그에 dark 클래스를 추가할거라고 함

이렇게 html을 변경하면 모든 요소들이 다크모드를 따라가게 됨(모든 요소의 부모 태그라서)

기존 방법이랑은 다른 전략임

솔직히 좋아하지는 않음

게을러서 직접 태그를 수정하는게 귀찮음

하지만 다크모드를 토글할 버튼을 원한다면 해볼 수 있음

복습해보자면 첫번째 방식은 기본 설정인 'media'임

media 방식을 사용하면 브라우저의 설정을 따라가게 됨

마우스를 여기 올려보면 dark mode 미디어 쿼리를 사용하는 것을 볼 수 있음

이것이 가장 좋아하는 방법이지만, 만약에 브라우저 설정과 상관없이 모드를 토글하고 싶다면 tailwind.config.js의 darkMode 설정을 'class'로 바꿔줘야함

'class' 방식에서 다크모드를 활성화하기 위해 필요한 조건은 단지 dark: 선택자를 쓰는 요소의 부모요소에 dark 클래스네임을 추가하는 것뿐임

다시 한번 만약 class 방식으로 다크모드를 사용하려 한다면, dark 클래스네임을 dark modifier를 쓰는 요소의 부모요소에 넣어야함

그래서 보통은 html의 body 태그나 html 태그에 dark 클래스네임을 추가함

넣을 수 있는 가장 상위 요소에 넣음

리액트로 버튼 같은 것을 만들어서 코드로 state를 변경하고, document의 root(가장 상위) component에 dark 클래스네임을 변경함

우리가 NextJS를 사용하고 있기 때문에 여기 Component 태그에 넣어볼 수도 있음

여기서 Component 태그를 감싸는 div에 모든 페이지들을 감싸도록 className='dark'를 넣음

아주 쉽게 할 수 있는 방법임

개인적으로는 그냥 유저 브라우저의 환경설정을 따라가는 것을 좋아함

darkMode:class랑 darkMode:media이 끝임

내가 제일 좋아하는 것은 media임

클래스네임을 외울 필요도 없이 바로 작동함

그리고 매우 멋져보이기도 함

컴퓨터의 다크모드 설정을 바꿔서 빨리 테스트 해보면 아주 잘 작동함

그럼 이제 다 끝났음

깃허브에서 볼 수 있게 주석을 달아놓음

다음 영상에서 볼건데 거짓말한 것이 있음

거짓말을 했지만 미안하지는 않음

## 4.12 Just In Time Compiler

이번 비디오에서는 정확히 어떻게 TailwindCSS가 동작하는지 알려주려고 함

지금까지는 뭐라고 했냐면, tailwindCSS를 아주 커다란 CSS 파일로 생각할 수 있다고 했었음

지금껏 보아왔듯이 클래스명을 아주 많이, 거의 무한대로 가질 수 있음

다크모드, hover, 미디어 쿼리 같은 여러가지 selector들을 중첩할 수도 있었음

그러고보니 지난 영상에서 하지 않았었음

원한다면 다크모드, 스크린 사이즈, 그리고 hover 같은 것들을 같이 쓸 수도 있음

나의 선택임

요점만 말하자면 이렇게 선택자를 중첩해서 사용하는 것이 이전 버전의 TailwindCSS에서는 불가능했음

왜냐하면 이전에는 Tailwind CSS가 실제로 아주 많은 클래스 명이 있는 매우 큰 CSS 파일이었기 때문임

하지만 이렇게는 선택자들을 중첩해서 쓸 수 없었음

왜냐하면 잘 생각해보면 우리가 이전 세션에서 한 것처럼 많은 선택자들을 중첩하면, 조합의 수가 매우 많아져서 CSS 파일 크기가 너무 커지기 때문임

예를 들어서 이런 코드가 실제 CSS파일에 있었다고 생각해봄

어떤 이유에서인지 sm:hover 같은 것을 하고, 거기에다가 그 전에는 dark mode도 중첩되어 있었다고 해봄

그리고 속성으로는 bg-red를 가지고 있었다고 함

그 말은 이런 모든 것을 가진 클래스명이 실제로 있다는 뜻임

그리고 여기에 각각의 색깔마다 100부터 950까지 9가지 단계의 색상이 또 있음

그러니까 10가지 정도의 색상임

그럼 이런 클래스명이 모든 색깔에 대해서 전부 있다고 생각해봄

얼마나 많아지겠어

CSS파일의 크기가 엄청 커짐

그리고 다시 말하지만 이전 버전에서는 이것이 불가능했음

Tailwind CSS 3.0 이전 버전에서는 불가능했음

이것은 Tailwind CSS 3.0의 어떤 요소 때문에 그런건데 바로 Just-In-Time 컴파일러임

그러니까 그 전에는 Tailwind CSS가 진짜로 하나의 커다란 CSS 파일이었음

그리고 웹사이트를 배포하기 전에 한가지 할 일이 더 있었는데 바로 파일을 청소하는 거였음

그러니까 이전에는 우리가 웹사이트 배포를 위해 프로젝트를 빌드할때, 모든 파일들의 코드를 스캔해서 CSS 파일에 포함된 클래스명을 제외하고 나머지 사용하지 않는 클래스들을 전부 삭제했음

그 과정은 purging이라고 불림

그런 식으로 했었음

테일윈드 버전 3.0 이전에 있었던 일임

매우 큰 CSS 파일이 있었음

그 안에 있는 모든 클래스명들을 전부 사용하는 것은 아니기 때문에 사이트를 배포하기 전에 파일 크기를 줄이기 위해, 우리의 파일을 모두 스캔해서 사용하는 클래스명을 제외하고 전부 삭제하는 purging 프로세스가 필요했음

하지만 이것 때문에 지금처럼 선택자들을 다른 선택자들의 위에 계속해서 쌓을 수 있는 기능은 가지질 못했음

이것이 과거에는 가능하지 않았지만, 지금은 가능한 이유는 Just-In-Time 컴파일러라는 것 때문임(JIT)

JIT 컴파일러라는 것은 코드를 실시간으로 감시하면서 필요한 클래스를 생성하는 기능을 함

그럼 JIT 컴파일러가 어떻게 동작하는지 보여줌

우선 개발자 도구를 열어서 여기 있는 Tailwind에 의해 생성된 CSS 코드를 한번 봄

여기를 보면 reset css들이 많이 보임

html이나 body, hr 같은 reset css들임

이것들은 전부 테일윈드 CSS의 reset 속성들임

그리고 이것들이 여기 있는 이유는 우리가 global 파일에 이 코드를 넣었기 때문임

그것이 바로 얘네들을 global 파일에 넣는 이유임

그럼 이제 이유를 알았고, 다시 개발자 도구로 돌아와서 더 아래로 내려가보면 이제 우리가 CSS 상에서 사용하는 클래스명들을 생성하고 있음

우리가 실제로 사용하고 있는 클래스명들만 생성함

예를 들어서 -top-16을 사용하고 있기 때문에 여기서 볼 수가 있는 거고, 그리고 bg-zinc 클래스를 사용하기 때문에 여기에 보임

보여주고 싶은 것은 바로 코드를 수정하게 되면, 클래스명들이 생성되고 삭제되는 것을 실제로 볼 수가 있음

그럼 여기 css코드들을 전부 지워봄

전부 다 지웠음

현재 내 코드는 한 줄도 없는 상태임

서버를 껐다가 재시작 해봄

그리고 새로고침 한 뒤에 보면, html의 스타일 태그에 reset 코드들만 보임

reset 코드들 말고는 없음

그럼 이제 여기에 클래스를 하나 만들어봄

그럼 상당히 이상한 클래스명을 한번 만들어봄

dark:md:hover: 상태일때 배경색을 teal-400으로 함

이것을 저장하면 이제 보다시피 나를 위해 자동으로 클래스가 생성됐음

엄청 신기하지 않아

이것이 바로 JIT 컴파일러임

내가 클래스명을 새로 생성하면, 컴파일러가 그것을 찾아낸 다음 내가 원하는 클래스를 생성해줌

다시 말하지만 예전에는 이런 컴파일러가 없었기 때문에 이런 것이 불가능했음

예전에는 커다란 하나의 CSS 파일이 있어서 빌드 후에 '청소' 해야했음

이제 우리는 시작할 때 작은 파일이 있고, 우리가 무엇인가를 작성하면 거기에 추가됨

이렇게 간단하게 필요한 코드가 생성됐음

바로 테일윈드 CSS의 마법이고, 내가 이 수업에서 테일윈드 CSS를 사용하기로 한 이유임

처음으로 버전 3.0을 봤을 때, 모두 이것은 알아야해! 라고 생각했음

클래스명 1개를 쓰면 컴파일러에 의해 바로 이렇게 생성됨

이게 바로 생산성이라는 것임

그리고 이것이 바로 내가 이걸 가볍다고 하는 이유임

왜냐하면 예전의 테일윈드 2.0때처럼 큰 하나의 파일이 있는게 아님

우리는 하나의 큰 파일이 있었고, 그것은 이런 선택자 중첩을 사용할 수 없었기 때문에 좀 별로였음

이제는 선택자를 겹쳐서 쓸 수 있음

왜냐하면 이 모든 클래스들이 필요에 따라 생성됨

하지만 여전히 가장 좋은 부분이 남아있음

테일윈드 CSS의 가장 좋은 점은 전에 말했던 적이 있었는데, 여기 예를 들어 hello라고 된 태그가 있다고 하면 어떨 때는 tailwind CSS의 규칙에서 벗어나고 싶을 때가 있음

예를 들어 글씨를 크게 만들고 싶다고 할때, 클래스명에 text를 적으면 여러 선택지가 있음

text-lg나 text-xl, 3xl, 2xl, base 등등 이런 모든 옵션들이 있음

그럼 만약에 내가 가장 큰 옵션보다도 더 크게 만들고 싶다면 어떨까

지금 이것이(text-9xl) 테일윈드가 제공하는 옵션의 최대값임

그럼 이제 개발자 도구에서 스크롤해보면 클래스명이 추가되어 있음

하지만 만약 테일윈드의 제한에서 벗어나야 한다면 어떻게 해야할까

만약 실제로 텍스트가 200px이기를 원한다면 어떻게 해야할까

예전에 했던 방법은 지금 노마드코더 웹사이트에서도 쓴 방법이기도 한데 이렇게 직접 씀

fontSize 속성에다가 예를 들어 800px를 직접 줌

이렇게 해야 했음

왜냐하면 프레임워크에 의해 제한받고 있었기 때문임

왜냐하면 테일윈드에는 그보다 큰 사이즈가 없다는 제한이 있음

하지만 이제는 멋진 JIT 컴파일러 덕분에 이렇게 클래스명에다가 직접 'text-픽셀값'처럼 원하는 사이즈를 적을 수 있게 됐음

그럼 이제 개발자도구를 보면, 테일윈드가 text 97851px라는 클래스를 실제로 만들었고 실제로 그 사이즈를 속성에 넣었음

또 다른 예로 색상을 한번 해봄

만약에 어떤 이유로 테일윈드의 색상 중에 마음에 드는 색상이 없다고 해봄

물론 테일윈드는 많은 색상들을 제공하지만, 그것들을 다 좋아하지는 않을 수도 있음

특수한 색상이 필요하다고 해봄

그럼 무엇을 해야할까

그럼 text-라고 적고 대괄호 안에 이렇게 직접 색상값을 줘봄

그럼 이제 무슨 일이 생길까

생성된 클래스가 있는지 개발자 도구에서 살펴보면 opacity 속성도 같이 있음

하지만 여전히 조심스러운 의견으로는 가장 좋은 부분은 아님

가장 좋은 부분은 바로 배경화면 이미지를 만들때임

테일윈드 3.0 이전에 배경 이미지를 설정하려면 이렇게 해야했음(inline-css)

이렇게 직접 이미지 주소를 적고 뭐 이런 것임

이제는 클래스명에다가 여기에 원하는 이미지 URL을 붙여넣으면 됨

우리는 vercel.svg라고 해줌

이렇게 배경화면 이미지가 설정됐음

CSS를 클래스명에서 적고 있는데, 적는 것이 전부 그대로 생성되고 있음

이것이 바로 JIT 컴파일러의 힘임

그리고 또 JIT 컴파일러는 예를 들면 여기 dark:md:hover:bg-teal처럼 이렇게 긴 클래스명을 생성해서 여러가지 선택자들을 겹쳐서 사용할 수도 있음

거기다가 특정한 값을 지정할 수 있게도 해줌

예를 들어 이렇게 직접 설정한 글자 크기라든지, 배경 색상이라든지 아니면 이렇게 원하는 이미지를 배경으로 한다던지 CSS가 한 줄도 필요 없음

다시 한번 JIT 컴파일러 덕분에 우리는 원하는만큼 선택자를 쌓아서 사용하거나 우리가 원하는 값을 설정해줄 수가 있음

예전에는 할 수 없던 것임

그러니까 거짓말 했던 것임

과거처럼 하나의 커다란 CSS 파일은 없지만, 이제 그것보다 훨씬 나은 방법으로 작동함

이것으로 놀래켜주려고 가장 마지막까지 기다렸음

JIT 컴파일러는 매우 멋진데다가 빠르기까지 함

## 4.13 Conclusions

여기까지가 Tailwind CSS를 알아보기 위한 여정이었음

Tailwind CSS를 좋아하게 됐길 바라고, 앞으로 Tailwind CSS를 사용해보길 바람

이제 우리는 JIT 컴파일러가 얼마나 굉장한지 알게 됐음

보다시피 매우 편리하고, 우리를 더 생산적으로 만들어주고 거의 한계가 없음

CSS 코드가 하나도 없이 전부 클래스명에 다 들어가고, 반응형 디자인도 있고 다크 모드 디자인도 있고 원하는 값을 넣을 수도 있음

폼이나 여러 상태 변화를 위한 선택자들도 있고 정말 굉장함

전에도 말했듯이 만약 테일윈드에 대해서 계속 이야기하고 싶다면 다음 섹션에서 봄

가짜 데이터들을 가지고 우리 어플리케이션의 모든 UI들을 한번 만들어봄

바로 다음 영상부터 테일윈드의 더 많은 기능들을 사용하는 것을 보여줌

만약 테일윈드 CSS에 대해서 더 알아볼 필요가 없다는 생각이 들면, 다음 섹션은 건너뛰고 백엔드 섹션의 소개 영상에서 보도록 함

어떤 것을 보기로 결정했든지 간에 다음 영상에서 보도록 함

그럼 거기서 봄

## 5.0 Introduction

이전에 말했다시피 이 섹션은 오직 UI만 클론함

UI를 만들거고 기본적으로 우리가 배워왔던 것들을 적용해봄

이전에 배웠던 것들이 있음

TailwindCSS를 적용해보고 연습해봄

만약 Tailwind를 연습해보기를 원한다면, 더 능숙해지고 싶다면 이 섹션에 머무르면 됨

만약 시간이 없다면, 그리고 padding이나 margin 등을 싫어한다면 다음 섹션에서 봄

거기서부터 인증 시스템, 백엔드, 데이터베이스 등을 만들기 시작함

다시 말하지만 Tailwind를 더 잘 하게 되고 싶다면 여기에 머물러

왜냐하면 장담하는데 유익한 시간이 됨

만약 Tailwind를 편안히 다루게 된다면, 그것은 아주 큰 이익으로 돌아옴

왜냐하면 아주 생산적이게 만듦

그리고 지금으로서는 좀 속도가 느리다고 느껴질지라도 낙담하지마

클래스 이름을 잊어버린다든가, 직관적이지 않다고 생각할 수도 있고, 숫자나 단위도 잊어버릴 수 있는데 걱정하지마

장담하는데 훨씬 나아짐

하지만 그렇게 편안해지기 위해서는 어쨌든 Tailwind를 사용해야만 함

그래서 사람들한테 연습하는 것을 추천함

하지만 연습할 시간이 없다면, 이것저것 만드는 serverless 파트로 넘어가고 싶다면 거기서 봄

물론 다음 섹션임

이번 섹션에서는 단지 UI만 만들어봄

말했다시피 오직 가짜 데이타로 만듦

그리고 약간의 URL들도 만들어볼 예정임

페이지들도 만들어볼거고, 그런 스크린들도 만들어봄

그러고 난 후에 이 섹션의 말미에서 우리 코드를 약간 정리해봄

왜냐하면 곧 알게 될 테지만, 우리 UI의 몇몇 엘리멘트들은 아주 반복적이게 됨

많은 다른 화면들마다 반복되게 됨

그래서 많은 다른 화면들에서 반복되는 것을 발견하면, 우리는 그것을 컴포넌트로 바꿈

그러고나서 Props 등 이야기해봄

하지만 우선은 UI를 만듦

그리고 코드를 정리하고 모든 것이 다 끝나면, 우리는 다음 섹션으로 넘어감

왜냐하면 최종적으로 UI를 끝냈으니까 이 코스를 진행하는 훨씬 나은 방법이라고 봄

왜냐하면 우리가 컨셉을 구분해서 집중할 수 있게 Tailwind에 관해서 다시 이야기하지 않아도 됨

이 섹션에서는 Tailwind에 관한 것을 하고, 다음은 Serverless 데이타베이스와 인증에 관해서 해보도록 함

그 다음에 Data Fetching 등등 우리는 각기 다른 컨셉들로 쪼개봄

이것이 이 영상의 끝임

다시 말하지만 이것을 굳이 볼 필요는 없음

하지만 만약 본다면 아주 훌륭한 Tailwind 스킬들을 갖게 됨

얼마나 Tailwind가 강력했는지 이전 섹션에서 봤었음

다음 영상에서 봄

바로 전 영상 이후로 아무것도 건드리지 않았음

단지 Home만 지웠음

지금은 null을 리턴하고 있음

우리는 인증 UI를 만들어봄

유저는 휴대폰하고 email로 로그인할 수 있으니까, 아마 Tab 같은 것을 쓰던가 해야함

## 5.1 Auth part One

Enter 페이지부터 만들어봄

이미 HTML파일을 준비해뒀음

카메라를 켜고 HTML을 작성하는 것은 모두에게 매우 지루할거라고 생각했음

그러니까 이 HTML을 가져다 쓰고 싶다면, 영상 상단에 있는 링크를 클릭함

깃헙 커밋에 가서 코드를 긁어다가 복붙하면 됨

enter.tsx라는 파일임

자바스크립트를 쓰고 있다면 확장자는 jsx여야함

이 파일은 반드시 pages 폴더 내에 있어야만 함

그거면 됨

빠르게 설명해봄

여기 타이틀이 있음

여기 두 버튼은 각각 탭(Tab)이 됨

여기 두 버튼들이 있음

그리고 얘네가 하는 것은 그냥 State를 변경하는 것임

그래서 여기 State가 있음

method란 이름임

그리고 이것은 “email” 또는 “phone” 두 문자열 중 하나가 될 수 있음

왜냐하면 우리가 email 또는 phone으로 로그인 해야하기 때문임

두 함수가 있는데 그건 method를 email 또는 phone으로 설정함

그리고 이 버튼들은 각각 phone 또는 email로 변경시킴

이제 form이 있는데 보다시피 method의 상태에 따라 각기 다른 텍스트를 보여주는 label을 갖고 있음

그래서 만약 여기를 클릭하면 label은 'Email address'임

그리고 여기는 input이 있음

여기를 클릭하면 label은 'Phone number'가 됨

그리고 여기 input은 숫자 input이 됨

보다시피 이 form을 submit하는 이 버튼 또한 우리가 휴대폰 번호로 로그인 한다면 이렇게 Get one-time password로 바뀜

그리고 이메일 주소로 로그인 한다면 Get login link임

그래서 여기도 보면 입력란이 변함

만약 email로 로그인하면 이렇게 input을 얻고, 번호로 로그인하면 이렇게 div를 얻음

input을 멋지게 만들어줄 멋진 Tailwind를 적용함

이 버튼도 물론 바꿈

그리고 여기를 보면 “enter with”가 있음

깃헙 또는 트위터로도 들어갈 수 있음

우리는 소셜 로그인도 만듦

이 HTML란 놈이 모두에게 매우 지루하기 때문에 이 HTML 파일을 이 영상 상단에 있는 링크에서 복붙해도 됨

그리고 또한 명심해

딱히 하는 것을 완전히 따라할 필요는 없음

똑같은 디자인, 똑같은 UI일 필요는 없음

이 섹션에서의 중요점은 직접 Tailwind를 연습하는 것임

그대로 따라할 필요는 없음

그게 내가 쌩 HTML로 시작한 이유임

후에 원하는 어떤 클래스 이름이든 추가할 수 있음

왜냐하면 TailwindCSS를 연습하는 것이 요점임

그래서 다시 말하지만 꼭 똑같은 결과를 가질 필요는 없음

연습하거나 창의력을 발휘해서 지금 하려는 것보다 더 아름다운 무엇인가를 만들 수도 있음

그리고 그게 TailwindCSS를 연습하는 더 나은 길이 될거라고 봄

무엇인가 새로운 것을 구현해봄

그래서 이것을 한번 크게 만들어볼 생각임

그리고 이 div는 margin-top으로 16을 줌

훨씬 나음

이제 컨테이너는 margin-top 16으로 함

나쁘지 않음

"Enter using"은 font-medium으로 줘봄

이제 이 두 버튼은 className으로 grid를 줘봄

그리고 gap은 16으로 함

margin-top도 8로 해줌

거의 다 됐음

그래서 무엇을 할거냐면 border를 이 두 버튼들의 bottom에 덧붙이고 싶음

이것 좀 바꿔봄

너무 큰 것 같은데 margin-top 16이니까 훨씬 나음

그럼 이제 이리로 와서 width full을 줌

그래서 이것이 내 Tab들임

그럼 이제 각 Tab들에 padding-bottom을 줘봄

너무 큼

4로 함

그래서 이것을 각 버튼들에 줘봄

유저가 이 Email address를 클릭한다고 침

그냥 그런 척 해봄

유저가 Email address를 클릭했다고 가정해봄

그래서 만약 Email address를 클릭하면, 이것을 text-orange로 바꿔보고 싶음

마음에 듦

font-medium도 해줌

그래서 이것이 Email address를 클릭하면 보이게 됨

하지만 또한 border-bottom도 추가해야함

그래서 만약 Email address를 클릭하면, border 색깔은 orange로 줌

그래서 만약 Email address를 클릭한다면 이렇게 보임

Phone number를 클릭하면 이렇게 바뀜

그래서 이제 무엇을 하고 싶냐면 실제로 이 로직이 일어나게끔 하고 싶음

그리고 생각해보면 우리가 지금 하려는 것은 일종의 조건을 Tab 안에 시행하고 있음

이것들은 오직 유저가 이 Email address를 선택했을때에만 허용됨

일단 섹시하지 않은 방법을 보여주려고 함

그 다음에는 아주 간단하면서도 아주 도움이 되는 해결책을 살펴봄

조건부 클래스이름을 위한 유틸리티 함수를 만듦

그래서 우리는 우선 여기에 이것을 해야만 하고 끝에도 똑같이 이렇게 만듦

이것이 첫번째임

두번째는 이쪽으로 와서 어떻게 써야하냐면, 만약 로그인 method가 현재 “email”일 경우에 우리는 이것을 보여줌

아닐 경우에는 아무것도 없음

그래서 보다시피 아주 잘 동작함

그런데 이 똑같은 것을 다른 버튼에도 적용해야함

이전에 말했다시피 우리는 우선 일종의 중복된 코드를 갖게 됨

그리고나서 뭐가 반복되는건지 확인한 후에 코드를 정리함

그래서 만약 phone으로 로그인한다면 이것은 border-orange를 가짐

작동하는지 한번 봄

잘 작동함

border-b는 여기에 넣어둠

그런데 문제가 생겼음

이것이 예쁘다고 생각하지 않음

전혀 좋아 보이지 않음

우리는 처음에 이런 식으로 시작해야함

그리고 이것을 해야함

전혀 좋아 보이지 않음

그래서 많은 사람들이 Tailwind를 사용할때 무엇을 하냐면 일종의 함수를 만듦

좀 더 읽기 쉬운 클래스 이름을 쓸 수 있도록 해주는 함수임

함수를 만들건데 classname이라고 이름 지음

아니면 아무렇게나 지어도 됨

classname이라고 함

그리고 여기에 우리는 모든 클래스 이름들을 담음

고로 무한 인자를 받음

그리고 이것은 string 배열 타입이 됨

그리고 우리는 string 배열을 공백 한 칸으로 join()시키면서 리턴함

만약 이것이 무엇인지 모른다면 이렇게 1, 2, 3이 있고 join()을 한다면 string을 얻음

그래서 이것을 줌

하지만 만약 예를 들어 이런 식으로 이것을 넣는다면, 이런 식으로 join이 됨

이렇게 우리의 경우에 한 칸 공백으로 join 해줌

전혀 좋아보이지 않음

이 부분을 잘라내고 우리는 cls를 호출함

cls라고 쓰고 첫번째 클래스이름은 이것이 됨

일종의 기본값임

둘째는 여기서 작성되고 있는 이것을 넣음

그럼 우리는 이 못 생긴 것을 삭제할 수 있음

그럼 보다시피 훨씬 작성하기도 쉽고 조건식도 써넣을 수 있음

그리고 여기에 옵션들을 작성하고 매번 이런 것을 할 필요가 없어짐

이해하기 엄청 쉬움

다음으로 넘어가기 전에 보다시피 이 Email address는 약간 점프하는데 좋지 않음

최선은 이쪽으로 와서 잘라내서 여기에 붙여넣음

어떤지 보면 보다시피 Email address는 더 이상 점프하지 않음

border를 여기에 넣어볼 수 있지 않을까

Email address는 더 이상 점프하지 않음

이제 우리는 똑같은 것을 Phone number에 적용할 수 있음

거의 다 됐음

만약 이것이 클릭되지 않은 상태라면 text-gray-500이 되도록 함

어떻게 보이는지 한번 봄

나쁘지 않음

그래서 이제 이것을 복사해서 여기에 붙여넣음

그리고 이것을 phone으로 바꾸는 것을 잊지마

그럼 다 됨

어떻게 보이지

그리 나쁘지 않음

이 input을 가져와야함

그리고 input들은 위에 label을 갖고 있고, input을 위해서 우리는 Tailwind plugin을 설치함

다음 영상에서 보여줌

그런데 현재로서는 이것으로 충분하다고 생각함

괜찮다고 봄

보다시피 이것은 그냥 CSS임

그냥 많은 TailwindCSS임

그리고 우리는 이 새로운 것을 배웠음

나중에 이것을 다른 파일로 옮겨야할 거 같음

꽤 유용한 놈이라고 생각함

하지만 그것은 다음 영상이 됨

재미는 없었음

하지만 TailwindCSS를 연습할 수는 있었음

## 5.2 Auth part Two

이번 영상에서 우리는 Tailwind Plugins에 대해서 이야기함

이유는 Form의 기본 스타일을 갖도록 해주는 Plugin을 사용하고 싶기 때문임

지금 input들은 여기 보다시피 별로임

얘네들을 바꾸고 싶음

그래서 무엇을 할거냐면, Tailwind Forms라 불리는 코어 Plugin(또는 오피셜 Plugin)을 설치함

Plugin은 기본적으로 Tailwind 환경에서 부가적인 기능을 더해주는데 어떤 코어, 핵심 Plugins들도 존재함

인기 기능을 위한 plugin인데, 이런저런 이유로 아직 메인 프로젝트에 속해있지는 않음

하지만 원한다면 설치할 수가 있음

예를 들면 이렇게 typography plugin을 설치한다면 이 "prose" 클래스 이름을 더할 수 있음

우리의 경우에는 forms라는 plugin을 설치함

input에 reset layer를 추가할 수 있는 plugin임

우리 코드를 절약해줌

그래서 이것을 복붙함

그리고 여기에 install 해줌

터미널에 npm i @tailwindcss/forms@0.4.0 -D 입력함

그럼 다 끝냈으면 tailwind.config.js로 가봄

그럼 여기에 배열을 넣어줌

그리고 보다시피 이 라인을 저장하는 순간, form들이 약간 바뀌었음

그런 것 같음

그럼 시작할 준비가 됐음

이제 label하고 input을 손봄

그럼 form에다가 className을 적고 전부 flex-column으로 해줌

label은 내 생각에 꽤 쉬울 것 같음

클래스 이름을 만들어야함

다 끝난 것 같음

이것이 내 Phone이 됨

다 됐음

그럼 이제 form에 여기 div에다가는 className으로 margin-top을 1로 함

먼저 input을 해줌

Email input을 먼저 해치움

Email input은 우선 외관을 리셋시켜야함

input이 갖고 있을지도 모르는 기본 스타일을 리셋해줌

w-full을 해줄거고 어떻게 보이는지 한번 봄

나쁘지 않음

하지만 패딩이 좀 필요할 것 같음

패딩을 좀 추가해볼건데 여기에다 좌우 패딩 4를 주면 훨씬 나음

그럼 우리 input으로 돌아가서 이제 이것을 둥글게 만들어야함

그림자도 넣어야하고 그리고 focus 상태일때의 스타일을 추가해야함

placeholder도 줌

focus-outline은 none이어야 하고 outline은 필요 없으니까 그러고나서 focus를 해야함

어쩌면 주변에 원을 추가할 수도 있음

그럼 끝났음

이것이 바로 우리 input임

나쁘지 않음

마음에 듦

이제 button을 손볼 차례임

지금 이 부분은 일단 스킵하고 button부터 봄

우리는 orange를 메인 색상으로 해야할 것 같음

전부 orange로 쭉 밈

고로 배경색을 해봄

orange-500이 됨

hover over에 bg-color도 orange로 함

text는 white임

여기도 똑같이 padding-x에 4를 줌

input하고 똑같이 border, border-transparent, rounded-md함

나쁘지 않음

이제 shadow를 걸어줘야함

그리고 text도 small이어야 하고, font는 medium으로 함

그럼 이제 한번 봄

그래서 여기 위에 마우스를 올려보면 마음에 듦

이건 좋아보이지 않음

그래서 focus:ring-2함

또 focus:ring-offset도 2가 되어야함

그리고 하고 싶다면 hover over에 transition을 걸어줄 수도 있음

그리고 focus:outline-none함

그럼 어떻게 보일까

그럼 이제 이 button에 margin-top을 줘봄

너무 크지도 않고 그럼 이제 다 됐음

우리의 button임

5로 고침

이제 Phone number의 input을 손볼 차례임

Phone number input에는 이 82를 이 input 안에 넣고 싶음

이거 마음에 듦

이 input도 좋고 이 button도 좋음

이제 시작해봄

이제 이것을 flex로 만들어주기만 하면 됨

이렇게 rounded를 넣어줌

이제 마치 이 82도 input에 속해있는 것이라고 사람들이 생각하게끔 일종의 trick을 만듦

그래서 우리는 span에다 flex를 넣어줘야함

그리고 items는 center로 함

그리고 justify도 center로 함

고로 얘는 center로 올거고 몇가지 더 추가함

여기서 보여주고 싶은 것이 있는데, 만약 이 두 가장자리만 둥글게 만들고 싶다면

이 가장자리는 둥글게 하고 싶지 않음

그럴 경우에는 rounded-l-medium을 쓰면 됨

그리고 border를 하면 테두리가 보임

딱 한쪽 부분만 rounded 되어있음

그래서 예를 들면 이 경우에 이렇게 rounded 할 수도 있음

그럼 오직 이쪽 부분만 둥글어졌음

꽤 좋음

만약 위에 마우스를 올려두면 Tailwind가 무엇을 해주는지 볼 수 있음

이것은 약간 shortcut 같은 것임

마음에 듦

그럼 이제 오른쪽 테두리는 없애줘야함

그럼 보다시피 input 안에 있는 것처럼 보이지만, 실제로는 input이 아님

엄청 멋지다고 생각함

input의 일부분이면서 disabled된 것처럼 보임

원한다면 이것을 select-none으로 만들 수도 있음

그럼 이것을 select 할 수 없게 됨

물론 모든 사람들의 번호가 이 숫자(82)로 시작하지는 않는다는 것을 앎

이런 것을 보여주고 싶었음

멋진 기능이라고 생각함

기능은 아니고 멋진 트릭을 씀

Tailwind를 쓰는 모두가 사용하는 좋은 패턴임

다들 이렇게 쓰고 많은 웹사이트에서도 봐왔음

우리 input을 손봄

평소에 하는 거랑 같음

이전에 했었음

사실상 이 input을 복사하면 될 것 같음

그냥 복사해와서 className까지 여기에 붙여넣음

그럼 다 됨

이 rounded는 보기 좋지 않음

그래서 우리가 할 것은 저 rounded를 없애버리는 것임

그래서 여기에 rounded를 하고 싶은데, 0이 아니라 none임

어떻게 보이는지 봄

거의 다 했음

이것을 이 “Or enter with”에 mt-6으로 마무리해봄

그리고 여기에 relative 클래스를 넣어줌

그 이유는 금방 알게 됨

그 이유는 뭐냐하면 바로 여기에 absolute를 할거기 때문임

그러니까 className을 absolute로 함

flex를 줌

왜냐하면 이것을 하고 싶었음

아주 심플함

아주 쉬움

이제 무엇을 하고 싶냐면 이쪽으로 와서 여기 className을 relative로 줌

그리고 여기 이 span에 bg-white를 함

text-center도 함

이제 중앙에 있음

마음에 듦

그래서 이제 여기로 와서 padding을 줌

그럼 거의 다 됐음

이것이 바로 relative랑 absolute를 조합할 수 있는 방법임

그럼 다 끝났음

margin-top을 8로 해줌

그럼 이제 이 두 button들을 작업해봄

그럼 우선 이 button들의 container에 className을 달아봄

그리고 margin top은 6으로 줌

그리고 첫번째 button에 집중해봄

지금까지 해왔던 거랑 같이 다른 녀석들하고 거의 동일하게 500으로 함

이것은 트위터고 이것을 복사해서 여기에 붙여 넣어줌

이것은 깃헙 버튼임

클릭할 수 있는 버튼들임

이것은 좀 멀리 간 것 같음

2로 함

그럼 이제 끝임

이것이 우리 시작 화면임

폰 번호를 입력할 수 있고 82를 찾아봄

너무 큼

Email이면 "Get login link"라고 뜨고 Phone이면 "Get one-time-password"라고 뜸

또는 소셜 로그인 버튼도 누를 수 있고 이것으로 다 끝냈음

약간 짜증나는 화면이었음

다음 영상에서 봄

코드는 깃헙에 있음

## 5.3 Home Screen

이제 우리의 front page를 만들 차례임

front page는 기본적으로 상품들의 리스트가 됨

이미 HTML을 끝내놨기 때문에 딱히 할 필요는 없음

HTML을 갖다 쓰고 싶으면, 영상 상단의 링크를 클릭하면 됨

어떤 클래스이름도 없는 HTML을 복사할 수 있고, 우리가 함께 클래스이름을 추가해봄

완전히 똑같은 클래스이름을 할 필요도 없고, 원하는대로 만들어도 됨

자신의 스타일을 만들면 됨

내 생각에 그게 나은 것 같음

꽤 연습하게 됨

그럼 이것이 우리의 HTML이고, 보다시피 모든 상품들을 하나의 HTML에 렌더링하고 있음

이것은 그냥 각기 어떻게 보이는지 확인하기 위한 용도고, 여기서 시작하면 됨

className을 씀

모조리 flex로 해주고, flex-column에 space-between을 각기 5로 줌

그리고 여기에 상하 padding 10을 줌

이제 여기 div에 flex를 줌

각 상품은 flex가 됨

그래서 flex를 씀

클릭해서 세부 사항을 볼 수 있어야 하니까, 커서는 cursor-pointer로 함

그리고 justify-between을 함

거의 완벽함

이제 여기 바로 이것은 이 column(열)임

우리는 두 column(열)을 갖고 있음

하나는 좋아요랑 하나는 댓글을 보여주는 곳임

고로 다시 calssName을 써줌

여기는 이미지가 들어갈 자리인데, 지금은 임시로 일단 당분간은 정사각형 박스로 해놓음

이것을 후에 실제 이미지로 변경함

나중에 이미지로 바꿈

둥글게 만들 수도 있을텐데 그렇게 함

그럼 넘어가도 됨

내 생각에 이것은 form에서처럼 padding이 필요할 것 같음

모두 다 padding을 가짐

다들 보기 좋음

아니면 이것을 여기에 줄 수 있음

그럼 이제 타이틀임

h3에 className으로 함

나쁘지 않음

이것이 우리 h3가 됨

이제 어쩌면 이 container 상단에 padding을 줘야할 수도 있음

이것은 약간 작은 애가 됨

얘네 부모에 flex랑 flex-column을 줘봄

나쁘지 않음

그리고 이 아이한테도 text-gray-500을 함

거의 다 됐음

이제 가격을 할 차례임

그래서 이제 가격을 약간 뚱뚱하게 함

이것이 우리 상품임

보다시피 아주 쉬움

우리는 타이틀을 갖고 있고, 상품의 어떤 설명이 있고 가격을 갖고 있음

사진만 넣으면 훨씬 나은 모습이 됨

그런데 NextJS에서의 이미지에 관해서 알아야할 몇가지가 있음

NextJS는 즉시 사용할 수 있는 아주 멋진 이미지 최적화를 갖고 있기 때문임

그래서 조금 있다가 나중에 이미지를 넣음

그럼 이제 이 파트로 넘어감

그럼 여기를 열어봄

여기 아이콘이 두개 있음

하나의 아이콘에는 svg, 그리고 숫자가 있음

이것도 똑같음

댓글 아이콘이랑 숫자가 있음

이 아이콘들을 어디서 얻었는지 궁금해 할거 같음

아이콘이 멋짐

아이콘은 heroicons라고 부르는 곳에서부터 얻을 수 있음

heroicons.dev는 오직 svg들의 콜렉션임

그래서 심지어 font-awesome과 같은 것들처럼 인스톨할 필요가 없음

종류가 엄청 많이 있는 것 같음

Font-awesome만큼은 아니지만 유용함

여기서 다 가져다 썼음

예를 들면 heart도 찾아보면 나오고 comment도 얻을 수 있고 user도 있음

그냥 다 있음

그냥 여기를 클릭함

그리고 코드로 되돌아와서 이렇게 붙여넣음

물론 몇가지를 수정해야됨

예를 들면 이것은 className으로 함

하지만 보다시피 Tailwind로 바로 쓸 수 있도록 준비 되어있음

w-6랑 h-6은 Tailwind 클래스이름임

그리고 잊지마

가끔은 이런 것을 고쳐야함

왜냐하면 이 path 태그에 있는 이 attribute는 React에서는 작동하지 않음

이렇게 고쳐야됨

그럼 이제 svg를 갖게 됐음

그래서 이것을 진짜 좋아함

아주 가벼움

이것은 그냥 코드임

이것은 그냥 svg고 원한다면 solid나 outline으로 고를 수도 있음

이것이 아이콘을 가져온 곳임

엄청 추천함

계속 해봄

이것은 그냥 flex로 만들면 됨

icon container를 flex로 만들어야겠고, 그럼 button으로 넘어가도 됨

이것을 닫아줌

보다시피 이것들은 아이콘들이고 이것은 container임

정말 쉬움

그리고 끝으로 몰고 싶으니까 items-end를 해야함

그리고 또 justify-end를 함

그리고 아이콘들도 각자 스타일을 가져야함

얘네도 flex를 해야함

text는 작게 만들어줌

그리고 잊지마

얘네는 svg임

즉 그냥 text-color를 바꿀 수 있음

그러니까 text-gray를 해줌

그리고 정말 좋아하는 className을 사용함

그건 svg에 margin-right를 span에 margin-left를 추가시켜줌

svg에 margin을 추가해주는 것 대신에, span에 margin을 사용하는 것 대신에 이쪽으로 와서 이렇게 쓰면 됨

space-x, 우리 경우에는 0.5임

여기 볼 수 있다시피 이것은 무엇을 하냐면, div의 자식들에게 margin-right와 margin-left를 추가해줌

그래서 보다시피 그냥 한 줄의 코드만 쓰면 됨

그럼 margin-right와 margin-left를 할 필요가 없음

엄청 멋지다고 생각함

이 클래스이름을 복사해서 여기다 붙여넣음

그럼 우리는 다 끝냈음

이 스크린은 정말 쉬움

다시 말하지만 보다시피 아주 중요한데 좋아요와 댓글 사이에 공간이 없음

그래서 여기에 margin-right, 여기에 margin-left 클래스 이름을 추가하는 것 대신에 그냥 space를 하면 됨

그래서 여기로 와서 이 경우에 space-x1.5를 넣음

그럼 다 됐음

그럼 이제 얘네 사이에 space(공간)이 생김

좀 더 크게 하고 싶으면 2로 할 수 있음

이 화면은 보다시피 아주 쉬움

이제 이 button을 해봄

floating button으로 만들어야함

일단 이것을 원으로 해야겠지

보다시피 여기에 둥 떠 있는데 이것을 bottom으로 놓아야만 함

그래서 bottom을 24로 하고 싶음

그리고 right은 5로 함

배경색은 orange로 감

너무 작은 것 같은데 어떻게 생각해

너무 작으면 더 크게 만들 수 있음

padding을 4로 만들어줌

그럼 이제 유저가 사용할 수 있는 floating button이 생겼음

여기를 클릭하고 싶음

굉장히 간단함

이제 hover 상태를 넣을 수 있음

초기값은 400이니까 이것은 500으로 함

그리고 cursor-pointer도 해줌

그럼 이제 floating button이 생겼음

그럼 여기를 클릭하면 유저는 상품을 추가하기 위한 form으로 보내져야함

그래서 이것이 업로드 링크임

여기를 클릭하면 상품을 업로드함

정말 간단한 화면임

정말 간단한 상품임

다음 영상에서는 여기에서 이 링크를 클릭했을때, 이 상품의 상세정보를 볼 수 있도록 해봄

## 5.4 Item Detail

이제 홈페이지에서 아이템 하나를 클릭하면 나올 아이템 디테일 페이지를 해봄

여기서 이렇게 클릭하면 슬래시 items 슬래시 id 페이지로 가게 됨

id는 무엇이든 될 수 있음

이렇게 items 뒤에 id가 붙는 형태임

이미 알고 있겠지만 Next.js에서 이런 형태의 url을 구현하려면, 이렇게 pages 폴더에서 items라는 이름의 폴더를 만들어주고 대괄호로 id를 감싸주면 됨

대괄호를 사용하면 id라는 페이지가 만들어지는게 아니라, Next.js에게 여기에 변수가 들어가는거라고 알려줌

그것만 잘 알고 있으면 됨

이제 여기 있는 HTML을 사용함

여기에는 나중에 사진이 들어감

Next.js에서 이미지를 어떻게 다루는지를 공부할때 해봄

이것은 우리가 예쁘게 만들어볼 프로필임

이것은 상품의 정보고, 판매자랑 대화할 수 있는 버튼도 있음

상품에 좋아요 표시를 할 수 있는 버튼임

그리고 여기에는 아주 간단하게 '비슷한 상품'을 렌더링함

그런 것 본적 있지

상품 페이지에서 스크롤을 하다보면 비슷한 상품을 보여줌

이것도 나중에 이미지로 바꿈

padding부터 설정해봄

위쪽 padding도 10정도로 설정함

이정도면 괜찮은것 같음

이 이미지는 높이를 96정도로 줌

background-color는 일단 100으로 줘봄

잘 보이게 200정도가 좋겠음

300이 나을까

이것은 임시로 해놓음

나중에 멋진 이미지로 바꿔봄

여기는 사용자의 프로필임

이것은 유저의 프로필 사진(Avatar)임

이러면 동그라미가 잘 보임

여기에 패딩을 추가함

border도 넣음

이러면 아래쪽 border가 생겼음

원한다면 위쪽에 margin을 추가해도 됨

좀 별로임

방금 것은 무시함

이제 사용자의 이름임

className을 씀

사용자를 표시하는 부분은 끝났음

여기에 커서를 올렸을때 포인터 모양이 되게 하면 좋을 것 같음

이렇게 포인터 모양이 되고, 클릭하면 프로필로 감

이제 메인 요리 차례임

일단 위쪽 margin을 10정도 줌

h1 태그를 손봄

지금보다 더 커야할 것 같음

마음에 듦

색을 검정에 가까운 회색으로 바꿔볼까

완전 검정은 잘 안 씀

완전 까만색은 별로 보기 좋지 않은 것 같음

어두운 회색이 훨씬 나은 것 같음

이 p 태그는 span 태그로 바꿔줌

block으로 만들어주는 것도 잊지마

이 p 태그도 비슷하게 해주면 됨

버튼을 스타일링할 차례임

하트 옆에 버튼을 만들어줌

이 버튼은 전에 만들었던 버튼이랑 아주 비슷함

어쩌면 컴포넌트로 만드는게 좋을지도 모르겠음

버튼 컴포넌트를 만들어야 할 것 같은데, 일단은 줄어들지 않도록 flex-1 클래스를 추가해줌

flex-1을 적용하면 다른 형제 요소보다 flex가 강해짐

이 하트가 '판매자와 대화하기' 버튼의 형제 요소임

flex-1을 적용하면 줄어드는 것을 방지할 수 있음

배경색은 오렌지색으로 함

bg-orange-500으로 함

전에 만들었던 거랑 똑같은 것 같은데 좀 더 둥글게 만들어야 할까

이대로도 괜찮은 것 같음

shadow를 추가하고, focus도 손봐야겠음

또 있나

항상 하던대로 하면 됨

여기를 클릭해보면 이렇게 focus 효과가 나옴

그럼 해봄

한번 확인해봄

잘 됨

이제 shadow를 추가함

그림자가 좀 별로임

그냥 폰트만 조절함

이러면 버튼은 완성됐음

focus 상태면 이렇게 보임

그리고 원한다면 hover할때 색을 어둡게 만들어줌

클릭도 해봄

ring 효과가 너무 좋음

이 버튼은 다 했음

하트 버튼을 만듦

좋아요 표시를 한 상품 리스트에 상품을 넣을 때 쓸 버튼임

그리고 텍스트 색을 바꿔줌

텍스트 색은 gray 400으로 함

hover 할때도 설정해줌

버튼이라는 것을 사람들이 알 수 있게 배경을 회색으로 해주고, hover 했을때 색도 바꿔줘야함

이렇게 하면 나쁘지 않은데 둥글게 만들어야겠음

여기 flex에서 spacing 처리를 해줌

spacing은 조그맣게 넣을까

그럼 여기는 다 마무리 됐음

이 focus는 원하는대로 바꿔보면 좋을 것 같음

지금 상태로도 괜찮은 것 같아서 그대로 둠

거의 다 됐음

text-base는 전에 다뤄보지 않았던 것 같음

text-base는 기본적으로 text를 리셋해주는 거라고 생각하면 됨

기초 상태로 만들어줌

아무런 설정도 해주지 않으면, 모든 text가 이런 상태임

보다시피 이것을 지운다고 해서 폰트가 변하지는 않음

지워도 바뀌지는 않음

위쪽 부분은 다 끝났음

상당히 빨랐음

이제 여기를 좀 바꿔봄

여백이 너무 넓은 것 같음

5정도로 함

이제 여기 '비슷한 상품' 부분을 꾸며줘야함

그렇게 어렵지는 않음

일단 여기에 margin-bottom을 줘야할 것 같음

두 구역을 나눠야함

하나는 이 시작 부분이고, 다른 하나는 '비슷한 상품'이 있는 이 공간임

그럼 여기에 margin-bottom을 줘야하는데 8정도로 함

이제 '비슷한 상품'만 꾸며주면 됨

거의 다 끝났음

여기가 중요함

여기는 grid로 만듦

보다시피 아이템을 6개 렌더링하고 있는데, grid에 넣으면 좋을 것 같음

grid를 연습해볼 수 있는 좋은 기회임

다 된 것 같음

여기는 끝난 것 같고 여기를 수정함

여기에는 class를 넣을 필요가 없음

그런데 여기에는 이미지가 들어감

지금은 그냥 볼품없는 사각형을 넣어줄거지만, 나중에 이미지를 넣으면 이쁨

어느정도 '비슷한 상품'이 만들어졌음

margin-top을 추가해줘야 할 것 같음

이미지 아래쪽에 작게 4정도 마진을 넣어줌

상품 이름도 꾸며줌

가격은 span 태그로 바꿔줌

텍스크 크기도 작아야함

이것을 xs로 바꿔줘야 할 것 같음

여기에는 아무것도 설정하지 말고, 이것을 sm으로 바꿔줌

여기에 -mb-1을 설정해줌

다 됐음

관련 상품 영역을 만들어 봤음

이것은 나중에 다 이미지로 바꿈

꽤 마음에 듦

여기 이것은 프로필임

이것은 다른데서도 쓸 것 같음

판매자와 대화하기 버튼도 있고, 원한다면 상품에 좋아요 표시도 가능함

## 5.5 Upload Item

이번 영상에서는 업로드 화면을 만들어봄

업로드 화면은 사람들이 바로 여기 있는 이 버튼을 눌렀을때 보이게 됨

이 버튼을 누르면 업로드 화면으로 감

그리고 보다시피 이 웹사이트는 모바일에 잘 맞지가 않음

모바일 웹사이트처럼 보이긴 하는데 그래도 걱정 하지마

이번 섹션의 마지막에 고쳐봄

다시 돌아가서 VS Code의 pages 폴더 안의 items 폴더의 upload 페이지를 만듦

items 폴더 안에서 두 개의 url로 이동할 수 있게 됨

하나는 id이고 다른 하나는 upload임

그럼 시작해봄

이렇게 슬래시 items 슬래시 upload로 이동해보면 이런 화면이 나오게 됨

HTML은 다 만들어져 있음

영상 위쪽의 링크를 참조하도록 함

그럼 바로 시작함

그렇게 오래 걸리지는 않음

그래도 파일 선택을 구현할때 정말 자주 사용되는 테크닉을 알려줄 생각에 신남

바로 여기에 적용해봄

보다시피 클릭을 하면 파일을 선택할 수 있음

그렇지만 보다시피 썩 훌륭하지가 않음

이것도 바꿔봄

바로 시작해봄

일단 padding이랑 margin을 좀 추가함

사진을 업로드하는 부분부터 바로 만들어봄

곧 얼마나 쿨한지 알게 됨

label 태그를 감싸고 있는 div 태그를 수정해줌

HTML은 수정하지 말고 있는 그대로 두는 것이 좋음

여기 label 태그 안을 보면, svg 태그랑 그리고 파일 input 태그도 있음

이것이 무슨 일을 하는지는 나중에 알게 됨

파일 input 태그를 완전히 보이지 않게 만들어줌

이렇게 하면 아이콘만 가운데에 남게 됨

보다시피 아이콘을 클릭하면 파일을 선택할 수 있게 됨

input 태그를 label 태그 안에 넣고 input을 숨기는 간단한 테크닉임

react.js로 input 태그를 렌더링은 하지만 css로 그것을 숨김

그러면 이것을 눌렀을때 input을 클릭하는거랑 같은 효과를 줄 수 있음

아주 멋진 테크닉임

예쁘지 않은 input은 숨김

계속 해봄

이번에는 멋진 상자를 만듦

위아래로 padding을 6정도 줌

생각대로 잘 만들어진 것 같음

나쁘지 않음

padding 대신 높이를 48정도 줘봄

둥글게 만듦

마음에 듦

아래쪽으로 margin을 좀 주고, 커서를 올렸을 때 색이 변하도록 해봄

잘 됨

border에도 똑같이 해줌

여기를 누르면 이렇게 파일을 선택할 수 있음

사실 이 class들을 이 div에 넣을 필요도 없음

그냥 이 class들을 가져다가, 이렇게 label 태그에 넣어줘도 됨

이 div는 지워버림

이렇게 해도 똑같이 작동함

클릭을 인식하는 범위가 좀 더 넓어졌음

커서도 포인터로 바꿔줌

아주 괜찮은 input이 만들어졌음

위쪽에 왜 이렇게 공간을 많이 남겨두나 궁금할 수도 있는데 그러는 이유가 있음

나중에 navigation 기능이 들어간 header를 만들거라서 그럼

그래서 공간을 조금 남겨둬야함

label 태그는 끝났음

이제 input 태그를 수정해봄

예상하겠지만 enter 페이지에서 만들어 봤던거랑 아주 비슷함

어쩌면 그 input을 컴포넌트로 만들어서 재사용할 수 있게 하면 좋을지도 모르겠음

home 페이지에서는 이렇게 htmlFor를 적어주는 것을 깜빡했던 것 같음

enter 페이지를 잠깐 빠르게 확인해봄

label에 htmlFor 속성을 넣어줘야함

값은 input이라고 함

그리고 이 두 input 태그는 input이라는 id 속성이 있어야함

Price라는 글자를 클릭하면 input 태그가 선택됨

label 태그는 enter 페이지에 있던 거랑 똑같이 해주면 될 것 같음

똑같은 스타일로 해주면 되니까 복사 붙여넣기함

이 div의 margin-bottom은 조금 바꿔줌

위아래로 다 줌

그 다음 input도 전화번호 input을 만들었을때랑 똑같이 만들면 될 것 같음

달러 표시를 input 안으로 넣어줘야함

부모 요소에 relative를 넣어주고 여기는 absolute를 써줌

다 끝난 것은 아니지만 거의 다 됐음

이제 input을 꾸며봄

home 페이지에 있는 거랑 똑같이 해주면 될 것 같음

home이 아니구 enter 페이지임

여기서 복사해서 여기에 붙여넣음

그렇지만 약간 다르게 해줘야 할 부분이 있음

여기에 padding을 추가해줘야함

그것만 바꿔주면 됨

보다시피 복붙하는 빈도가 늘고 있음

바로 해봄

왼쪽 padding을 7픽셀만큼 주고 달러 표시의 색도 바꿔줌

여기 USD라는 글자도 똑같이 해주면 됨

className을 쓰고 absolute를 줌

사람들이 이 글자를 이렇게 긁지 못하게 하려면, 여기에 pointer-events-none 클래스를 주면 됨

이것도 똑같이 해줌

이제 아까처럼 긁지 못 함

꽤 마음에 듦

이 label 태그에 margin-bottom을 1로 주고 block으로 만듦

이제 description 차례임

description의 label 태그는 방금 만들었던거랑 똑같이 해주면 됨

그대로 복붙해줌

description의 label 태그는 이렇게만 하면 되고 이제 textarea 태그를 꾸밈

이 div는 지워줘도 될 것 같음

솔직히 말해서 input 만든거랑 별 다를게 없을 것 같음

한번 확인해봄

여기를 클릭하면 잘 됨

focus에 오렌지색 ring 효과를 줬고 border는 회색이니까, focus했을때 border도 오렌지색으로 바꿔주면 됨

클릭해보면 잘 됨

아주 훌륭함

ring이 너무 두꺼운 것 같기도 함

너무 두꺼우니까 focus:ring-2는 지움

이제 괜찮은 것 같음

이제 똑같지

이제 upload product 버튼임

이 버튼은 enter 페이지에 있는거랑 완전히 똑같을 것 같음

보다시피 복붙이 많아지고 있음

이제는 컴포넌트로 만들어줘야 할지도 모르겠음

w-full만 추가해주면 끝남

나쁘지 않음

다 끝났음

이것이 완성된 모습임

이 페이지를 통해서 사람들이 물건을 업로드하게 됨

그리고 보다시피 여러 부분을 재사용하기 시작했음

그러니 아까 말했던대로 input이나 button을 컴포넌트로 만들어야 할지도 모르겠음

## 5.6 Community

이제 우리 앱의 커뮤니티 탭을 만들어봄

무엇을 할거냐면 pages 폴더에 있는 community 페이지를 수정할건데, 나중에 다른 곳으로 옮겨야 할 것 같음

지금 옮겨볼까

이 파일의 이름을 community 슬래시 index.tsx로 바꿈

이렇게 하는 편이 낫겠음

이렇게 하는 것이 더 낫다고 하는 이유는 뭐냐면, 사람들이 community 경로에서는 모든 게시글을 볼 수 있게 하고, id 경로에서는 각각의 게시물을 볼 수 있게 하려고 해서 그럼

이것은 나중에 구현해봄

항상 그랬듯이 별거 없기는 하지만 이 HTML을 쓰고 싶다면 영상 위의 링크를 참조하도록 함

내용을 보면 "동네질문"이라는 작은 컴포넌트를 하나 렌더링하고 있음

우리 동네 최고의 만둣집이 어딘지 묻는 그런 것임

똑같은 것을 궁금해하는 사람들이랑, 답변해준 사람, 그리고 버튼까지 front 페이지에서 플러스 버튼을 눌러서 새 상품을 등록했던 거랑 똑같이 이 쓰기 버튼을 누르면 새 게시글을 작성할 수 있음

물론 나중에 post detail 페이지랑 upload post 페이지도 만듦

그러니 바로 시작해봄

여기에 이렇게 써줌

그리고 여기에도 className을 주고 이 부분은 배치(batch)가 됨

rounded를 써서 먹는 알약 모양으로 만듦

rounded-full도 잊지 말고 여기에 적은 것 같은데 안 됨

태그가 만들어졌어.

여기에 좌우로 padding을 주는 것도 잊지마

이제 여기를 열어서 질문글을 꾸밈

여기는 div로 바꿔주고 className을 줌

여기도 className을 주고 질문 부분은 font-medium으로 함

질문 부분은 끝났음

이 div를 열어봄

이것은 질문한 사람 부분임

font는 medium으로 할까

"동네질문"이라는 배치(batch)랑 질문도 잘 보이고, 작성자랑 게시시간도 잘 나오고 있음

계속 가봄

하나 더 열어봄

또 flex-box임

flex가 엄청 많음

그리고 위쪽이랑 아래쪽에 border가 필요할 것 같음

이렇게 나옴

질문글이 이런 식으로 보일거고 이 부분만 고치면 될 것 같음

거의 다 됐음

그러니까 이 span 안에서 복사해서 여기도 똑같이 해주면 될 것 같음

게시글이 완성됐음

똑같은 것을 다섯개로 늘려봄

1, 2, 3, 4, 5, 6 숫자는 아무거나 써도 상관 없음

그리고 이렇게 key 속성도 잊지 않고 써주면 끝임

마음에 듦

조금만 더 다듬어보자면, 아래쪽 border가 좀 두꺼운 것 같음

border-b가 0이나 2밖에 없음

그럼 이렇게 1픽셀로 씀

임의의 값을 줄 수 있으니까 1.5정도로 해볼까

이렇게 변수를 쓸 수도 있다는 것 기억하지

멋진 기능임

2픽셀로 해볼까

버튼은 home 페이지의 버튼을 그대로 복붙해도 될 것 같음

home 페이지로 가보면 여기에 이미 만들었던 것이 있음

이것은 이제 닫고 여기에 붙여넣음

새 게시글 작성 버튼임

이렇게 커뮤니티 탭을 만들어 봤음

다음 영상에서는 이런 질문글을 클릭했을때를 구현함

질문글의 세부사항을 보게 되겠지

커서를 포인터로 만들어 주는 것도 잊지마

## 5.7 Community Detail

이번에 해볼 커뮤니티 디테일 페이지는 아주 쉬움

아주 금방 끝남

먼저 페이지를 어디에 만들어야할까

pages 폴더의 community 폴더 안에 대괄호 id 파일에 만들면 됨

이제 community 폴더 안에 index랑 id 두개의 페이지가 생겼음

index는 community 경로에서 표시되는 페이지임

index는 거기에 표시되는 페이지임

이렇게 community 뒤에 id가 붙으면, 그때 community detail 페이지가 나옴

그러니 community 폴더 안에 두 파일을 잘 만들었는지 확인하고 바로 시작해봄

얼마나 빨리 끝나는지 알면 놀람

왜 그러냐면 보면 알겠지만, 여러 컴포넌트가 많은 화면에서 재사용되고 있음

이번 community post detail 페이지에서도 많은 컴포넌트가 재사용됨

community post detail은 사용자가 community tab에서 질문글 하나를 클릭하면 나오는 페이지임

질문글을 클릭하면 community detail 페이지로 넘어감

가장 먼저 해야 할 일은 질문글을 올린 사람의 프로필을 보여주는건데 이미 items detail에서 프로필을 만들어 봤음

items detail에 이미 프로필이 있음

바로 복붙해버림

프로필이 생겼음

좀 더 작아져야 할 것 같으니까 12 대신 10으로 함

이정도면 적당한 것 같음

margin-bottom도 5정도 줘볼까

3이 적당함

이제 질문글 차례임

이 디자인도 index 파일에 이미 있음

일단 태그가 있지

이것을 여기에 넣어주고 flex로 만듦

여기에 div를 먼저 넣어주고 붙여넣음

그런데 그냥 flex가 아니고 inline flex로 만들어줘야함

inline이 아니면 여기 보다시피 block이 돼서 화면 전체를 차지함

그러니까 inline flex로 해줌

flex기는 하지만 inline임

그리고 질문글은 만들어둔 것이 있으니까 이렇게 붙여 넣어줌

그리고 작성자랑 게시시간 부분은 다시 쓰지 않음

작성자는 프로필에 이미 나와 있음

여기 나온 사람이 작성자인 거잖아

그러니 넘어감

질문글도 완성했고 같은 것을 궁금해하는 사람이나 답변도 보여줘야함

이 div도 복사해서 질문 밑에 붙여 넣음

거의 다 됐음

원래 만들어뒀던 프로필에 padding이 없으니까 조금 추가해줌

좌우로 4정도 넣어줌

보통 그정도가 적당함

거의 다 됐음

여기서 새로 해야하는 것은 질문에 대한 이 답변 부분뿐임

그것을 하기 전에 이 textarea랑 button을 좀 꾸며줌

그런데 생각해봐

textarea랑 button도 만들지 않았어

여기 upload 페이지에서 textarea랑 button을 예쁘게 만들었음

여기서도 똑같은 모양을 쓸거니까 그대로 복붙하면 됨

예쁜 textarea가 만들어졌음

그리고 좌우로 padding을 넣어주는 것도 잊지 말자

부모 요소에 padding을 넣으면 되는데 자꾸 여러군데에 padding을 넣는 이유가 궁금함

왜 그러냐면 이 border가 끝까지 그어졌으면 좋겠어서 그럼

다른 화면에서 했던 것처럼 이렇게 padding을 넣으면 border가 여기서 끝나게 됨

이것이 별로 마음에 안 듦

그래서 border가 화면 끝까지 그어지도록 요소 각각에 padding을 따로 넣어줌

이것이 좀 더 멋있는 것 같음

그러면 textarea는 끝났고 이제 button을 복붙함

조금만 바꿔줌

0으로 할까

조금은 있어야겠음

2정도 줌

거의 다 끝났음

이제 답변 부분만 코딩하면 됨

그러면 끝임

질문에 "우리집 옆에 있는 만둣집이 최고에요." 라고 답변하는 부분은 끝났음

여기도 끝났고 프로필도 됐음

이제 무엇을 컴포넌트로 만들어야 하는지 콕 집어서 말할 수 있게 됐음

지금은 그냥 복붙을 많이 하고 있는데 나중에 코드를 정리해야함

어떤 요소를 컴포넌트로 만들어야할지 한눈에 보임

예를 들면 이 프로필, 배지, 질문은 컴포넌트로 만들어야함

textarea도 컴포넌트여야 할거고 버튼도 똑같이 생겼으니까 마찬가지임

작은 버튼이 큰 버튼 안에 들어가 있는 형태로 만들면 좋음

이 녀석을 구현하는데 집중해봄

그런데 그 전에 이 동네질문을 프로필 위로 올려야겠음

이것이 좀 더 나음

그리고 이거는 여기로 옮기고, 여기 border-top은 지워줌

이렇게 하는 것이 나은 것 같음

이제 진짜로 시작해봄

클론 코딩을 하다보면 가끔 이렇게 작은 차이점도 못 견디고 고치고 싶을 때가 있음

이제 질문이랑 답변을 마무리함

질문은 끝났음

답변만 처리하면 됨

먼저 가짜 이미지를 만듦

말했다시피 나중에 진짜 이미지로 바꿈

일단 이렇게 이미지를 만들어두고 클래스를 적어줌

그리고 이 p 태그들은 span으로 바꿔도 될 것 같음

얘네 둘만 바꿔줌

마지막 애는 아님

이제 어떻게 하느냐면 "2시간 전"에도 비슷하게 해줌

그럼 끝났음

이제 이 p 태그를 수정함

여기에는 별로 해줄 것은 없는 것 같음

다 됐음

이제 간격만 주면 됨

간격이랑 margin, padding을 줘야함

그러니 이 부모 요소에다가 이렇게 사용자 답변이 완성됐음

이렇게 답변을 늘려봄

잘 됨

사용자 답변을 마무리 지었음

잘 나온 것 같음

이정도면 만족함

다 했음

여기에 위쪽 margin을 줄 수도 있을 거 같음

그렇게 큰 차이는 아니겠지만 그래도 해봄

margin-top만 주면 정말 끝임

보다시피 컴포넌트를 만들어봤고 꽤 괜찮음

사람들이 게시글을 클릭하면 이런 화면을 보게 됨

그리고 여기에 답변을 달 수도 있음

"답변을 달아주세요!"라고 placeholder를 넣어볼까

## 5.8 Write

이제 write 화면을 만듦

write 화면은 사람들이 바로 이 버튼을 클릭하면 보여줘야 되는 페이지임

이 연필 모양 버튼을 눌러서 질문글을 남길 수 있음

진짜 간단한 페이지라서 40초 안쪽으로 끝날 것 같음

일단 community 폴더 안에 write 페이지를 만들어줌

이제 community는 페이지가 세개임

하나는 슬래시 community고 그것이 바로 index.tsx임

다른 하나는 주소에 id가 들어가는 것임

그리고 마지막은 write 페이지임

그렇게 세개임

Next.js의 라우팅이 너무 좋음

엄청 이해하기 쉬움

write 페이지에 들어가면 글을 쓸 수 있는 textarea가 있어야겠지

그거랑 버튼 하나만 있으면 끝남

그 두개만 있으면 끝남

community, write로 가야함(화면을 참고함)

그러면 write 페이지가 나옴

그런데 생각해봐

이미 write 페이지는 거의 다 끝났음

여기에 div 하나만 만들어서 다른 페이지처럼 4픽셀 좌우 padding을 넣어주고, div를 닫고 이제 이 div 안에 textarea랑 button만 넣어주면 끝임

나중에 navigation bar를 넣어줘야 하니까 위아래로 padding을 넣어줌

그것은 이 섹션의 마지막에 해볼거고 벌써 거의 다 됐음

textarea랑 button만 넣어주면 됨

그리고 그것은 이미 community post detail에서 다 만들어놨음

여기에 사람들이 다른 사람의 질문에 답변을 작성하는 기능이 있음

지금은 질문을 하는 상황이니까 placeholder만 "Ask a question"으로 바꿔줌

너무 비어보인다고 걱정할 필요는 없음

텅 빈 느낌이기는 함

그래도 모바일을 우선적으로 고려한 사이트처럼 보이게끔 나중에 여기에 뒤로가기 버튼이 있는 navigation bar를 넣음

그리고 이것은 Reply 대신 Submit으로 바꿈

사실 얘들은 div가 아니라 form 안에 담겨야 하는데 그것은 나중에 react-hook-form이랑 뭐 그런거 배울때 form을 다룰때 함

지금은 이렇게 둠

정말로 이대로 완성임

이것이 바로 write 페이지임

## 5.9 Chats

이번 영상에서는 chats 페이지를 만듦

chats.tsx 파일을 pages 폴더에 만들어놨는데 이것은 다음 영상에서 바꿈

그렇지만 지금은 이대로 씀

먼저 기본적인 것들부터 설정해줌

채팅 목록에도 padding이 필요할테니까 상하좌우로 padding을 넣어줌

그리고 여기에 전에 만들었던 프로필 컴포넌트를 가져와야 할 수도 있을 것 같음

여기에 있었던 것 같음

여기에 프로필 컴포넌트를 가져오면 아주 쉽게 만들 수 있을 것 같음

이렇게 나옴

이것을 chat 컴포넌트의 기반으로 사용할건데 몇 가지는 바꿔줘야함

예를 들자면 border-top은 필요 없음

view profile이라는 글자도 필요 없으니까 지움

view profile 대신에 상대방한테 보낸 마지막 메시지가 나오면 좋겠음

적당하게 그냥 "내일 오후 2시에 모퉁이에서 만나요"라고 함

그리고 크기도 바꿈

다 됐음

이것을 chat 컴포넌트로 쓰면 될 것 같음

그런데 보여주고 싶은 것이 있음

여기를 보면 우리는 지금 아주 흔한 패턴을 사용하고 있음

컴포넌트를 구분해주기 위해서 아래쪽에 border를 주고 있음

컴포넌트가 목록을 이루고 있으면 구분선이 필요함

그런데 여기를 보면 border가 화면 끝까지 그어지지 않고 있는데, 이것은 component를 감싸고 있는 container에 padding이 있어서 그럼

그러니 그 padding을 여기로 옮겨줌

그러면 이렇게 화면 끝까지 border가 그어지게 됨

조금 더 나음

이렇게 하면 문제가 생김

어떤 문제가 생기는지 보여줌

이 컴포넌트를 여러개 렌더링해봄

보다시피 컴포넌트를 많이 렌더링함

문제가 뭐냐면 일단 아까 말했다시피 border-bottom을 써서 구분선을 그어주고 있지

끝까지 다 잘 되고 있음

그런데 생각해보면 이 마지막 컴포넌트 아래에는 선이 없어야 하지 않을까

왜냐하면 첫 컴포넌트의 위에 선이 없는 것처럼 이것이 마지막 컴포넌트임

첫 컴포넌트 위에는 선이 없어야 하고 실제로 없음

그런데 마지막 컴포넌트의 아래에는 선이 생겨버림

이것을 해결하기 위한 두 가지 방법이 있음

하나는 "last" modifier를 이용함

이렇게 하면 해결됨

아래에 다른 컴포넌트가 있을 때만 선을 긋게 됐음

여기를 보면 밑에 아무것도 없으니까 선도 안 그어졌음

그런데 tailwind-css에는 이런 문제를 해결하는 아주 멋진 utility class가 있음

그러니까 이렇게 last를 사용하는 대신에 divide라는 클래스를 사용하면 됨

필요에 따라서 x축으로 구분할 수도, y축으로 구분할 수도 있음

divide-y-2를 넣어주면 아까랑 비슷하지만 살짝 더 굵은 구분선이 나타남

divide는 일종의 지름길이라고 보면 됨

보다시피 divide는 어떤 요소의 옆에 형제 요소가 있으면 border를 넣어줌

예를 들어 여기를 보면 이 요소는 아래에 아무것도 없으니까 아래쪽 border는 없음

divider를 더 두껍게 만들 수도 있음

2, 4, 8까지 가능함

이렇게 자동으로 만들어줌

알아서 다 해주니까 last-child 같은 것을 사용할 필요가 없음

이것이 너무 두껍다고 생각할 수도 있음

보다시피 이것이 최대한 얇게 만든건데 이것도 두껍다고 생각할 수 있음

그래도 이렇게 두께를 1px로 정할 수 있으니까 문제 없음

그러면 이렇게 1px 두께의 divider가 만들어짐

이제 이 컴포넌트에는 border-bottom이 필요 없음

다 지워줌

이렇게 변수를 쓸 수 있다는 것을 기억함

아주 좋은 기능임

2로 해도 우리 디자인에는 너무 두꺼웠음

그래서 이렇게 1px로 만들어줬음

이 멋진 기능을 보여주고 싶었음

그럼 chats 페이지는 끝났음

다 했음

다음 영상에서는 이 chat을 클릭하면 나타나야 하는 화면을 만들어봄

여기를 클릭하면 전체 대화가 나와야함

## 5.10 Chat Detail

이번 영상에서는 chats 파일을 수정해봄

두 URL을 만들고 싶으니까 이것의 이름을 바꿔줌

하나는 우리가 저번 영상에서 만든 것처럼 이런 식으로 나의 모든 채팅을 보여줌

슬래시 chats가 그 URL임

또한 chats 슬래시 1과 같이 채팅의 id가 담긴 URL을 만듦

이것을 chats 슬래시 index로 이름을 바꿔줌

파일 이름이 index이면 이것은 우리가 chats 경로로 갔을때 보여짐

이제 여기에 폴더가 하나 생겼을거고 그 안에 대괄호 id.tsx를 만들어줌

이제 이 파일은 우리가 이 경로로 이동했을때 보임

그리고 이미 chat detail을 위한 HTML을 준비해뒀음

이거랑 같은 HTML을 쓰고 싶다면 영상 위에 있는 링크를 눌러줌

그럼 HTML을 받아서 같이 styles를 입힐 수 있음

이것은 누군가가 남긴 질문 혹은 메세지이고 그 뒤에는 내 답장, 그리고 그 뒤에는 상대방의 답장임

이 메세지들이 좌우에서 번갈아가며 나오도록 해야함

오른편에는 우리가 보낸 메세지가 나오고, 왼쪽에는 상대방이 보낸 메세지가 나오도록 함

그리고 여기는 입력창인데 이것을 화면의 하단부에 떠다니게 만들고 싶음

그렇게 만듦

우리의 HTML은 그것으로 끝임

그 이상 특별히 해줄 것은 없음

이제 첫번째 채팅 버블을 만들어주면서 시작해봄

div 엘리먼트에 className을 부여함

즉 요소들 사이에 수평으로 공간을 주고 싶음

여기 마우스를 올리면 이것이 어떤 의미인지 알려줌 

이런 식으로 이 부분은 이미지가 들어갈 자리인데 그것은 나중에 넣도록 하고 지금은 그냥 div로 둠

이것을 원으로 만듦

우리는 이제 원을 만드는데 전문가임

원을 마음대로 만들 수 있음

그러면 이렇게 원이 만들어짐

이것이 우리 Avatar가 됨

이제 이것을 해봄

얼마에 파실 건가요?라고 적힌 div를 봄

이것은 p태그 안에 넣음

그것이 더 맞는 것 같음

여기에 className을 쓸건데 이 텍스트는 너비가 50%가 되도록 만들어줌

여기에는 1, 2, 3, 4 같은 숫자 혹은 상대적인 값들을 쓸 수 있음

그래서 1/2를 쓰면 그럼 얘는 50% 너비로 만들어줌

그리고 일종의 테두리를 그려주고 싶음

버블처럼 보이게 하고 싶음

padding과 border를 지정함

테두리의 색을 바꿔줘야함

어떻게 생각해

안녕하세요, 얼마에 파세요

이렇게 일종의 버블을 만들었음

items-center를 쓰지 말고 items-start를 써봄

이것이 더 나을 것 같음

그럼 우리는 다 끝났음

테두리 색을 한번 바꿔봄

이것이 마음에 듦

그런데 이러면 처음이랑 같은 것 같음

같은 것을 한번 더 해줌

같은 className을 다음 거에도 써줄건데 이것은 조금 다른 점이 있음

왜냐하면 순서를 뒤집어야 하기 때문임

그리고 I want 20,000을 p태그 안에 넣어줌

하지만 이것의 순서를 바꾸고 싶음

이 동그라미를 오른쪽으로 옮기고 싶음

그리고 HTML을 바꾸는 것을 원하지 않음

그냥 그러고 싶음

물론 HTML을 수정할 수도 있지만, 그냥 Tailwind를 이용해봄

flex의 방향을 지정함

className에 flex-row-reverse를 추가함

보다시피 이런 식으로 방향은 잘 바뀌었음

그런데 여기에 보다시피 여백이 사라졌음

그래서 무엇을 해야하냐면 여백도 reverse를 해줘야함

그러면 보다시피 버블과 아바타 사이에 같은 공간의 여백이 생김

그리고 위아래로 여백이 필요할 것 같음

여백을 추가해봄

이것이 우리의 메세지가 됨

이것을 봄

엄청 간단하게 할 수 있음

우리는 CSS의 기능인 reverse를 사용했음

또 우리는 space-reverse를 사용했는데 이것은 CSS의 기능이라고 할 수 없음

보다시피 이 className은 꽤 복잡하게 되어있음

고맙게도 Tailwind가 이것을 쓸 수 있도록 도와줌

이제 나머지 메세지에도 적용해서 어떻게 보이는지 확인해봄

상대가 나한테 다시 보낸 메세지는 reverse가 필요없음

여기에는 reverse가 필요없음

그럼 다 끝남

이것이 우리의 메세지 버블임

이런 식으로 보이게 됨

어떻게 생각해

이제 입력창을 만들어봄

입력창은 고정되게 함

입력창이 화면의 제일 아랫부분에 떠 있게 함

그렇게 만들기 위해서 max-w-md를 쓰는 이유는 최대 너비가 448px가 되도록 하고 싶기 때문임

어떻게 보이나 확인함

이것은 container의 역할을 함

그리고 이 div는 input과 화살표를 포함할건데, 이 화살표가 input 안에 있도록 하고 싶음

그런 효과가 좋음

이 컨테이너는 flex와 items-center 속성을 가짐

보다시피 화살표는 input 바로 옆에 있음

더 잘 보이도록 화면 사이즈를 조금 조정해봄

이것이 우리 input임

우리는 input을 어떻게 만드는지 앎

오랫동안 해왔음

둥글게 만드는 이유는 이것을 채팅창처럼 보이게 만들고 싶기 때문임

여기에서 input을 클릭하면 이런 식으로 보임

마음에 듦

나쁘지 않음

이제 오른쪽에 padding을 좀 줌

저 화살표가 들어갈 자리를 마련해야 하니까 얼마나 우리가 길게 쓸 수 있는지 봄

화살표는 여기에 위치하게 됨

이제 화살표의 container에 집중을 해봄

여기에서 className을 입력함

absolute이고 inset-y-0으로 위아래에 inset을 0으로 줌

거의 다 왔음

이제 화살표에도 className을 줌

만약 absolute를 사용할때 그 부모 (컨테이너)는 relative가 되어야 한다는 것을 명심해

그래서 여기에 relative를 부여함

이제 화살표를 마무리하면 이 화면은 다 끝나고, 다음으로 아마 프로필로 넘어가게 됨

text-sm, text-white를 써서 어떻게 보이는지 한번 볼까

rounded를 잘못 쓴 것 같음(오타를 수정함)

이것이 우리의 화살표임

우리의 input은 이런 식으로 보임

유저가 여기에 메세지를 입력하고 엔터를 누르거나 저 아이콘을 누르면 메세지가 보내짐

그러고보니 생각났는데 hover(포인터가 객체 위에 위치)와 focus에 대한 상태를 추가해야함

한번 해봄

마우스를 가져다대면 잘 작동함

커서를 pointer로 바꿔볼까

그런데 이것보다는 이런 식으로 span을 button으로 바꿈

이제 마우스 커서는 pointer 모양이 되고 이것을 누를 수 있음

그리고 여기서는 focus를 추가함

이렇게 클릭할 수 있는 예쁜 버튼을 만들었음

이 고리가 마음에 듦

위치가 너무 낮은 것 같음

그러니까 이것을 0으로 하지 말고 4로 바꿔봄

이것은 너무 머니까 2로 바꿔봄

그리고 임시로 이것을 엄청 많이 복붙해서 다른 메세지들이 많이 수신되었을때 어떻게 보이나 봄

이런 식으로 보이게 됨

어떻게 생각해

마음에 듦

녹화를 끄고 몇 개를 수정함

이것으로 끝임

이 결과물이 꽤 마음에 들고 같이 입력창을 만들어봐서 좋았음

## 5.11 Profile

이번 영상에서는 프로필 화면을 만듦

profile.tsx파일을 pages 폴더에 만들었고, 같은 HTML 파일을 쓰고 싶다면 영상 위에 있는 링크를 누름

이런 비어있는 div를 보면 나중에 사진이 들어갈 공간이라고 생각하면 됨

이제 해봄

먼저 해야하는 것은 header를 만드는 것임

사진, 이름, 그리고 프로필을 수정하기 위한 링크가 있을건데 수정 화면은 다음 강의에서 다룸

여기에 className을 써줌

3픽셀이 아니라 3단위임

w-16, h-16을 넣음

원이 생겼음

내 이름 혹은 유저의 이름, 폰트 크기는 보통으로 함

그리고 edit profile은 좀 작게 만듦

이제 프로필 부분을 잠시 닫아두고 동그라미 부분으로 다시 돌아가봄

다음 부분은 여기임

이것은 원의 컨테이너 역할을 함

원은 svg를 가지고 있고 글자도 포함되어 있음

이 스타일은 추가로 만들 두 개의 원에 공통적으로 적용됨

처음 하나는 영상에서 같이 해보고, 나머지 것들은 따로 해서 업데이트 해둠.

보다시피 쇼핑 카트 아이콘과 "판매내역"이 가운데에 있음

이제 여기에서 원을 만들어봄

원이 그려졌음

이제 해야할 것은 span을 수정하는 것임

그리고 이 span은 그냥 작은 텍스트가 됨

그러면 우리가 만든 원이 이렇게 보임

윗부분에 여백을 좀 줌

원이 이렇게 보일거고 이 전체가 링크임

여기를 클릭하면 우리는 판매한 제품 목록을 볼 수 있음

이것은 구매한 내역 그리고 이것은 좋아요를 표시한 목록임

여기서 잠시 녹화를 멈추고, 다른 원들을 우리가 했던 것처럼 바꿔줌

단순한 복사 붙여넣기임

이제 모든 아이콘들은 원형이고 똑같이 생겼음

이제 리뷰 부분을 만들건데 어렵지 않음

className을 써서 mt-12를 줌

이미지를 빠르게 한번 만들어봄

여기에 x축 방향으로 공간을 줌

그러면 이것은 아주 조금 멀어질거고, 리뷰 작성자의 이름을 작고 굵은 폰트로 바꿔줌

그럼 이것은 닫아도 됨

이 부분은 리뷰의 본문이 될텐데, 리뷰의 본문은 위쪽으로 여백을 가지고 있음

나쁘지 않음

이정도면 다 된 것 같음

이것이 우리의 리뷰임

원한다면 이 본문 글자는 작게 만들어도 좋음

이 영상은 이것으로 끝임

이것이 우리의 프로필 화면의 모습임

이제 사용자가 여기를 누르면 프로필을 수정하는 폼으로 이동하도록 만듦

이 버튼들은 누르면 각각 판매내역, 구매내역, 관심목록을 볼 수 있도록 해줌

그럼 끝임

그리고 이 세 화면에서 사용할 컴포넌트는 여기에 쓴 거랑 홈페이지에 있는 같은 것을 씀

왜냐하면 이 가로방향의 컴포넌트는 제품의 목록을 만들때 씀

그래서 난 이 세 화면에서 쓰기에 적합하다고 생각함

UI는 거의 다 완성했음

## 5.12 Bought, Loved and Sold

이번 비디오에서는 이 세 개의 화면을 끝내보려고 함

엄청 쉬움

사실상 이 가로형 제품 목록 화면을 복붙한거랑 같음

하지만 파일 이름은 바꿔줘야함

왜냐하면 프로필 화면에 세 개의 화면을 더 포함시켜줘야함

그래서 profile 파일의 이름을 바꿔줌

이것을 index로 바꿈

이 index는 profile 폴더 안에 위치함

다음과 같이 파일 이름을 변경함

profile/index가 만들어졌고, 이제 profile 폴더 안에 sold.tsx 파일을 만듦

그리고 profile 폴더 안에 bought 혹은 buy.tsx 파일을 만들어주고 여기서 love.tsx 파일도 만들어줌

각각 buy, love, sold의 세 가지 항목을 가지고 있고, 이들은 단순히 제품 목록임

그리고 이 안에 HTML을 만들어주면 끝임

그냥 전부 복붙하기만 하면 됨

sold에서 웹페이지의 첫번째 화면(index)에 있는 이것들을 만들고 싶음

말 그대로 이것이 세 개의 화면에 필요한 전부임

버튼들은 더 이상 필요가 없으니 지움

그러니까 만약 누군가가 sold로 이동하면 그들은 제품 목록을 보게 됨

다시 한번 잘 기억해 둠

이것은 가상의 데이터이지만 어플리케이션 상에서는 똑같이 보임

홈페이지에서 넘어오든 아니든 그냥 제품들의 목록일 뿐임

그래서 나는 이것을 복붙할거고 이것을 Bought라고 해줌

다 됐음

그리고 여기서는 Sold 대신에 Loved를 쓰는거고 파일 이름도 바꿈

buy 대신에 bought로 바꾸고 love는 loved라고 함

그럼 다 끝남

그리고 이것이 잘 작동하나봄

/profile로 가면 아직 우리가 만들어둔 프로필 화면을 볼 수 있음

그리고 /profile/loved로 가면 관심제품목록을 볼 수가 있음

나중에 네비게이션 바랑 제목을 여기에 만들어줌

/profile/bought을 확인함

/profile/sold을 확인함

## 5.13 Edit Profile

이번 영상에서는 프로필을 수정할 수 있는 화면(Edit Profile)을 만들어봄

우리가 필요한 입력창이랑 버튼 등등을 이미 다 가지고 있어서 아주 쉬움

다 가지고 있음

세 개의 input 이 필요함

이메일, 전화번호 그리고 다른 것, 예를 들어 이름을 위한 것이 필요함

사용자가 프로필에서 수정할 수 있음

당연히 사용자가 프로필 화면에서 프로필 사진도 바꿀 수 있어야함

그래서 전에 만들어 두었던 enter 화면에는 지금 필요로 한 것들이 다 있음

label이랑 input들을 가지고 있음

보다시피 이것을 복붙할거고 현재까지는 아무 문제 없음

나중에 코드를 다시 살펴보고 자주 사용되는 것들을 컴포넌트로 분리시킴

그럼 복붙을 안 해도 됨

그러면 재사용할 수도 있고 props에 대한 TypeScript 인터페이스를 만들어 줄수도 있음

하지만 당장할 것은 아니고 복붙하는 것만으로도 괜찮음

여기로 와서 enter 화면에서 만든 label이랑 input을 복붙함

이 label은 이메일 주소가 됨

그리고 이 부분을 지워주면 정상 작동함

여기 Email address가 나타남

이것을 이제 div 안에 넣음

그리고 이 div는 필요 없음

왜냐하면 여기에서 space-y-1을 입력하면 결과는 같아짐

이제 이 input의 이름(id)은 email이 될거고 htmlFor 값도 email이 됨

그리고 이것을 한번 더 복사해서 붙여넣어줌

이번에는 전화번호를 위해 만들어둔 것을 가져옴

일단은 그냥 복붙하고 이 부분들을 phone이랑 phone number로 수정해줌

그리고 이 div를 복사해서 여기에 붙여넣어줌

이제 Phone number input을 갖게 됐음

이것은 이미 만들어뒀던거고 이제 여기 간격을 좀 넣어줌

space는 child 사이에 수직 방향으로 간격을 추가해줌

이 child들은 input임

마지막으로 이 버튼을 만들어줘야함

여기로 복사해줌

그리고 Update Profile이라고 함

보다시피 버튼은 공간을 꽉 채우지 않음

이것이 default라 그럼

이런식으로 w-full을 넣어줄 수도 있음

block을 넣어도 똑같이 될 거같긴 한데 w-full을 써야함

이제 우리가 가진 이 근사한 form을 쓸 수 있게 됐음

이제 필요한 것이 뭐냐면 이것들 앞에 또 다른 div가 필요한데 이 div는 프로필 사진을 갖게 됨

그럼 우리는 그것을 변경할 수 있음

일단 다시 한번 사진이 담길 원을 만들어 놓음

이것이 사진이 들어갈 원임

이 옆에는 또 다른 div를 만들어줄거고 이것은 label이 됨

div가 아니라 label임

프로필 업로드 화면에서 쓴 것과 같은 것을 사용함

상품 등록 화면임

input을 label 안에 만들어줌

이 label은 버튼을 가짐

그런데 이것은 버튼을 가질 필요가 없을거 같음

그냥 type이 file인 input을 만들면 됨

그리고 이것을 숨겨줌

label에는 Change photo라고 적어줌

여기 나왔음

여기를 누르게 되면 type이 file인 input을 클릭함

여기 있음

그래서 여기를 누르면 이렇게 파일 선택 창이 나옴

엄청 간단함

꼼수지만 아주 좋은 꿀팁임

왜냐하면 type이 file일 때의 input은 엄청 못생겼음

원래는 어떻게 생겼는지 봄

예쁘지는 않음

이전 섹션 영상(Tour of Tailwind)에서 본것처럼 이 style을 바꿀수 있긴 함

이 버튼을 바꾸기 위한 방법들이 있지만 "No file chosen" 이 부분을 바꿀수는 없음

그래서 이 부분을 완전히 가려주는 것을 선호함

저것을 완전히 가렸고 label을 수정했음

이것을 버튼처럼 만들어봄

cursor-pointer가 먼저고 padding을 줄건데 우리가 항상 하던 것처럼 만드는 거 같음

더 필요한게 무엇일까

글자색을 회색으로 만들어줌

text-gray-700을 추가해줌

그리고 Change photo 대신에 Change만 씀

이것이 우리 버튼임

이제 htmlFor를 추가해줘야 됨

이것을 picture로 지정함

그리고 이것은 picture를 id로 가짐

우리가 필요한 모든 것을 끝냈음

여기로 와서 Change를 누르고 파일을 고름

accept 속성을 부여할 수 있는데 image/*라고 해주면 사진 파일만 받을 수 있게 해줌

그리고 이렇게 보이다시피 우리는 사진 파일만을 받을 수 있음

우리가 가진 input 중에 type이 file인 input에 다 넣어주면 됨

이것이 Edit Profile 화면의 전부임

보다시피 엄청 간단한데 근사함

## 5.14 Live

이번 영상에서는 live 스크린을 만듦

여기서는 사람들이 우리 웹사이트의 현재 활성화된 모든 live stream을 볼 수 있음

그래서 무엇을 할거냐면 나중에 대체될 이미지를 담고 있는 컴포넌트를 만듦

원형은 아니고 비디오의 썸네일이 됨

여기에 className을 입력함

비디오처럼 보이게 하기 위해서 aspect ratio(영상 비율)를 사용했으면 좋겠어서 비디오처럼 만들어주는 classname을 씀

바로 aspect-video임

aspect-video를 사용하면 보다시피 높이가 즉시 비율에 맞게 자동으로 조정이 됨

높이를 계산할 필요가 없음

아주 좋음

다시 한번 설명해줌

이런식으로 높이를 지정해 줄 필요가 없음

그냥 aspect-video를 쓰기만 하면 끝임

이것은 자동으로 비디오의 비율(aspect-ratio)을 주는데 16대9로 되어 있음

예전에 원을 만들때 aspect-square를 쓸 수도 있었음

왜냐하면 기억하다시피 원을 만들때는 먼저 정사각형을 만들어야 했음

그리고 rounded-full을 썼었지

이것이 원을 그리기 위한 class였음

먼저 정사각형을 만들고 rounded-full을 쓰면 원을 만들 수 있었음

이전에는 너비(width)와 높이(height)를 직접 지정해줬음

만약 높이를 신경쓰고 싶지 않다면 그냥 aspect-square를 쓰면 됨

이것은 엄청 멋진 CSS 속성임

이것은 Tailwind의 마법이 아니라 그냥 CSS의 속성일 뿐임

원래 우리가 만들어 두었던 것으로 돌아가봄

이것이 우리의 비디오가 될거고 여기에 기본값을 조금 추가해줌

이것이 우리 비디오가 됨

조금 둥글게 만들어볼까

그림자도 넣어봄

이러면 이미지가 조금 더 예뻐보이겠지

나중에 이 부분을 이미지로 바꿔줌

여기는 h3를 하나 만들어줌

이 h3는 라이브 스트림의 이름을 가질건데 라이브 스트림의 이름은 "Let's try potatoes"라고 해줌

이제 className을 추가해줌

이런 식으로 라이브 스트림이 보여짐

지금은 볼게 없지만 여러 개를 렌더할 수 있도록 함

이것을 할때 꼭 1, 2, 3, 4, 5로 안 해도 됨

그냥 1, 1, 1, .... 1, 1로 만들어 줘도 상관 없음

그냥 1, 2, 3, 4, 5를 씀

그리고 여기에서 map 함수를 사용해서 이러면 끝임

이것이 바로 라이브 스트림을 보여주는 방식임

key를 인덱스로 설정해줌

보다시피 간격이 좀 필요함

여기에 좀 넣어줘볼까

그리고 여기에 있는 font-medium을 없애도 될 거 같음

이것이 더 나아 보임

linter가 귀찮게 하지 않도록 이것을 좀 바꿔봄

이것을 꼭 할 필요는 없음

이 에러가 안 뜰 수도 있음

지금은 이렇게 바꿔둠

이제 border가 생겼음

이 x방향 padding을 컴포넌트로 옮겨봄

그러면 테두리가 양 옆으로 늘어남

그럼 다음 단계로 넘어가볼까

이제 index로 넘어가면 여기에 복사하고 싶은 버튼이 있음

이것을 복사해서 여기에 붙여 넣음

나중에는 새로운 라이브 스트림을 만들고 싶을때 이 버튼을 클릭하면 만들 수 있도록 함

그리고 방금 아래쪽에 있는 테두리를 제거해 줘야 된다는 것을 깨달았음

border-transparent를 입력함

테두리를 가지고 있는 것처럼 보임

이것은 컴포넌트로 만들어도 될 거 같음

이것은 원을 기반으로 prop을 바꿔서 만들 수 있음

아이콘을 props로 보낼 수 있음

어쨌든 이것은 컴포넌트가 됨

아이콘을 바꿈

라이브 스트림처럼 생긴 아이콘을 찾아봐야겠음

여기 hero icon에서 video 아이콘을 찾아봄

완벽한 거 같음

이것을 여기에다가 붙여넣음

몇 개를 좀 수정해야함

예를 들면 class는 className이 되어야함

이것은 제대로 작동하지 않을거니까 이 부분을 대문자로 바꿔줌

이런식으로 보이게 됨

맘에 듦

live 화면도 다 만들었음

다음 비디오에서는 여기를 누르면 새로운 스트림을 만드는 간단한 form이 나오도록 만듦

## 5.15 Stream

이제 파일 이름을 수정해야함

이름을 바꿔봄

live라는 폴더를 만들어줄거고 이 파일은 live폴더 안의 index가 됨

id라는 파일도 만들어줌

그리고 index파일의 내용을 id에 옮겨넣음

여기로 와서 붙여넣어줌

그리고 Live를 LiveDetail로 바꿔줌

아니면 StreamDetail로 할까

Stream이 더 나은 거 같음

그러면 Live가 있는 모든 곳을 Stream으로 바꿔줌

여기 있는 이 map을 지우고 이 부분도 지워줌

button도 지움

이것은 LiveDetail이었고 엄청 쉽지

왜냐하면 live로 갔을때 영상을 봄

다른 화면이 있는게 아님

여기를 클릭하면 비디오 페이지로 감

작동하는지 봄

/live/1로 가봄

보다시피 같은게 나옴

divide는 지워줌

그리고 padding을 양옆으로 4씩 줌

이것은 live였고 다 됐음

제목을 조금 더 키워봄

크기를 2xl로 바꿔줌

나쁘지 않은 것 같음

그리고 글자색을 좀 더 어둡게 바꿔주고 font에 semibold를 줌

이것은 LiveStream이고 잘 나왔음

아니면 text-center를 줘볼까

어떻게 되려나

Let's try potatoes가 가운데로 왔음

이 정도까지만 함

여기서 사람들은 LiveStream을 보게 됨

비디오 플레이어를 만들거고 클릭할 수도 있게 할거고 전체화면 기능도 만들어봄

그리고 여기에는 사람들이 메세지를 보낼 수 있게 채팅방 같은 것도 만들어봄

그러면 chats의 ChatDetail로 돌아가면 이미 말풍선(bubble)을 갖고 있음

이거 2개를 복사함

그리고 다시 원래로 돌아와서 제목 밑에 붙여줌

text-center는 그냥 지움

그래서 붙여 넣어준 다음 div를 닫아줌

그 다음에 이것을 좀 많이 복붙해줌

그래서 화면이 넘어가서 스크롤을 overflow 시킬건데 이렇게 하는 대신에 메세지를 스크롤하는 동안에도 동영상이랑 제목은 고정됐으면 좋겠음

이 메세지들의 container를 봄

보다시피 이 화면들은 우리가 이미 만든 요소를 복붙함

일단 내용을 다 닫아줌

padding top을 이렇게 주는 대신에 margin top에 10을 줌

그리고 높이는 일단 50vh로 해줌

이제 높이도 설정했음

그 다음에 대화내역을 볼 수 있게 스크롤에 overflow도 설정해줘야함

overflow-y-scroll이라고 써줌

이제 화면에 고정된 채로 이렇게 스크롤 할 수 있음

나쁘지 않음

그 다음에 mt-10은 그냥 py-10으로 바꿔줌

괜찮아 보임

그리고 이제 input을 가져올건데 ChatDetail 화면에서 만든 것을 가지고 옴

여기에 복붙해주면 됨

이제 input이 생겼고 꽤 괜찮아 보임

다 됐음

우리가 해냈음

이것은 Stream Screen이 어떻게 보일지에 관한거였음

## 5.16 Add Stream

이제 Screen의 마지막 부분을 만들고 끝냄

바로 LiveStream Screen을 만드는 것임

그리고 LiveStream Detail을 보여주고 싶은데 우리가 본 것과 비슷함

이런 식으로 LiveStream 목록을 보여줌

만약 /streams/1로 가면 우리가 item을 볼때하고 비슷함

/items/1로 가보면 Talk to seller하고 Similar items를 제외하면 매우 유사함

보다시피 엄청 비슷함

Live Stream이나 플랫폼을 만들때 제품을 판매하는 것이라고 생각하기 때문에 이렇게 했음

그래서 거의 비슷하게 만들려고 함

그리고 또 /items/upload에서 form에 Name이 없다는 것을 알게 됐음

그래서 Name을 추가해줬고 이것을 수정하는동안 Upload form하고 LiveStream을 만드는 form이 같다는 것을 알았음

차이점은 photo의 유무뿐임

제품을 등록할 때는 사진이 필요하지만 LiveStream은 동영상임

우리가 해야할 것은 그냥 Upload form을 복붙하는 것임

만약 코드를 원하다면 이 강의 영상 위쪽에 Github 링크를 보면 됨

이 div만 빼고 복사할건데 이 div에는 label이 있고 이 label은 photo 아이콘을 갖고 있기 때문임

그래서 upload.tsx 파일의 Upload form에서 그 div 밑의 모든 것을 복사해줌

그리고 약간 리팩터링(refactoring)도 해봤는데 왜냐하면 우리가 이런식으로 className을 쓰고 있다는 것을 알게 됐음

이렇게 className을 쓰고 있는 div를 갖고 있었음

className="my-5" 이런 식임

이것은 좀 일관성이 없음

우리는 이런 방식으로 많이 했었음

어떤 div는 위아래로 margin을 가지고 어떤 것은 그렇지 않음

그래서 margin top 같은 것을 추가하는 대신에 space를 줬었음

항상 까먹긴 하는데 space가 margin보다 좀 더 나은 방법 같음

margin을 추가하는 것보다 훨씬 나음

margin top을 추가하고 여기도 추가함

이쪽에도 넣는 것은 효율적이지 않음

그래서 여기에도 똑같이 넣어줌

이제 다시 이것을 복사해서 붙여넣음

이것은 Create Stream Screen이었음

보다시피 엄청 쉬움

그러면 이제 /streams/create로 가봄

이 화면에서 Stream 혹은 Product의 Name을 입력 받을거고 Price랑 Description도 입력 받음

그 다음에 Upload item 대신에 Go live라고 써줌

이제 다 됐음

이것이 만들고 싶었던 마지막 Screen 부분이었음

이제 정말 다 끝났고 Tailwind를 많이 연습해봤으면 좋겠음

완전히 끝난 것은 아님

다음 영상에서는 navigation bar를 만들어봄

layout component 같은 것을 만들건데 하단에 사용자에게 보여줄 navigation bar랑 상단에 보일 제목을 만듦

더 앱 같이 보이게 만들려고 함

웹사이트의 경우에는 이렇게 하면 안 좋아 보이기 때문에 어떻게 해야할지도 고민해야함

만약 화면을 크게 늘리거나 큰 모니터를 쓰면 보다시피 이것이 썩 좋아보이지는 않잖아

하지만 우리가 한 것에 대해서는 꽤 만족함

진짜 데이터로 빨리 해보고 싶음

엄청 재미있음

## 5.17 Layout part One

이 영상에서는 간단하게 좀 고쳐볼건데 우리의 앱이 큰 화면에서 매우 못생겨지는 문제를 해결해봄

그러면 _app.tsx 파일로 가서 Component를 div로 감싸줌

여기 안에다 넣음

이제 이 div에는 w-full이라는 className을 줄거고 가능한 많은 space를 확보함

max-w-lg(512px)라고 써줄거고 좌우에 margin을 auto로 주는 mx-auto를 이용해서 div를 중앙에 배치시킴

만약 div를 중앙에 놓고 싶다면 width를 설정해준 다음에 그리고 양쪽 margin을 auto로 설정해주면 됨

또 그 div는 block이어야 함

그러면 div가 중앙에 놓아짐

이제 이 화면을 늘려보면 보다시피 모바일 전용 웹사이트가 됐음

이 div를 조금 더 넓히고 싶다면 max-w의 lg를 더 크게 xl로 바꾸면 정한 한계까지만 커짐

이것은 하고 싶은대로 하면 됨

이것은 간단한 수정이었음

이런 수정을 한 이유는 이미 충분히 Tailwind를 사용했기 때문임

우리는 Tailwind로 많은 작업을 했음

반응형 디자인을 하고 싶지 않음

이런 디자인을 더 큰 화면에 적용시키고 responsive modifier를 쓰는 것을 녹화하지 않음

Tailwind로 반응형 디자인을 하는 것은 쉬움

하지만 이렇게 계속 하다보면 Tailwind UI 클론으로만 영상 10개를 찍어야함

이정도면 적당했고 이제 다음 섹션으로 이동함

이제 무엇을 할거냐면 모든 Screen에 적용되는 title과 navigation bar component를 만듦

원하던 것들임

navigation bar는 tab bar처럼 할건데 만약 이것이 실제 앱이었다면 Tailwind로 tab bar를 만들었음

그러면 이제 새 폴더를 만들어줄건데 이름은 components라고 해줌

안쪽에는 layout이라는 파일을 만들어줌

layout.tsx라고 써줌

div를 return 해줌

안쪽 부분은 나중에 만듦

먼저 props를 만들고 interface LayoutProps라고 써줌

이것은 typescript를 쓸때만 할 수 있음

만약 typescript를 쓰고 있지 않다면 30초만 기다려줌

그 다음에 children을 받아야하니까 이렇게 써주고 type은 React.ReactNode가 됨

다음에는 title을 받을건데 어떨 때는 안 받을 때도 있음

type은 string으로 해줌

돌아가기 버튼이 있다면 canGoBack도 받음

이것은 boolean이 됨

hasTabBar도 만들어주고 이것도 boolean이 됨

여기에서는 props를 받을건데 이 props는 title, canGoBack, hasTabBar, 그리고 children까지 방금 만든 것들을 받게 됨

type은 LayoutProps임

이제 어떻게 할거냐면 이 component를 모든 페이지에 넣음

그리고 페이지를 2개의 div로 감쌈

하나는 상단에 navigation bar고 children이 들어간 다음 하단에는 tab bar가 놓임

이 화면의 메뉴가 있는 tab임

tab bar는 항상 보이지는 않고 hasTabBar이어야 tab bar가 보이게 함

tab bar를 가질때만 보이게 함

그러면 이제 header부터 만듦

이 부분은 엄청 간단함

그냥 흰 배경만 만들면 됨

매우 간단함

이 div에서 className이라고 써주고 bg-white라고 함

w-full도 쓰고 text는 lg가 될거고 font-medium 그리고 위아래로 padding을 4씩 줌

그리고 고정되게 만들어야함

그러면 fixed를 써주고 이제 거의 다 된 것 같음

flex랑 items-center도 해줘야함

그리고 안에 있는 상단 bar로 title을 보내야함

그러니 title이 존재할 때만 여기에 title을 적어줌

만약 title이 존재하면 title 내용의 span을 보여줄거고 아니면 아무것도 보여주지 않음

그러면 이것이 어떻게 보일까

layout을 우리의 홈페이지에 적용해봄

홈페이지에서 layout을 적용해볼건데 pages로 가서 index 파일에 들어가봄

이 component를 모두 복사하고 Layout을 import함

그리고 이 component는 children이 됨

그리고 title은 "홈"이라고 함

저장해주면 새로고침이 됨

하지만 justify-center를 넣는 것을 깜빡했음

justify-center를 추가해줌

이것이 우리의 navigation bar임

조금만 더 작게 만듦

text를 다른 색으로 해볼까

orange라든지 마음대로 하면 됨

이제 이것을 모든 페이지에 적용시킴

하지만 보다시피 Screen의 위쪽 공간을 조금 띄워줘야함

왜냐하면 navigation bar에 가려져 있음

index에서 py를 너무 많이 쓰니까 그 대신에 layout.tsx에 있는 children에 py를 줘봄

일단 children을 div 안에 넣어봄

이렇게 div를 만들어주고 안에 children을 넣음

그리고 className을 써주고 py-10을 넣어줌

이 padding은 navigation bar나 tab bar가 밑에 있는지에 따라 바뀜

어떤 경우에는 tab bar가 있겠지만 항상은 아님

좋은 생각이 있는데 pt(padding-top)을 16px으로 줌

보다시피 홈에 있는데 첫번째 제품이 잘 보이고 있음

나중에는 children의 padding bottom을 어떻게 설정해야할지 고민해야함

navigation bar가 무엇인가를 가리지 않도록 해야함

왜냐하면 어떤 때는 tab bar가 있을거고 어떤 때는 없음

계속 해봄

이 Screen에서는 tab bar가 필요할 것 같음

이 경우에는 hasTabBar를 써줌

그러면 이제 tab bar를 가질거고 className이 조금 바뀌어야 할 것 같음

그리고 이것은 우리가 만들었던 className에 관한 utility function을 써볼 차례임

여기 있음

새 폴더 안에 새로 파일을 하나 만들어 줄건데 libs/ 안쪽에는 utils.ts라는 파일을 만듦

이 폴더는 잘 만들어졌음

이것은 파일이어야 하는데 utils.ts 파일을 만들어줌

이 function은 첫번째가 됨

export 해줌

여기에서 cls를 import 해주고 layout에서도 cls를 써줌

왜냐하면 tab bar를 가지면 Screen의 padding bottom이 달라져야 하기 때문임

한번 해봄

이것은 지워주고 cls를 써줌

첫번째로는 pt-16이 들어감

그 다음에는 hasTabBar가 있으면 pb-16을 줄거고 아니라면 아무것도 안 해줌

보다시피 이 경우에는 New iPhone 14하고 끝 사이에 간격이 있음

아주 좋음

이제 navigation bar를 해봄

이 navigation bar도 고정되어야 함

배경은 흰색이어야 하고 border 그런것들을 위쪽의 bar하고 똑같이 해줌

그리고 5개의 children을 가져야 할 거 같음

그러면 className을 써줌

다 똑같을 것 같으니까 그냥 복붙해도 될 것 같기는 함

어쨌든 fixed도 써주고 이 경우에는 bottom-0을 써줌

아래쪽 padding은 좀 더 크게, 위쪽은 작게 줘봄

어떻게 보일지는 잠시 후에 보게 됨

flex랑 justify-between도 써줌

그리고 items-center까지 씀

navigation bar가 생겼음

이제 span을 만들 시간임

nav 안쪽에 span을 5개쯤 만들어줌

span이 아니고 link임

우리는 link를 만들어야 됨

동네생활, 채팅방, Stream, Profile을 포함해서 5개의 link를 만들어야 함

먼저 span을 써주고 5개를 만들어줌

다음 영상은 이 Layout의 part 2가 됨

## 5.18 Layout part Two

기억해야할 것이 있음

element를 고정시켰다면

보다시피 max width를 따르지 않음

홈이 엄청 멀리 있음

max width를 따르지 않는데 왜냐하면 fixed된 것은 다른 평면에 있기 때문임

그래서 페이지와 똑같은 max width를 적용시켜야함

그러면 항상 중앙에 있게 됨

이제 다른 것을 해봄

아이콘을 여기에 추가해봄

nav에 필요할 것 같음

여기 nav 안쪽에서 아이콘 하나를 만들고 이것을 복붙해서 많이 만들어줌

첫번째 아이콘은 홈 화면에 관한 것임

div를 써주고 안쪽에는 svg 같은 아이콘이 있어야 하겠지

그리고 "홈"이라는 글자가 적힌 span을 써줌

그러면 Heroicons에서 svg를 찾아봄

하지만 먼저 className을 설정함

className이라고 써주고 flex랑 flex-column을 써줌

그러면 아이콘은 위에 단어는 밑에 있음

그리고 items-center를 써줌

그러면 둘다 중앙에 놓여짐

그리고 space-y-2도 써줌

Heroicons에서 홈 아이콘을 찾아봄

여기 home svg가 있음

여기에서 이 svg를 복붙함

홈을 만들었음

class는 className으로 바꿔줌

만약 이런 대쉬(-)가 있다면 지움

대쉬가 붙어있다면 지우고 뒤에 이어지는 첫번째 글자를 대문자로 바꿈

매우 중요함

원하면 svg의 크기를 조절할 수 있는데 width를 조절하든지 마음대로 하면 됨

이 정도가 괜찮은 것 같음

이제 홈이 생겼음

나중에는 Router를 써서 우리가 있는 화면에 따라 아이콘의 색을 바뀌게 함

그렇게 되면 멋짐

우리가 있는 위치에 따라 색을 바꿈

이렇게 4번 더 하면 됨

이것은 홈에 관한 거였고 하나는 동네생활, 하나는 채팅방, 다른 하나는 LiveStream, 마지막 하나는 Profile에 관한 것임

동네생활에서는 newspaper 아이콘을 가져옴

두번째 버튼으로 감

일단 첫번째는 닫음

두번째로 와서 이것은 newspaper 아이콘이어야함

이런 것은 나중에 바꿈

이것은 두번째 svg였고 닫음

이제 채팅방에서는 message 아이콘을 찾음

여기 있음

이 svg를 바꿈

LiveStream은 video camera 아이콘을 씀

이것은 닫아주고 이 svg를 camera 아이콘으로 바꿈

마지막 Profile에서는 user 아이콘을 씀

여기 있음

이 svg는 지우고 붙여넣음

이렇게 보임

이제 글자랑 이런 것들을 다 바꿔줌

이런 작은 문제들을 고친 뒤에 돌아옴

이제 다 해결했음

문제를 하나 발견했는데 밑으로 스크롤하면 보다시피 tab bar가 아직도 마지막 제품을 가림

그러니까 hasTabBar면 children의 padding bottom을 더 크게 해야함

children이 pb-24를 가지게 함

이렇게 하면 더 이상 가리지 않음

navigation bar랑 tab bar는 이제 아래하고 위 둘다 아무것도 가리지 않음

이제 다시 멈출건데 여기 밑의 모든 Screen을 이 component로 감싸줌

왜냐하면 나중에는 다른 Screen도 같은 component로 둘러싸야 할텐데 어떤 Screen은 돌아가기 버튼이 있을 수 있기 때문임

그러면 돌아가기 버튼을 만들어야함

만약 어떤 제품으로 들어간다면 여기에서는 tab bar가 필요없음

tab bar가 필요없을 거라고 생각함

하지만 돌아가기 버튼이랑 함께 위쪽에 title은 있어야함

이렇게 함

이 4개의 Screen을 layout component로 감싸고 난 후에 잠깐 멈춤

다시 돌아옴

각 페이지에 모두 적용시켜줬음

또 div를 Link로 둘러싼 뒤에 이 div를 a로 바꿨음

Link를 만들어서 이제 모두 연결되었고 클릭하면 모든 Screen으로 갈 수 있음

멋진 앱처럼 보임

이제 이것은 다 했고 다음으로 넘어갈 수 있음

마지막으로 하고 싶은 것은 layout을 수정하는건데 돌아가기 버튼을 눌렀을 때의 경우를 만듦

예를 들어 만약 우리가 홈페이지에 있고 어떤 제품을 클릭하면 /items/[id] 페이지로 가게 됨

이 페이지는 아직 layout이 없음

한번 적용시켜봄

여기로 와서 이렇게 Layout을 써줌

그리고 안쪽에 붙여넣어줌

제품 페이지로 가봄

보다시피 tab bar는 굳이 추가할 필요없고 title이 없는데 넣어줌

어떻게 생각해

title을 넣어야 할까

안 넣어도 될 것 같음

이렇게 이런 식으로 할 수는 있겠지만 잘 모르겠음

하지만 canGoBack은 넣어줘야함

canGoBack이 있으면 뒤로가기 버튼으로 그 전에 있던 화면으로 돌아갈 수 있음

그래서 canGoBack을 써줌

여기에서 canGoBack이면 span을 넣어줌

그러면 왼쪽 방향 화살표를 넣어줌

될 거 같은데 만약 아니면 null을 return함

canGoBack 아이콘이 생겼음

이제 이 span을 button으로 바꿔줌

onClick을 만들어주고 Next.js Router를 가져옴

useRouter라고 해줌

이 앞에 const router를 써줘야함

useRouter를 import해주고 onClick에서는 router.back()을 써줌

이러면 원래 있던 곳으로 돌아가게 해줌

그 다음에 button에 onClick을 써줌

이제 여기를 클릭하면 원래 있던 곳으로 돌아옴

하지만 이 화살표를 중앙에 놓고 싶지 않기 때문에 상단 bar의 className을 cls를 써서 조건부로 만들어봄

왜냐하면 화살표를 중앙에 놓고 싶지 않음

만약 title을 보여주고 있다면 title을 중앙에 놓을거고 화살표는 중앙에 나오게 하고 싶지 않음

그래서 cls를 써줌

그리고 조건부 className을 써줌

이 justify-center는 조건부의 하나여야 함

그래서 설정해줄건데 만약 canGoBack이 아니라면 justify-center를 해줄거고 그 외에는 아무것도 안 해줌

그러면 됐음

좌우로 padding을 10 추가해줌

이제 해봄

이렇게 보임

버튼을 누르면 다시 돌아가고 홈 화면에 있음

이제 해야 할 것은 상단 bar를 보여주지 않는 페이지로 가는 것임

하지만 돌아가기 버튼은 보여줘야함

이것은 반복적이고 그냥 복붙임

우리가 만들었던 페이지들로 가서 어느 화면에 상단 bar를 넣는게 맞는지, 안 넣는게 맞는지 결정하면 되고 그 중에서 몇몇은 그냥 돌아가기 버튼만 사용해서 만들면 됨

또 만약 이 화살표가 마음에 들지 않아서 다른 것으로 바꾸고 싶다면 너무 작으니까 Heroicons로 가서 arrow나 chevron을 찾으면 됨

여기서 chevron을 복사해서 이거 대신에 붙여넣어줄 수도 있음

하지만 잊지마

class를 className으로 바꿔줘야 하고 여기 밑의 width와 stroke-line 부분도 바꿔줘야함

이제 홈으로 가서 /items/1로 가봄

보다시피 조금 더 커졌음

더 나아보임

layout부분은 이제 끝났음

아무데나 가서 페이지를 layout component로 감싸줌

## 5.19 Conclusions

UI부분을 끝냈고 tailwind CSS도 다 했음

이것을 모두 했음

앞으로 오랫동안 UI에 대해서는 다루지 않음

다음 섹션에서는 백엔드를 설정할거고 진짜 데이터를 가지고 해봄

다시 UI로 돌아와서 진짜 데이터들을 갖고 해봄

이 섹션의 핵심은 엄청나게 신기하거나 재밌게 만드는게 아니라 최대한 연습을 많이 하도록 하는게 핵심이었음

우리가 이 섹션에서 정말 많이 연습했을거라고 확신함

장담할 수 있음

그래서 조금 지루하고 tailwind CSS가 짜증났을 수도 있음

우리가 한 것은 tailwind CSS밖에 없음

이제 tailwind CSS는 조금 쉴 시간임

그것이 다음 섹션이 됨

하지만 이 섹션을 마쳤다면 tailwind가 좀 더 편해졌을거라고 생각함

왜냐하면 계속 하면 할수록 더 익숙해짐

이제 무엇을 할거냐면 코드를 정리할건데 react component로 쪼갬

이 New iPhone의 component들을 복붙하는 대신에 쪼개진 각각의 react component에 넣음

여기의 question component나 chat component나 stream component나 여기 circle, profile, avatar 등등으로 쪼갬

가능한 많은 component로 나눔

typescript를 이용해서 props들의 type을 지정해줄거고 카메라에 대해서는 하지 않을건데 엄청 지루하기 때문임

하지만 대신에 이 영상 위쪽의 링크에는 남겨놨음

만약 어떻게 코드를 정리했는지 궁금하다면 component들을 복붙하면 됨

링크를 위에 남겨놨음

하지만 스스로 해보는 것을 추천함

이렇게 연습하는게 좋다고 생각함

그냥 평범하고 식상한 코드를 작성해보기도 하고 어떻게 className을 다루는지도 보고 리팩터링(refactoring)도 좀 해볼 수도 있음

여기에 border를 넣을 필요가 없을 수도 있음

divide className도 사용해 볼 수 있음

스스로 코드를 정리해보는 것은 정말 좋다고 생각함

코드를 혼자 써보고 정리해보면 개발자로서 성장시켜줌

그리고 자주 하는 실수들도 확인할 수 있음

확실히 리팩터링하면서 엄청 도움이 됐음

가지고 있던 나쁜 습관들에 대해 알게 됐음

이 영상 위쪽에 링크는 남겨놓음

input이나 textarea나 button 같은 component들을 찾아볼 수 있음

그런 것들을 링크에 남겨놓음

다음 섹션에서 봄

백엔드를 만들기 시작함

그리고 말했다시피 만약 지루했거나 tailwind CSS에 조금 짜증이 났어도 괜찮음

## 6.0 Before We Start

이번 섹션에서는 Prisma PlanetScale에 대해 공부할거고 이 어플리케이션에 적용할 serverless back-end 코드를 어디에 작성할지도 알아봄

Prisma PlanetScale에 대해서는 다음 영상부터 공부할거고, 이번 영상에서는 UI 부분의 최신 버전을 공유해주려고 함

지난 섹션을 공부했다면 이 UI가 아주 익숙함

Tailwind를 엄청 연습하면서 우리가 같이 만들어 본 UI임

지난 섹션을 공부하지 않았다면 아마 이 코드를 쓰고 싶음

같은 UI에서 진행하는게 좋을테니까 영상 위의 링크를 클릭해서 코드를 다운받도록 함

그리고 그 코드로 pages, libs, components 폴더를 변경하면 됨

components 폴더랑 libs 폴더는 새로 만들어야 할 수도 있음

pages 폴더는 이렇게 교체하고 components랑 libs는 새로 만들어서 이렇게 파일을 넣어줌

이렇게 하면 같은 UI를 쓸 수 있음

혹시 지난 섹션을 봤다면 무엇을 했는지 궁금함

코드가 엉망이라 정리를 좀 해야겠다고 말했었음

지금부터 알려줌

코드를 살펴보면서 두번 이상 반복된 컴포넌트를 확인하고, 두번 이상 반복된 컴포넌트는 components 폴더 내에 넣어줬음

button 컴포넌트도 만들었음

이것이 button임

button 중에서도 big button임

이거 말고 다른 button도 있음

이것은 small button임

둘이 똑같은 종류임

이것이 button 컴포넌트고 floating-button도 있음

floating-button은 여러 화면에서 사용함

세개 있음

지난 섹션에서 만들어 봤던 input 컴포넌트임

input 컴포넌트는 세 종류를 갖고 있는데 text는 이런 이메일 주소 같은 것임

phone은 이렇게 앞에 indicator가 달려 있고 전화번호를 숫자로 적을 수 있는 종류임

마지막으로 price는 여기서 사용됨

이것이 price input임

앞에 이렇게 표시가 돼 있음

뒤에는 통화(currency)가 적혀 있음

이것이 input 컴포넌트임

prop을 보면 아주 쉽게 이해할 수 있음

label은 바로 이것임

name은 input이랑 label에 설정하는 name 속성임

kind는 이미 설명했음

input의 세가지 옵션임

그리고 여기 이것은 input에 원하는 prop을 전달하고 싶을때 사용함

input에 password, number, email 같은 타입을 명시해야 할 수도 있고 required일 수도 아닐 수도 있음

그렇게 여러 종류의 prop을 보내야 할 수도 있으니까 여기에 이것을 써서 원하는 prop을 보낼 수 있도록 해 놓음

여기서 label, name, kind 외에 다른 prop들을 싹 포착해서 input에 전부 넣어줌

이것을 이용하면 이 컴포넌트를 사용할 때 원하는 prop을 바로 input에 넣어줄 수 있음

required, max-length나 password 같은 input의 type 등 다 보낼 수 있음

이것이 input 컴포넌트고 이것은 item 컴포넌트임

itemprops가 있고 item은 세로로 늘어서 있는 이것임

이것이 item임

iPhone 14라고 써 있는 이 props를 읽어보면 꽤 직관적으로 되어 있음

title은 이거고 id는 링크를 걸 수도 있음

보다시피 따로 설명할 필요없겠지

layout 컴포넌트는 전에 같이 만들어봤음

사용자가 어디 있는지를 확인하기 위해서 router를 추가했고 사용자의 위치에 따라서 layout의 링크에 색을 입혀줬음

이렇게 클릭하면 오렌지 색으로 변함

이것 때문에 router를 추가함

그리고 message 컴포넌트가 있는데 이것은 우리가 만든 chat message에 쓰임

이것을 message 컴포넌트로 만들어 줬음

이 컴포넌트에는 reversed라고 하는 prop이 하나 있는데 이것을 설정하면 message 컴포넌트를 뒤집게 됨

전송하는 message에는 reverse를 적용함

받는 message에는 reversed가 적용되지 않는 거고 보내는 message에는 reversed를 적용함

프로필 사진 부분이랑 말풍선(bubble)의 순서를 뒤집음

그리고 textarea 컴포넌트가 있는데 이것은 그냥 textarea임

바로 여기서 사용되고 있음

이것이 textarea임

보다시피 굉장히 간단함

label을 보내면 받을 수 있고 여기에는 textarea 태그가 있음

textarea도 마찬가지로 모든 prop을 받을 수 있도록 해줬고 여기 interface에도 적어놨음

원하는 prop을 무엇이든 보낼 수 있음

아까도 말했다시피 textarea가 required일 수도 있고 placeholder를 설정하고 싶을 수도 있고 그런 것을 처리하기 위해서 이렇게 해줌

모든 prop을 여기에 적지 않아도 되도록 쉬운 방법으로 만들어둠

코드가 어떻게 정리됐는지 궁금해 할 사람이 많을 테니까 지난 섹션을 공부한 사람들을 위해 알려줌

그래도 혹시 코드를 원한다면 Github에 올라가 있으니 그것을 쓰면 됨

pages랑 components 폴더를 바꿔주기만 하면 됨

이렇게 해서 지난 섹션을 잠시 정리해봤고 공식적으로 UI는 끝임

이제 진짜 데이터를 가지고 이 앱을 만들어봄

다음 영상에서는 Prisma에 대해 공부함

## 6.1 What is Prisma

이번 영상에서는 Prisma가 무엇인지, 어떤 점에서 좋은지 간단히 설명하려고 함

이미 Prisma가 무엇인지 알고 있고 좋아한다면 다음 영상으로 가서 셋업을 시작해도 좋음

이번 영상에서는 Prisma를 설명함

이전에 Prisma에 대해 들어본 적 없거나 들어봤지만 잘 모르는 경우, 이번 영상이 도움이 됨

Prisma는 Node.js와 Typescript ORM임

ORM은 Object Relational Mapping이라는 뜻이고 기본적으로 번역기의 역할을 한다고 생각하면 됨

자바스크립트 혹은 타입스크립트 코드와 데이터베이스 사이에 다리를 놓아줌

SQL 같은 데이터베이스 언어를 작성하지 않고 타입스크립트 코드만 작성하는게 더 좋기 때문임

타입스크립트를 사용하면 오류가 발생하기 전에 알려줌

알다시피 타입스크립트는 타입을 사용해서 문자열을 써야하는 자리에 숫자를 쓴다든가 하면 경고를 받게 됨

아주 편리한 기능임

Prisma를 사용하면 더 편리하게 데이터베이스를 사용할 수 있음

Prisma를 사용하기 위해서는 먼저 Prisma에게 데이터베이스가 어떻게 생겼는지를 schema.prisma라는 파일에 설명해줘야 함

이 파일에서 Prisma에게 데이터의 모양을 설명해줌

예를 들면 이렇게 데이터에는 id, title, content가 있음

string 타입인데 content는 required가 아니니까 이렇게 물음표로 표시해줌

published는 true 혹은 false일건데 기본적으로는 false임

author는 User 타입인데 User는 또 다른 model임

이렇게 Prisma에게 모든 데이터에 관해 서술해 줄건데 보다시피 거기에 사용되는 언어가 읽고 쓰기에 아주 편함

이렇게 Prisma에게 전부 설명해주고 나면, Prisma는 데이터베이스의 타입에 관해 알게 됨

아주 좋은 일임

Prisma가 이런 타입에 관한 정보를 알고 있으면 client를 생성해 줄 수 있음

client를 이용하면 타입스크립트로 데이터베이스와 직접 상호작용할 수 있음

Prisma에게 데이터베이스가 어떻게 생겼는지를 설명해주면 Prisma는 client를 생성해줌

그 client 안에는 필요한 모든 name이 들어있음

예를 들어서 데이터베이스에 User라는 model이 있다고 해봄

그런 상태에서 client를 만들면 자바스크립트 코드로 이렇게 prisma.users.create를 사용할 수 있음

이런게 자동적으로 생성될건데 Prisma에게 User라는 model이 있다는 것을 알려줬기 때문임

그리고 보다시피 자바스크립트 함수랑 객체를 이용해서 user를 생성할 수 있음

여기에서 타입스크립트를 통한 보호도 받을 수 있음

Prisma는 데이터베이스와 상호작용 할 수 있게 해줄 뿐 아니라 client라는 것도 만들어 주는데, client는 자동완성을 지원하기 때문에 아주 좋음

예를 들어서 이렇게 Prisma Schema에 User model이 있으면 이렇게 훌륭한 자동완성 기능을 사용할 수 있음

왜냐하면 Prisma가 User에 posts가 있다는 것도 알고, posts에는 title이 있다는 것도 알기 때문임

그리고 그 데이터를 가지고 우리가 할 수 있는 모든 작업들을 자동완성 해줌

이것이 Prisma를 사용하는 이유임

거기에 Prisma Studio라는게 있어서 더 좋음

Prisma Studio는 아주 휼륭한 Visual Database Browser인데 데이터베이스를 위한 관리자 패널(Admin Panel) 같은 것임

너무 근사함

지금까지 Prisma를 짧게 설명해봤고 사용해본 적 없다면 마음에 듦

말했다시피 이것은 번역기 같은 역할을 하고 데이터베이스에 연결이 됨

여기를 보면 PostgreSQL, MySQL, SQL Server, SQLite, MongoDB에 사용할 수 있음

MongoDB에도 사용할 수 있는게 엄청남

예전에는 안 됐었는데 이제는 지원하는 거 같음

우리는 MySQL을 사용할건데 PlanetScale이 MySQL과 호환되는 데이터베이스임

그래서 MySQL을 사용할건데 개발자로서 해야 할 일이 바뀌지는 않음

Prisma를 사용하면 그래서 좋음

Prisma를 사용해서 데이터베이스에 연결하면 큰 차이가 없음

지금까지 Prisma에 대해 알아 봤음

정말 훌륭한 툴이고 어서 시작하고 싶어서 두근두근함

다음 영상에서는 기본적인 Prisma project를 만들고, prisma client를 생성해서 이것이 얼마나 멋있는지 봄

## 6.2 Prisma Setup

Prisma 프로젝트를 만들어봄

하지만 그 전에 먼저 VS Code에서 prisma extension을 설치해줌

Prisma라고 검색해서 Prisma에서 만든 Prisma를 설치하면 됨

Syntax highlight 같은 기능이 있어서 prisma 파일을 좀 더 보기 좋게 만들어줌

formatting이랑 자동완성 기능도 있음

그러니 꼭 Prisma 확장 프로그램을 설치하길 바람

Prisma로 작업할 때 삶의 질을 팍팍 늘려줌

이제 시작할 준비가 됐음

두번째로 Prisma를 설치함

터미널로 와서 -D(Developer Dependency)로 Prisma를 설치해야함

터미널에 npm i prisma@3.8.0 -D 입력함

Prisma 설치가 끝나면 Prisma를 불러와야 하는데, 불러오는 방법에 익숙해질 필요가 있음

이렇게 prisma만 쓰면 안 됨

그렇게 하는게 아니라 npx prisma라고 해야함

prisma를 사용할 때면 항상 npx prisma라는 명령어를 사용함

지금 같은 경우에는 npx prisma init을 사용함

터미널에 npx prisma init 입력함 

보다시피 무엇인가를 했음

예를 들면 우리 application 안에 prisma 폴더가 생겼고 .env 파일이 생겼음

여기 설명들을 좀 읽어봄

첫번째로 여기에 나와있듯이 .env 파일에 있는 DATABASE_URL을 설정해줘야 함

Prisma를 사용하려면 데이터베이스가 있어야 함

Prisma는 번역기의 역할을 할 뿐이니까 데이터베이스가 필요함

.env 파일에 가 보면 postgresql DATABASE_URL이 있음

postgresql 데이터베이스는 안 쓸 거고 어차피 컴퓨터에 있지도 않음

데이터베이스는 PlanetScale에 있을거니까 이것은 나중에 바꿔줘야 함

제대로 된 DATABASE_URL을 넣어주는 것이 첫번째임

두번째는 schema.prisma 파일에서 datasource의 provider를 설정함

provider는 우리가 사용할 데이터베이스라고 생각하면 됨

Prisma는 provider로 postgresql, MySQL, SQLite, SQLServer 그리고 mongoDB를 지원함

이것은 지난 영상에서 얘기했던 부분임

우리는 MySQL로 바꿔줌

이것은 바로 해봄

prisma 폴더의 schema.prisma 파일로 가서 여기 provider를 mysql로 바꿔줌

이러면 Prisma를 사용할 준비가 끝났음

정말 이거만 하면 됨

이제부터 해야 할 것은 데이터베이스에 사용할 model을 만드는 것임

이제 진짜 데이터를 이용해야 함

그럼 이렇게 model User를 만들어줌

이렇게 하면 Prisma에서 model을 만들 수 있음

보다시피 아주 간단함

schema.prisma는 데이터베이스에 대한 모든 설명을 담은 파일이라 굉장히 중요함

어플리케이션의 핵심인 파일임

일종의 정수임

Prisma는 이 파일을 굉장히 자주 찾아 봄

변경점을 데이터베이스에 push 할 때도 사용하고, client를 만들 때도 사용함

그럼 좀 더 연습을 해봄 

User model에 ID를 넣어줌

ID의 타입은 Int라고 함

1, 2, 3, 4, 5, 6 같은 정수임

그리고 Prisma에게 이것이 ID라는 것을 알려줌

보다시피 여기 있는 이 @id parameter는 이것이 model의 id라는 것을 알려주는 역할을 함

유니크한 식별자임

그리고 기본적으로는 자동으로 증가하는(autoincrement) field로 설정함

이런 것들이 무엇인지는 나중에 알려줌

지금은 그냥 Prisma의 코드를 작성하는데 불편하지 않도록 익숙해졌으면 좋겠음

아주 간단함

지금까지 한 것은 Prisma에게 User에는 ID가 있다는 것을 알려줌

그리고 그 ID는 1, 2, 3, 4, 5 같은 정수임

@id를 써서 이 ID가 실제로 ID를 가지고 유저를 찾을 수 있게 유니크한 식별자라는 것도 알려줬음

그리고 따로 건들지 않으면 1, 2, 3, 4, 5, 6, 7, 8처럼 점점 증가함

이제 유저에게 전화번호를 가지고 로그인 할 수 있도록 전화번호도 있다고 해줌

그리고 전화번호도 Int 타입임

정말 큰 숫자를 다뤄야 하면 BigInt 타입으로도 설정 할 수 있는데 일단은 그냥 Int 타입으로 함

하지만 가끔은 유저가 전화번호가 아닌 이메일로 로그인 할 수도 있음

그러니까 전화번호는 required는 아님

무엇인가를 필수적이지 않은 선택적인 옵션으로 만들고 싶다면 물음표를 붙이면 됨

하지만 만약에 유저에게 전화번호가 있으면, 그 전화번호는 유일했으면 좋겠음

그러니 이렇게 @unique라는 것을 붙여줌

이메일에도 똑같이 해줌

말했다시피 전화번호로 로그인 할 수도 있고, 이메일로 로그인 할 수도 있으니까 둘 중 하나를 선택하면 됨

이메일은 이렇게 String 타입이고 required는 아님

유저에게는 이름도 있어야 함

String 타입임

그리고 이름은 required여야 할 것 같음

이름은 required임

보다시피 물음표를 붙이지 않았음

그리고 아바타도 넣어줌

아바타는 계정을 만들때 꼭 바로 설정할 필요는 없음

아바타는 처음에 undefined인 상태였다가 유저가 원할때 교체할 수 있으면 됨

이미지 파일 URL을 넣어야 하니까 String 타입임

보다시피 required가 아닌 선택사항으로 함

혹시 원한다면 required 여부를 기준으로 정렬해도 됨

크게 신경 안 쓰지만 원하는대로 해도 좋음

이제 model에 날짜를 좀 넣어주고 싶음

유저가 언제 생성됐는지 날짜를 넣고, 유저가 프로필을 수정하면 마지막으로 수정된 날짜가 언제인지도 알고 싶음

그러니 이렇게 createdAt을 만들고 타입은 DateTime으로 함

날짜를 나타내는 DateTime이라는 타입임

그리고 기본적으로는 now 함수를 사용함

now 함수는 새 유저가 만들어질 때 그 시점의 날짜를 가져와서 여기에 넣어주는 함수임

마지막으로 유저가 업데이트된 시점을 저장하도록 함

이렇게 updatedAt을 써줌

원한다면 At을 붙이지 않아도 좋음

그냥 created나 updated라고만 써도 됨

마음대로 해도 괜찮음

이 column은 마음대로 이름 지어줘도 됨

이것들은 다 마음대로 정해도 되는 이름임

반면에 이 column은 이름을 지켜줘야함

하지만 이쪽은 마음대로 이름을 지어도 되고 꼭 phone일 필요는 없음

이렇게 phoneNumber여도 됨

createdAt도 마찬가지로 DateTime 타입임

그런데 여기에 함수 비슷한 것을 써서 유저가 업데이트될 때마다 이 field가 변할 거라고 Prisma에게 알려줌

우리는 방금 Prisma에게 이 유저가 어떻게 생겼는지를 설명했음

아주 훌륭함

아직은 이렇게 설명을 한 결과를 볼 수는 없음

아직 데이터베이스가 없으니까 이렇게 설명을 해서 좋은 점이 무엇인지를 아직 알 수 없음

Prisma는 이 파일을 읽고 데이터베이스에 변경점을 deploy함

이 파일을 읽고 자바스크립트, 타입스크립트 Client를 생성해줄건데 아직은 데이터베이스가 없음

그러니 그것은 다음 영상에서 확인함

지금은 그저 Prisma로 작업하는게 얼마나 편리하고 이 언어가 얼마나 이해하기 쉬운지도, Prisma에서 model을 작성하는게 얼마나 쉬운지 알았으면 좋겠음

누구라도 이것을 읽으면 phone이 유니크하지만 required는 아니라는 것을 알 수 있음

createdAt이랑 updatedAt이 무엇인지도 한눈에 알 수 있고 보다시피 정말 이해하기 쉬움

이런 것들이 다 어디서 뜬금없이 나타났는지 궁금함

공식문서를 보면 다 나와있고 나중에 다 보여줌

그렇게 많지 않으니까 너무 걱정하지 않아도 됨

여기에 쓴 것들이 가장 유용한 것들이고 나머지는 나중에 살펴봄

당장은 이 정도면 충분함

보다시피 Prisma는 아주 간단하지만, 아직 Prisma의 진정한 능력은 보지 못했음

데이터베이스가 없어서 아직 Prisma의 진정한 힘은 보지 못했지만 그것은 다음 영상에서 함

다음 영상에서는 PlanetScale을 공부할건데 정말 깜짝 놀람

## 6.3 What is PlanetScale

이번 영상에서는 PlanetScale에 대해 알려줌

PlanetScale은 MySQL과 호환되는 serverless 데이터베이스 플랫폼임

그게 대체 무슨 뜻일까

데이터베이스 플랫폼이라는 것은 데이터베이스를 제공해준다는 의미임

serverless는 정말로 서버가 없다는게 아니라, 서버를 우리가 유지할 필요가 없다는 뜻임

serverless는 서버가 없다는 뜻이 아님

그것은 말도 안 됨

serverless는 우리가 서버를 관리하고 유지보수할 필요가 없다는 뜻임

PlanetScale은 데이터베이스를 제공해주는 데이터베이스 플랫폼임

그렇지만 이것은 사람들이 아마존에서 데이터베이스를 만들 때 사용하는 AWS의 RDS(관계형 데이터베이스 서비스) 같은 것은 아님

왜냐하면 거기서는 서버를 만들어야 하고, 적당한 크기를 설정하는 등 모든 것을 직접 해야함

예를 들어 백만 명이 데이터베이스에 연결되면 직접 scaling(확장)시켜 줘야함

좋은 소식이 아님

이런 serverless 플랫폼을 사용하면 그런 작업을 대신 해줌

안정성을 신뢰할 수 있는거고 굉장히 좋은 일임

그리고 여기를 보면 MySQL serverless database가 아님

MySQL-compatible serverless database임

거기에도 의미가 있음

MySQL을 쓰는게 아니라, MySQL이랑 호환되는 무엇인가를 사용해서 그럼

그것 덕분에 provider를 mysql로 설정할 수 있음

serverless고 MySQL이랑 약간은 다른 것을 사용하기 때문에 schema.prisma에서 약간 바꿔줘야 할게 있음

코드 두 줄만 바꾸면 잘 됨

그 코드가 무엇인지는 나중에 설명해줌

지금은 PlanetScale을 더 알아봄

여기를 보면 All power, no pain임

vacuuming, rebalancing, scaling을 할 필요가 없음

query planning도 없고 downtime도 없음

downtime이 없다는 것은 database가 꺼지지 않는다는 말임

많은 사람들에게 좋은 기능임

그리고 여기가 이번 영상에서 가장 중요한 부분인데 MySQL serverless platform이 아닌 이유는 Vitess가 있기 때문임

Vitess는 가장 scaling 기능이 뛰어난 오픈소스 데이터베이스임

Vitess는 유튜브를 scale하기 위해 구글이 만듦

Vitess는 대기업들이 규모에 맞게 MySQL을 scale하기 위해 쓰는 방법임

왜냐하면 scaling이 가장 까다로운 부분임

SQL 데이터베이스를 하나만 갖고 있어도 많은 유저들을 위해서 엄청 많은 일을 할 수 있음

서버가 하나만 있어도 정말 많은 일을 할 수 있음

하지만 매초 수백만 개의 쿼리를 처리해야 하고, 수십만 개의 연결이 들어오고 수만 개의 노드가 필요하다면 거기서부터는 정말 어려운 일이 시작됨

데이터베이스에 horizontal scaling도 해야하고 sharding도 해야하고, 데이터베이스가 맛이 가지 않도록 유지하고 조정해야 하는 등 많은 노력이 필요함

Vitess는 이런 일을 하기 위해 만들어졌음

보다시피 정말 많은 유명한 대기업들이 사용하고 있음

유튜브, 슬랙, 에어비앤비, 트위터 등등 이런 곳에 Vitess가 사용됨

그리고 보다시피 이것은 오픈소스 기술임

많은 사람들이 사용함

웹사이트에 가 보면 사이트가 썩 훌륭하지는 않지만 완전히 오픈소스임

이런 일을 하는 것임

MySQL을 horizontal scaling하기 위한 database clustering system임

무슨 뜻이냐면 MySQL을 좀 더 쉽게 scaling 할 수 있도록 하는 시스템임

보다시피 여기 Horizontal Scale이라고 적혀 있고 sharding이 가능함

High Availability는 복사본에 failure가 일어나도 괜찮도록 데이터베이스의 복사본을 저장해둔다는 의미임

어쩌면 데이터가 폭발해서 디스크가 날아가버리는 일이 발생할 수 있는데 그런 문제도 해결해야함

High availability라는 것은 디스크가 하나 죽더라도 괜찮도록 데이터를 여러 장소에 복사한다는 의미임

여기를 보면 MySQL 호환에 관한 것도 있음

코드를 많이 바꾸지 않아도 됨

그리고 이것은 Schema Migration이라는 정말 훌륭한 기술임

PlanetScale은 schema migration을 정말 훌륭하게 구현했음

더 살펴보기 전에 가격 정책을 한번 봄

무료 플랜은 한 달에 10GB의 저장 공간, 1억 번의 읽기, 1천만 번의 쓰기, 3개의 branch를 제공함

이거에 대해서는 있다가 얘기함

동시 접속은 1000개까지 가능한데 그렇게 자주 일어나는 일은 아닐 거고 매일 자동 백업도 됨

29달러를 내면 AutoScaling을 지원함

사람들이 많이 방문하면 자동으로 Scaling을 해서 더 많은 트래픽을 받을 수 있도록 함

계속해서 살펴봄

PlanetScale에서 가장 좋아하는 것은 개발자 경험(Developer Experience)임

PlanetScale은 아주 훌륭한 CLI가 있는데 마치 깃(github)을 사용하는 것처럼 쓸 수 있음

정말 훌륭한 점임

마치 깃을 쓰는 것처럼 데이터베이스를 다룰 수 있음

예를 들어서 데이터베이스에 user라는 새 model을 추가하려 한다고 해봄

모두가 사용하는 메인 데이터베이스를 직접 수정하는 대신 데이터베이스에 branch를 만들 수 있음

그 branch에서 schema도 바꾸고 새 model도 만들고 fields도 수정함

원하는 수정을 다 한 다음에 잘 된다는 생각이 들면 schema를 옮기는건데 그것을 알아서 해줌

이렇게 합칠 수 있음

여기를 보면 branch를 이용해서 schema 변경을 100% 자동으로 배포한다고 함

정말 좋은 기능임

깃을 쓰는 거랑 똑같음

development라는 branch를 만들고 준비가 되면 main branch에 합침

그리고 downtime 없이 배포하거나 migration함

사용자가 방해 받지 않도록 처리할 수 있음

그리고 말했다시피 아주 훌륭한 CLI도 있음

이렇게 pscale branch를 이용해서 branch를 만들 수 있고 여기서는 지웠음

pscale branch delete, pscale branch create가 있고 pscale branch list를 이용하면 branch 목록을 불러올 수 있음

정말 굉장함

Prisma랑 같이 쓰면 얼마나 훌륭한지를 알게 됨

지금까지 PlanetScale에 대한 설명이었고 마음에 들었으면 좋겠음

PlanetScale을 이용하는게 얼마나 쉽고 재밌는지 와닿았으면 좋겠음

데이터베이스를 직접 배포하고 유지보수하는 것은 고통 그 자체임

그리고 말했다시피 DX(개발자 경험, Developer Experience)도 끝내줌

그것이 어떤 의미인지 곧 알게 됨

그러면 바로 계정을 만들어봄(https://planetscale.com/)

Sign In을 클릭해서 계정을 만듦

계정을 만들거나 깃허브로 로그인하면 됨

## 6.4 Connecting to PlanetScale

계정을 만들고 로그인을 했으면 이런 화면이 보일 텐데 이것은 일종의 관리자 패널(Admin Panel) 같은 것임

하지만 관리자 패널을 깊게 살펴 보진 않을건데 PlanetScale의 최대 장점 중 하나가 CLI라고 생각함

제공하는 Command Line Interface가 아주 훌륭함

그러니 그것을 다운받아서 설치함

맥 유저라면 brew install planetscale/tap/pscale을 실행한 다음 mysql-client도 설치해주면 됨

리눅스 유저는 여기서 release를 다운로드 받고 이 명령어를 각각 실행시켜주면 됨

.deb를 받았다면 dpkg, .rpm을 받았다면 rpm 명령어를 실행시켜주면 됨

윈도우 유저라면 먼저 scoop을 다운받는 것을 추천함(https://scoop.sh/)

PowerShell에서 Set-ExecutionPolicy RemoteSigned -Scope CurrentUser 입력함

PowerShell에서 irm get.scoop.sh | iex 입력함

scoop은 콘솔을 통해서 쉽게 다운로드 받을 수 있게 해주는 도구임

먼저 scoop.sh로 이동해서 이 명령어를 실행해줌

PowerShell에서 Set-ExecutionPolicy RemoteSigned -Scope CurrentUser 입력함

PowerShell에서 irm get.scoop.sh | iex 입력함

그러면 이런 식으로 설치할 수 있음

우리는 여기 나와 있는대로 scoop bucket으로 planetscale의 bucket을 add 해주고 scoop install로 pscale mysql을 설치해주면 끝임(https://github.com/planetscale/cli)

터미널에 scoop bucket add pscale https://github.com/planetscale/scoop-bucket.git 입력

터미널에 scoop install pscale mysql 입력

scoop: command not found가 나오면 VS Code를 재실행 해봄

이렇게 설치가 끝났다면 VS Code에서 pscale을 입력해봄

이런 화면이 보인다면 잘 설치가 됐음

혹시 이런 화면이 보이지 않는다면, pscale이 잘 설치가 안 되면 영상 아래의 버튼을 클릭해줌

이슈 버튼을 눌러서 스크린샷과 함께 어떤 문제가 있는지 보여주면 최대한 도와주도록 함

혹은 친절한 노마드코더 식구들이 최대한 도와줌

그러니 여기서 잠시 영상을 멈추고 pscale CLI를 설치하도록 함

콘솔에서 pscale을 실행할 수 있게 되면 다시 영상을 재생시켜줌

설치가 끝났음

지금부터는 pscale을 살펴보면서 어떤 명령어들이 있는지 확인해봄

예를 들면 로그인을 위한 auth, backup, branch, completion과 데이터베이스에 연결하기 위한 connect와 데이터베이스를 다루기 위한 database와 그 하위에 다시 create, read, delete 등이 있음

region을 보기 위한 명령어임

어떤 region들이 있는지 확인해볼까

pscale region 그리고 추가 명령어는 list임

터미널에 pscale region 입력함

pscale region list라고 하면 됨

터미널에 pscale region list 입력함

보다시피 아직 로그인이 안 됐음

로그인을 먼저 함

터미널에 pscale auth login 입력함

이렇게 하면 브라우저가 열림

여기에 뜬 숫자가 터미널에 있는 숫자랑 같은지 확인만 해주면 됨

확인을 눌러줌

전부 준비 됐음

보다시피 여기 확인 대기 중(Waiting for confirmation)이라는 표시가 로그인 완료(Successfully logged in)로 바뀜

그럼 로그인이 된거고 이제 다시 pscale region list 명령어를 실행할 수 있음

터미널에 pscale region list 입력

그래서 region을 확인 해보면 보다시피 아시아가 있음

한국은 없지만 도쿄나 싱가폴도 충분히 가까우니까 괜찮음

유럽에는 더블린이 있음

나쁘지 않음

그럼 이 region에 데이터베이스를 만들어봄

바로 여기에 데이터베이스를 만듦

그러니 이 이름을 기억함

ap-northeast에 데이터베이스를 만듦

이제 pscale database 명령어를 확인해봄

터미널에 pscale database 입력

사용할 수 있는 옵션을 보면 create가 있음

터미널에 pscale database create 입력함

그러면 이런 옵션들이 보임

Flags랑 이렇게 사용 방법이 나와 있음

pscale database create 다음에 데이터베이스의 이름을 적어줘야 함

그리고 이렇게 region을 명명해줄 수 있음

터미널에 pscale database create carrot-market --region ap-northeast 입력

이렇게 하면 데이터베이스가 만들어짐

이제 관리자 패널로 돌아가 보면 보다시피 이미 데이터베이스가 만들어져 있음

물론 여기 이 New database를 클릭해도 됐음

사실 그냥 이거만 눌러도 데이터베이스를 만들 수 있음

이름을 넣어주고 region을 정해주면 됨

하지만 CLI 사용에 익숙해지는 것을 추천함

이 버튼을 누르는 것보다 더 생산성이 높아짐

CLI는 모든 것에 사용됨

이제 우리의 데이터베이스가 생겼음

굉장히 쉽지

엄청 간단함

이제 해야 하는 일은 URL을 구하는 것임

이 데이터베이스를 Prisma에 연결해야함

여기를 보면 데이터베이스에 연결하기 위해서 Prisma는 환경변수로 DATABASE_URL을 찾고 있음

그런데 지금 .env 파일의 URL을 보면 이렇게 돼 있음

좀 별로임

이것은 진짜 데이터베이스가 아님

우리는 postgresql 데이터베이스를 쓰지 않음

그러니 이것은 지움

지금부터 데이터베이스의 세계에서 경험한 것 중 가장 엄청난 거 하나를 보여줌

보통 데이터베이스 플랫폼에서는 데이터베이스를 하나 만들면 이렇게 암호를 생성함

엄청 많은 회사에서 Heroku나 AWS 같이 이런 방식을 선택함

그런 회사는 암호를 만들어 줌

그리고 그 암호를 관리해야 함

암호를 환경 파일에 집어 넣어야 함

그런데 그러면 암호가 장치에 저장됨

누구든 컴퓨터를 열어서 암호를 확인할 수 있음

그리고 혹시나 실수로 이 파일을 깃허브에 올리거나 하면 그냥 올라가버림

URL이 업로드 됨

그런 일은 좋지 않음

그래서 사람들이 보통 하는 방식이 뭐냐하면, 컴퓨터로 작업할 때 진짜 데이터베이스는 건드리지 않음

데이터베이스를 두 개 사용함

컴퓨터에서 서버를 작동할 수 있도록 가짜 데이터베이스를 사용함

그리고 실제 배포할 때 AWS나 Heroku를 이용함

이런 일은 강의에서도 여러 번 있었음

postgres를 다운로드 받고, postgres 서버를 작동시키고, postgres 데이터베이스도 만듦

postgres도 작동시킬 수 있어야 하고 실제 데이터베이스 서버를 만드는 식으로 강의했었음

그러는 대신에 PlanetScale에서는 컴퓨터랑 PlanetScale 사이에 일종의 보안 tunnel을 이용할 수 있음

암호나 그런 것을 알 필요도 없어짐

아주 좋은 기능임

다시 말하지만 MySQL을 다운 받고 설치하고 실행할 필요가 없음

그리고 두 개의 데이터베이스를 만들어서 하나는 컴퓨터 용으로 다른 하나는 PlanetScale용으로 관리하는 방식을 쓸 필요도 없음

그리고 .env 파일에 암호를 저장해야 할 필요도 없음

굉장히 훌륭한 점임

그럼 어떻게 해야 암호 없이 컴퓨터와 PlanetScale 사이에 보안 연결을 만들 수 있을까

그 답은 CLI에 있음

이렇게 pscale이라고 입력해 보면 보다시피 database와 보안 연결을 만들어 주는 connect 명령어가 있음

한번 해 봄

터미널에 pscale connect carrot-market 입력

그리고 실행하면 연결이 됐음

엄청 간단하지

데이터베이스에 연결을 해본 적이 있다면 그게 얼마나 까다로운지 앎

host도 복사해야 하고 port도 복사해야 하고 username, password 등 모든 것을 다 복사해야 함

그런데 이것을 봄

이렇게 pscale connect만 치면 이런 URL이 나옴

이 URL은 PlanetScale 서버랑 연결됨

진짜 엄청나지

이제 우리가 해야 할 일은 이 URL을 복사해서 이 연결은 끊지 말고 이 콘솔은 닫으면 안 됨

최소화만 해 놓고 새 콘솔을 연 다음 이 콘솔을 통해서 PlanetScale이랑 연결되어 있는 거니까 닫으면 안 됨

닫지 말고 연결을 끊지 마

이 URL을 복사해서 여기에 넣음

.env 파일에 DATABASE_URL="mysql://127.0.0.1:3306/carrot-market" 입력 

이렇게만 해주면 끝임

이렇게 하면 PlanetScale이랑 연결됨

이런 개발자 경험이 얼마나 놀라운지 알았으면 좋겠음

콘솔로 데이터베이스를 만들었고 암호도 모른 채로 연결에 성공했음

컴퓨터랑 PlanetScale 사이에 secure tunnel만 만들어줬음

암호나 다른 어떤 것도 복사할 필요가 없었음

얼마나 편리한지 몰라

중요한 것은 이것이 끝이 아님

이제부터는 Prisma를 이용해서 PlanetScale에 변경점들을 push하는 방법을 알아볼건데 정말 생각도 하기 힘든 방법임

그 전에 아주 잠깐 schema.prisma 파일에서 바꿔줘야 할 부분이 있는데 그것은 다음 영상에서 해봄

## 6.5 Push To PlanetScale

이번 영상에서는 이 model을 데이터베이스에 push 해봄

Prisma는 두 가지 목적을 위해서 이 파일을 살펴봄

하나는 model들을 데이터베이스에 push하고 SQL migration을 자동으로 처리하기 위함임

다른 하나는 데이터베이스와 상호작용하기 위해 client를 생성하고 그 client에 자동완성으로 타입들을 추가함

이 두 가지는 Prisma가 이 파일을 살펴본 뒤에 일어나는 일들임

거의 다 왔음

필요한 것은 전부 준비 됐음

이렇게 pscale connect carrot-market 명령어를 통해서 PlanetScale과 연결했고, URL을 얻어서 컴퓨터랑 PlanetScale 사이에 보안 tunnel을 만들었음

schema.prisma 파일은 환경변수에 있는 DATABASE_URL을 찾고 있음

그리고 우리는 환경변수 파일에 PlanetScale과 연결되는 보안 tunnel의 URL을 넣어줬음

거의 다 됐지만 코드를 조금 바꿔줘야 함

사실 두 줄만 추가해주면 됨

이것은 전에도 말했지만 PlanetScale이 MySQL과 호환되는 서버 플랫폼이라서 그럼

PlanetScale은 MySQL 서버 플랫폼이 아님

이것은 얘들이 MySQL이랑은 몇 가지를 다르게 처리한다는 뜻이고, 그 이유는 전에도 말했다시피 PlanetScale이 기본적으로 Vitess를 사용하기 때문임

그리고 Vitess는 MySQL-Compatible 데이터베이스임

MySQL이랑은 아주 약간 다름

호환되지만 약간 다름

Vitess는 대량의 connections, tables와 다양한 서버들을 scaling 할 수 있음

그게 Vitess의 특별한 점이지만 어쨌든 Vitess는 MySQL이 아니기 때문에 MySQL은 하지만 Vitess는 하지 않는 몇 가지가 있음

그 중 하나는 foreign key 제약임

그게 무엇인지 이제부터 설명함

Users DB가 하나 있다고 가정해봄

그리고 그 데이터베이스에 id가 1이고 이름은 nico인 사용자가 있다고 함

그리고 Comments DB가 있는데 거기에 새로운 댓글을 하나 추가한다고 생각해봄

그러면 아마 이런 식임

새 댓글의 id는 1이고 내용은 wow!라고 함

그럼 이 댓글과 사용자를 연결해야 함

작성자가 누구인지 알아야 함

그래야 말이 됨

그러면 이 새 댓글은 id가 1인 작성자에 의해 생성된 거라고 해줌

그럼 이 경우에 데이터베이스는 여기 이 숫자가 Users DB에 있는 사용자의 id라는 것을 앎

이러면 서로 연결이 됨

다시 봄

Users DB 에는 id가 1인 사용자가 있음

아무 문제 없음

그리고 Comments DB에 새 댓글을 추가할건데 댓글의 내용은 wow!임

댓글의 작성자가 누구인지 알고 싶기 때문에 이 댓글을 작성한 사용자가 Users DB에 있고 그 id는 1이라고 알려줌

말하자면 이 사용자가 대체 어디에 있는지 주소를 알려줌

그러면 데이터베이스는 이 사용자를 호출해서 정보를 볼 수 있음

그럼 나중에 id가 1인 댓글을 찾고 싶다면 데이터베이스가 id는 1이고, text는 wow!이고, 작성자가 nico인 댓글을 찾아줌

여기에 실제로 nico를 저장하는 것은 아님

그냥 사용자의 id가 1인 것만 알려줌

사용자 객체의 주소를 알려줌

나중에 댓글을 검색하면 이런 댓글을 받아 볼 수 있음

왜냐하면 데이터베이스가 이 id를 가지고 어디를 찾아봐야 할지 알고 있음

SQL이나 postgresql의 세계에서는 여러 것들을 연결하기 위해 항상 이런 방식을 사용함

이것이 foreign key라는 것임

데이터베이스에 사용자의 id만 저장하면 데이터베이스가 자동으로 이것이 사용자 데이터베이스의 정보라는 것을 앎

그래서 댓글을 찾을 때 id가 여기 있으니까 사용자도 같이 찾을 수 있게 됨

어려운 이야기는 아님

그런데 예를 들어서 이렇게 댓글을 추가하려고 하는데 이 댓글의 작성자의 id가 이렇게 5라고 해봄

이것은 평범한 SQL이나 postgresql에서는 제대로 작동이 안 됨

왜냐하면 여기서 지금 댓글의 작성자의 id가 5라고 했는데 데이터베이스는 이 댓글 정보를 저장하기 전에 사용자 데이터베이스에서 이 작성자에 대한 정보를 찾아 봄

작성자 정보랑 같이 댓글을 저장하려면 그 작성자가 존재하는지를 확인해야 하니까 생각해보면 당연함

그러니까 이렇게 작성하면 평범한 MySQL이나 postgresql 환경에서는 제대로 작동을 안 함

왜냐하면 그런 관계형 데이터베이스 환경에서는 이렇게 foreign key를 생성하고자 할 때 그 키가 반드시 존재해야함

하지만 PlanetScale에서는 이것이 아무 문제없이 작동됨

이것이 되는 이유는 뭐냐하면 MySQL과 Vitess의 차이점 때문임

PlanetScale이 데이터베이스로 사용하는 Vitess는 중요하니까 잘 기억해야 함

Vitess는 Scalability에 특화돼 있음

Vitess는 데이터베이스를 잘게 쪼개서 여러 서버에 분산시키는데에 특화되어 있음

조금 다른 방식으로 scale함

그러니까 이런 경우에 Vitess는 댓글을 생성하기 전에 사용자가 존재하는지 확인하지 않음

이런 코드가 아무런 문제없이 작동함

그 이유는 Vitess가 foreign key constraint(제약)을 지원하지 않기 때문임

그러면 개발자가 조심해서 존재하는 사용자로만 댓글을 생성하는 것도 한 방법임

하지만 조금 도움을 받는 것도 좋음

보통은 데이터베이스에게 도움을 받음

보통은 MySQL이나 postgresql에게 도움을 받지만 Vitess에게는 그런 도움을 받을 수 없음

하지만 Prisma를 이용해서 도움을 받을 수는 있음

이런 식으로 작성해도 데이터베이스가 오류를 일으키지 않는다는 것은 알았지만 그게 좋은 일은 아님

오류를 내서 멈춰주는게 좋음

데이터베이스가 이런 코드를 제한하지 않으니까 Prisma가 확인하게 함

확인 작업을 추가할건데 그게 데이터베이스 측에서 일어나는 것은 아님

확인 작업은 Prisma 측에서 일어남

Prisma가 확인해줌

코드 두 줄만 추가하면 됨

지금 우리가 하려는 것은 이렇게 한 객체가 다른 객체에 연결된 상태를 생성하려고 할 때, 그 연결을 받는 객체가 존재한다는 것을 보장함

그것을 하려고 함

일반적인 SQL이나 postgresql 환경에서 이렇게 하면 오류가 발생함

존재하지 않는 작성자로는 댓글을 작성할 수 없기 때문임

하지만 PlanetScale의 Vitess에는 그런 제한이 없기 때문에 아무런 오류가 생기지 않음

하지만 오히려 오류가 도움이 되기 때문에 그것을 설정해줌

데이터베이스에게서 도움을 받을 수 없다면 Prisma를 이용해 도움을 얻음

지금부터 바로 그것을 해봄

그럼 여기 client에서 previewFeatures라는 베타 버전 옵션을 설정할건데 막 미완성이거나 하지는 않음

어느 정도는 완성 됐음

그리고 우리가 preview하고자 하는 것은 referentialIntegrity임

이것이 무슨 뜻이냐면 다른 객체에 연결될 때 그 객체가 존재하길 바란다는 것임

이렇게 previewFeatures 옵션을 설정했고 그 다음에는 데이터베이스에 이렇게 써서 이 작업은 prisma가 할 거라고 해줌

이러면 다 됐음

이것을 하지 않는다고 해서 아무것도 안 되고 그러는 것은 아님

반대로 아무 문제없이 다 잘 됨

하지만 데이터베이스가 도움을 주지 못하는 부분에서 Prisma가 referentialIntegrity 확인을 통해 도움을 줄 수 있게 함

전부 준비 됐음

이제 우리가 만들어낸 결과를 마주할 시간임

이제 이 schema를 PlanetScale에 push함

이것을 기억해야함

아주 중요함

이렇게 pscale connect를 실행시키지 않으면 아무것도 안 됨

데이터베이스랑 보안 tunnel로 연결되어 있어야 함

그러니까 잊지 않고 pscale connect를 실행시켜 두도록 하고, pscale connect를 통해서 얻은 URL을 .env 파일에 잘 넣도록 함

이렇게 mysql로 시작한 다음 URL을 넣고 그 다음 데이터베이스의 이름이 잘 오도록 함

똑같은 상태라면 이제 모든 준비가 끝났음

바로 가봄

터미널에 pscale connect carrot-market 입력하고 다른 터미널을 열어 npx prisma db push라고 입력

보다시피 .env 파일에서 환경 변수들을 불러오고 있음

MySQL 데이터베이스를 잘 찾아서 연결하고 있고 데이터베이스가 schema랑 잘 동기화됐다고 함

그리고 보다시피 Prisma Client가 생성됐다고 나옴

이것은 다음 영상에서 살펴봄

지금은 일단 PlanetScale로 돌아감

PlanetScale로 돌아가서 데이터베이스에 어떤 일이 생겼는지 확인해 봄

여기 branches를 클릭해 보면 이렇게 main branch가 있고 여기를 클릭함(https://app.planetscale.com/kko0831/carrot-market)

그리고 schema를 확인해 봄

데이터베이스의 모양을 알려줌

여기 Refresh schema를 누르면 schema가 생성 중이라고 나오고 이런 화면이 나옴

우리가 여기에 갖고 있는 SQL의 버전이 나옴

보다시피 성공적으로 연결 됐음

Prisma가 이것을 이해함

그리고 그것을 PlanetScale에게 잘 번역해줬음

PlanetScale 데이터베이스에서 우리의 User table은 이렇게 생김

잘 따라왔다면 이렇게 잘 작동함

다 만들어졌음

컴퓨터에 있는 Prisma와 PlanetScale 사이에 직접적인 연결이 생성됐음

schema도 성공적으로 업데이트 됐음

다음 영상에서는 client에 대해 살펴봄

콘솔을 보면 이렇게 node_modules 안에 Prisma Client도 생성했으니까 다음 영상에서 살펴봄

## 6.6 Prisma Client

프리스마 써보니까 괜찮지

아주 좋은 기술임

이런 식으로 스키마를 정의하고 npx prisma database push를 하면 끝임

알아서 PlanetScale 데이터베이스를 수정해주고 sql 같은 것들을 자동으로 만들어줌

다 알아서 됨

우리가 할 것은 없음

우리는 데이터가 어떤 구조를 가질지 작성해주면 됨

이것만 해도 굉장한데 프리스마 스튜디오라고 하나 더 소개해줄게 있음

터미널에 npx prisma studio를 입력함

보다시피 엄청 대단한 데이터베이스 관리자 패널을 볼 수 있음

이것을 먼저 보게 될텐데 프리스마 스튜디오가 schema.prisma를 읽어서 User model이 있다는 것을 알고 User를 관리할 수 있는 패널을 준비해줌

그냥 사용할 수 있음

User를 클릭하면 보다시피 여기서 새로운 User를 추가해 볼 수 있음

그리고 User가 가지는 데이터 필드들을 확인할 수 있음

id를 확인해봄

이것은 숫자여야 하니까 '#'을 확인할 수 있음

phone은 숫자여야 하지만 선택적인거니까 '#?'를 볼 수 있음

email은 문자열에 선택적인거니까 'A?'를 볼 수 있음

name은 문자열, avatar도 문자열, 선택적임

createdAt과 updatedAt은 날짜 형식임

이렇게 데이터를 다룰 수 있는 관리자 패널이 공짜로 생김

나중에 model을 추가하면 다른 것들도 확인할 수 있음

지금은 첫번째 유저를 만들어봄

물론 사용자들이 이런 식으로 user를 만들지는 않음

관리자가 이렇게 할 수 있음

얼마나 대단한지 보여줌

Add record를 클릭하면 phone은 비워두고 email은 nico@nomadcoders.co으로 해봄

name은 니꼬, avatar는 필요없음

createdAt도 추가할 필요 없음

updatedAt은 이미 추가되어 있음

원한다면 createdAt에 날짜를 추가할 수 있음

이거랑 같은 날짜를 넣어봄

똑같이 넣고 'Save 1 change' 클릭하면 저장하는 중임

보다시피 새로고침을 해보면 새로고침을 하는 중임

데이터베이스에서 User를 확인할 수 있음

데이터베이스에 user가 생겼지

보다시피 schema.prisma 파일은 정말 강력함

프리스마가 확인해서 PlanetScale 데이터베이스를 수정해줄거고 정말 좋은 관리자 패널도 제공해줌

그리고 프리스마가 prisma client라는 것을 제공해줌

이거에 대해 얘기해봄

다시 한 번 얘기해줌

프리스마는 데이터베이스를 수정해주고 공짜로 이용할 수 있는 관리자 패널을 제공해줌

그리고 client라는 것을 제공해줌

우선 이 client를 초기화 해줘야함

이것을 위해 libs 폴더 안으로 와서 client.ts라는 파일을 만듦

그 전에 client 설치부터 해봄

터미널을 열고 npm install @prisma/client@3.8.1 입력함

보다시피 여기서는 -D 옵션을 사용하지 않았음

왜냐하면 백엔드에서 이 client를 직접 사용함

이것은 development dependency가 아님

우리가 서비스에서 직접 사용할 dependency임

그러면 @prisma/client에서 PrismaClient를 import 해봄

그리고 export default new PrismaClient함

이것만 하면 prisma client를 만든 것임

이제 이 파일에서 PrismaClient를 import 해서 자동완성 기능을 가진 PrismaClient로 데이터베이스에 대화를 걸도록 만듦

우리가 했던 것을 다시 봐보면 npm이 아니라 npx prisma db push임

이것을 하면 client가 생성되었다는 메세지를 볼 수 있었음

그러면 다시 해봄

이번에는 터미널에 npx prisma generate를 입력 해봄

그러면 client를 생성했다는 메세지를 볼 수 있음

이것을 꼭 다시 할 필요는 없지만 그래도 해봄

터미널에 npx prisma generate 입력

보다시피 node_modules/@prisma/client에 PrismaClient를 생성했음

저기로 가봄

node_modules로 가서 @prisma에 client가 있음

이것을 클릭해서 타입을 확인해보면 우리의 스키마와 일치하는 타입이 생성되어 있음

node_modules/.prisma/client/index.d.ts에서 확인할 수 있는 User 타입임

보다시피 타입스크립트로 타입이 생성되어 있음

프리스마가 스키마를 확인해서 타입스크립트로 타입을 만들어줬음

보다시피 어떤 필드가 선택적이라면 여기서 확인할 수 있음

number | null이라고 나와있음

보다시피 이렇게 생성되었고 프리스마가 만들어준 이 모든 것은 이 파일에서 나옴

바로 이것이 프리스마에게 가장 중요한 파일임

이렇게 데이터가 어떻게 생겼는지 설명해주는 것만으로 프리스마가 데이터베이스를 수정해주고 관리자 패널도 제공해줌

그리고 클라이언트에서 우리를 도와줄 타입스크립트 타입도 생성해줌

이것으로 우리가 코드를 잘 짤 수 있도록 자동완성 기능을 이용하고 체크를 할 수 있음

그러면 PrismaClient를 좀 더 자세히 알아봄

왜냐하면 지금은 client를 export하고 아무것도 하지 않고 있음

export default를 하기 전에 const client를 선언해봄

그리고 스키마에서 작성한 데이터를 기반으로 자동완성 기능을 이용하는 것을 보여줌

여기서 client.을 쓰면 여러 가지 옵션을 볼 수 있는데 중요한 것은 user가 있음

이것이 있는 이유는 프리스마가 schema.prisma 파일을 보고 User 타입을 만들어줬기 때문임

그러면 client.user를 통해 user 테이블을 다룰 수 있음

보다시피 엄청 많은 옵션이 있음

우선 create를 살펴봄

create를 쓰면 어떻게 되는지 봄

아주 좋은 자동완성 기능으로 여기에 data를 써보면 email을 쓰려고 하면 email을 자동완성으로 쓰고 string 타입이라는 것을 알려줌

이렇게 숫자를 쓰면 오류가 발생했다는 것을 알려줌

왜냐하면 여기서 email이 String이거나 undefined일 수 있다고 했음

email에 숫자를 쓰면 number는 string, null, undefined가 아니라고 알려줌

그럼 Hi로 고쳐봄

그러면 이제 data에서 오류를 확인할 수 있음

name이 필요함

왜냐하면 여기서 스키마를 확인해보면 필수로 보내야하는게 하나 있는데 바로 name임

다른 것은 꼭 필요하지 않음

이것은 꼭 필요하지 않고 이것도 마찬가지임

이 2가지는 알아서 채워질거고 id도 마찬가지임

이제 이것이 얼마나 멋진지 알겠지

prisma.schema 파일을 토대로 도움을 받고 있음

그럼 조건을 만족시키기 위해 name에 hi를 써봄

이것이 다인 것 같음

보다시피 이제 안전하게 user를 create 할 수 있음

물론 이 파일은 누구나 실행할 수 있음

그러면 지금만 이렇게 해봄

pages에서 client를 import 해봄

지금만 index.tsx에서 client를 import 해봄

client를 import하면 이 코드가 실행됨

이것을 import하고 실행해봄

보다시피 실행시켰음

브레이브 브라우저로 돌아가서 홈으로 가봄

보다시피 PrismaClient는 브라우저에서 실행할 수 없음

왜냐하면 잘 생각해보면 여기서 이렇게 한 것은 정말 잘못 됐음

여기서 우리가 db에 직접 접근할 수 있는 파일을 프론트엔드인 브라우저에 추가했기 때문임

이것은 브라우저에서 실행되면 안 됨

이것이 nodejs이든 javascript이든간에 여기서 하고 있는 것은 말이 안 됨

브라우저에서 PrismaClient를 실행할 수 있으면 안 됨

그럼 정말 큰 일이 남

누구도 PrismaClient에 접근할 수 있으면 안 됨

이 코드를 여기에 추가하면 사용자가 홈페이지를 통해 이 자바스크립트를 다운로드 받고 PrismaClient에 직접 접근할 수 있음

이런 사태가 벌어지면 안 됨

거의 다 왔음

보다시피 PrismaClient가 잘 작동하고 있음

아주 좋은 자동완성 기능이 생겼음

여기서 보다시피 이 모든 타입은 schema.prisma에 작성한 내용을 바탕으로 만들어졌음

실수를 덜 할 수 있으니까 이것은 아주 좋은 소식임

그런데 이 client를 어디서 사용할지는 아직 모름

물론 이 client를 프론트엔드에서 사용하는 것은 안 됨

다행스럽게도 여기에 에러가 출력되고 있음

브라우저에서 실행할 수 없음

아주 다행임

이 말은 nextjs 프론트엔드에서 prisma를 import 할 수 없다는 것임

큰 보안 문제를 막아주고 있으니 아주 다행임

사용자들에게 데이터베이스를 수정할 수 있는 권한을 주면 안 됨

그럼 이것은 어디서 사용할 수 있을까

이 PrismaClient를 어디서 실행시키면 될까

이것은 다음 영상에서 알아봄