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