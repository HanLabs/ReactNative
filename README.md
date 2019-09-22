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
nvm install node
nvm alias default node
```

**!! Trouble Shooting during installation** <br>
nvm 을 install 시도 시 몇 가지 직접 설정해주어야 하는 작업들이 있었다. <br>
나는 CLI 로 zshell 을 사용중이므로, `~/.zshrc` 파일을 수정했다. <br>
`[ -s "/Users/kksd0900/.nvm/nvm.sh" ] && source "/Users/kksd0900/.nvm/nvm.sh"` 을 추가했다. (경로는 각자 설정) <br>
만약 이 source 를 추가하고도 nvm 이 실행되지 않는다면, $ `source $HOME/.nvm/nvm.sh` 을 커맨드라인에 직접 실행하면 된다. <br>

설치가 성공적으로 진행되었다면 <br>
> **$ nvm --version** <br>
> 0.34.0

이 출력된다.
