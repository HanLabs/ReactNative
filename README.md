# ReactNative HanSJin
Study the ReactNative for iOS.

## References for RN
https://academy.realm.io/kr/posts/react-native/


### What's the defference between `React`, `Ractive`, and `ReactNative`?

* [React](https://facebook.github.io/react/) 는 페이스북이 웹 개발을 쉽게 하기 위해 만든 기술. <br>
커스텀 컴포넌트를 만들고 쉽게 조합해서 뷰를 손쉽게 만들 수 있습니다.
* **Reactive** 는 마이크로소프트가 창안한 개념으로 스트림과 비동기 처리등을 LINQ에 영향을 받은 방법으로 깔끔하게 처리할 있게 한 패러다임. <br>
예를 들어 [RxJava](https://github.com/ReactiveX/RxJava), [RxAndroid](https://github.com/ReactiveX/RxAndroid), [ReactiveCocoa](https://github.com/ReactiveCocoa/ReactiveCocoa) 등등 ..
* [React Native](https://facebook.github.io/react-native/) 는 리액트의 접근 방법을 모바일로 확장하는 페이스북의 오픈소스 프로젝트.


### Let's Set Environment

ReactNative 는 iOS & Android 플랫폼 모두에서 JS 를 통해 개발되는 환경이기 때문에 Node.js 를 비롯한 귀찮은 설정 과정이 필요하다.

Let's install the `watchman` and `flow`.
```
brew install watchman
brew install flow
```
> brew 를 통해 위 모듈들을 설치하며 pre-version 인 OS X 로 인해 경고가 출력되었지만, 설치에 실패하지는 않았다.
> 
> **$ watchman --version** <br> 
> 3.8.0 <br>
> **$ flow --version** <br>
> Flow, a static type checker for JavaScript, version 0.17.0

And install `Node.js` with `nvm`.
```
brew install nvm
```

nvm 을 설치한 후 나오는 메시지를 따라해야한다.

You should create NVM's working directory if it doesn't exist:
```
mkdir ~/.nvm
```

Add the following to ~/.zshrc or your desired shell
configuration file:
(내 경우는 vi ~/.bashrc)

```
  export NVM_DIR="$HOME/.nvm"
  [ -s "/usr/local/opt/nvm/nvm.sh" ] && . "/usr/local/opt/nvm/nvm.sh"  # This loads nvm
  [ -s "/usr/local/opt/nvm/etc/bash_completion" ] && . "/usr/local/opt/nvm/etc/bash_completion"  # This loads nvm bash_completion
```

```
nvm install node
nvm alias default node
```

**!! Trouble Shooting during installation** <br>
nvm 을 install 시도 시 몇 가지 직접 설정해주어야 하는 작업들이 있었다. <br>
나는 CLI 로 zshell 을 사용중이므로, `~/.zshrc` 파일을 수정했다. <br>
`[ -s "/Users/kksd0900/.nvm/nvm.sh" ] && source "/Users/kksd0900/.nvm/nvm.sh"` 을 추가했다. (경로는 각자 설정) <br>
만약 이 source 를 추가하고도 nvm 이 실행되지 않아서, `$ source $HOME/.nvm/nvm.sh` 을 커맨드라인에 직접 실행하니 된다. <br>

설치가 성공적으로 진행되었다면 <br>
> **$ nvm --version** <br>
> 0.34.0

이 출력된다.

> **$ node --version** <br>
> v12.10.0

node 의 설치도 성공적.


### Create RN Project

프로젝트 생성 전에 npm 을 통해 RN 라이브러리를 설치한다. <br>
`npm install -g react-native-cli` 

패키지를 설치했다면, cli 명령어를 통해 Xcode 프로젝트를 생성한다. <br>
`react-native init ReactNative` (근데 무슨 플젝 생성에 시간이 이리 오래걸리는건지;;)

>  Run instructions for iOS: <br>
>  • cd ReactNative && react-native run-ios <br>
>    - or - <br>
>  • Open ReactNative/ios/ReactNative.xcworkspace in Xcode or run "xed -b ios" <br>
>  • Hit the Run button

프로젝트 생성 성공! (아니, 잠깐만.. AppDelegate 가 ObjC 로 생성되는거 모야 ㅡㅡ)


### Start Develop RN !

생성된 프로젝트에서 `app.js` 와 `index.js` 파일을 실행한다.  <br>
물론 Xcode 로는 켜지지 않는다.. WebStorm 을 정말 오랜만에 켜는것 까지는 OK.. 근데 WebStorm 에서 코드 인덴트가 다 깨지는데..?
> 웹스톱의 `Swtich language level to JSX Harmony` 를 실행하니 빨간 줄이 다 사라졌다. <br> 
> 근데 JS ECMA 6 에서 뭔가 문제가 발생하는 것 같은데.. 어쨋든 Xcode 상에서 App Run 은 문제 없이 동작한다.

**!! Trouble Shooting with start an App** <br>

* `$ react-native run-ios --verbose` 입력 시, iPhone X simulator 를 찾을 수 없다는 Alert 가 출력된다.
> Xcode 를 13.0 으로 업데이트하며 iPhone X 모델의 시뮬레이터가 설치되지 않은 것으로 보인다. 시뮬 추가 후 정상 동작한다. 

* 앱을 실행 시 Node Server 에 접속이 실패했다는 경고창이 출력된다. 
> 시뮬레이터가 node server 에 접속하지 못하는 현상으로 보인다.  <br>

`$ npm start` 를 통해 node server  를 실행해주어야 한다. <br>
 하지만 `error listen EADDRINUSE: address already in use :::8081.` 으로 이미 node port 가 사용 중이라는 메시지가 출력된다. <br>
그러므로 `$ ps aux | grep node`  와 `kill -9 {PID}` 를 통해 process 를 죽인 후 npm start 를 입력했지만 또 다른 에러가 출력된다.
이 에러를 자세히 확인하기 위해 `http://localhost:8081/index.bundle?platform=ios&dev=true&minify=false` 에 접속해보니

> Error: Duplicated files or mocks. Please check the console for more info <br>
>   at setModule (/Users/kksd0900/Desktop/HanSJinLab/ReactNative-HanSJin/ReactNative/node_modules/jest-haste-map/build/index.js:620:17) <br>
> ...

과 같은 에러가 출력된다..
