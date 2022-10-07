# CalculatorII - Team
## 🗒︎목차
1. [소개](#-소개)
2. [개발환경 및 라이브러리](#-개발환경-및-라이브러리)
3. [팀원](#-팀원)
4. [타임라인](#-타임라인)
5. [UML](#-uml)
6. [실행화면](#-실행-화면)
7. [트러블 슈팅 및 고민](#-트러블-슈팅-및-고민)
8. [참고링크](#-참고-링크)


## 👋 소개
[Kyo](https://github.com/KyoPak), [som](https://github.com/jsa0224)의 각자의 계산기 프로젝트를 합쳐본 Calculater입니다.


## 💻 개발환경 및 라이브러리
[![swift](https://img.shields.io/badge/swift-5.6-orange)]()
[![xcode](https://img.shields.io/badge/Xcode-13.4.1-blue)]()


## 🧑 팀원
<img src = "https://user-images.githubusercontent.com/59204352/193524215-4f9636e8-1cdb-49f1-9a17-1e4fe8d76655.PNG" width=200 height=170>|<img src = "https://i.imgur.com/Q2htdu3.png" width=200 height=170>|
|:--:|:--:|
|[Kyo](https://github.com/KyoPak)|[som](https://github.com/jsa0224)|
 

## 🕖 타임라인

Step - 1, 2 : 2022.10.03 ~ 10.07


## 🗺 UML

<details>
<summary> 
펼쳐보기
</summary>
    
![제목 없는 다이어그램](https://user-images.githubusercontent.com/59204352/191893437-3885c44e-cb43-46e6-aeb6-49a7beb0d05e.jpg)
    
</details>



## 💻 실행 화면 
<details>
<summary> 
펼쳐보기
</summary>
|일반계산|=후 연속계산|.,- 사용계산|
|------|--|---|
![일반계산](https://user-images.githubusercontent.com/59204352/193729556-202e49fc-a65e-45bd-81f3-e99eb46dec2b.gif)|![연속계산](https://user-images.githubusercontent.com/59204352/193729600-3cf71d6b-4369-40cf-a86c-ba7640be61f5.gif)|![- 버튼연산](https://user-images.githubusercontent.com/59204352/193729706-4cbad361-6ac0-407f-85ac-5665b60c44eb.gif)

|AC 버튼클릭|CE 버튼클릭|계산내역|
|------|--|---|
![AC버튼](https://user-images.githubusercontent.com/59204352/193729761-2d302f55-15b2-43c8-95f0-eb35376c8170.gif)|![EC버튼](https://user-images.githubusercontent.com/59204352/193729774-ff6208a0-b167-4ce7-8ed5-b148b274a751.gif)|![계산내역](https://user-images.githubusercontent.com/59204352/193729825-1efe6006-b630-414c-bd8c-f6b7ad9c7dbf.gif)

</details>


## 🔗 협업 진행 방식
- 코드를 수정해야하는 부분을 정한 후, 서로에게 PR을 보내 merge를 하는 방식으로 진행하였습니다. 
팀원이 PR을 보내면 어떤 부분을 수정하였는지 코드 변경이력을 보며 리뷰어의 입장이 되어 꼼꼼하게 check해보는 경험을 할 수 있었던 것 같습니다.
- 또한 수정이 필요한 기능, 파일 등으로 브랜치를 생성하여 수정을 따로 진행하였습니다. 
기능별로 Branch를 생성하여 수정하다 보니 처음에는 약간 번거로웠지만 어떤 부분을 수정하였고, 어떤 기능과 관련이 있는 수정을 진행하였는지 한눈에 파악하기가 쉬웠다고 생각합니다. 

![스크린샷 2022-10-07 오후 2 02 20](https://user-images.githubusercontent.com/59204352/194471468-7a9aec38-7d28-4532-880f-3aa5858890ea.png)

![스크린샷 2022-10-04 오후 3 26 02](https://user-images.githubusercontent.com/59204352/193749323-5718010a-245b-428e-81cb-0e62dbdcc760.png)

- 위와 같은 방식으로 진행하면서, PR에 Label를 표시할 수 있다는 사실을 알게 되었습니다. Label을 추가해서 PR을 작성하니 직관성이 높아져 자주 사용하게 될 거 같습니다👍

## 🎯 트러블 슈팅 및 고민
### Step - 1, 2

   
#### ***1. Error Handling에서의 타입캐스팅!***
- Error가 발생한다면 resultLabel에 Error Message를 표기하는 방식으로 이용자에게 Error를 전달해주고자 하였습니다. 때문에 발생한 Error와 보여줘야할 Message를 아래와 같은 코드로 일일이 매칭을 해줘야 했습니다.
```swift
} catch CalculatorError.ErrorA {
    resultLabel.text = CalculatorError.ErrorA.message 
    ...
} catch {
    resultLabel.text = CalculatorError.ErrorB.message
```
- 하지만 위와 같은 방식은 아래코드처럼 매칭이 잘못될 확률이 있다고 피드백을 받았습니다. 
```swift
} catch CalculatorError.ErrorA {
    resultLabel.text = CalculatorError.ErrorC.message 
```
- 타입캐스팅이란 방법을 조언을 받은 후, 전달받은 error타입의 변수를 CalculatorError타입으로 다운캐스팅을 한다면 일일이 매칭하지 않아도 된다는 것을 알게 되었습니다. Error마다 처리방법이 다르다면 일일이 처리방법들을 구현해줘야하지만 지금과 같은 로직이라면 이러한 방법을 사용하여 개발자의 실수를 줄일 수 있고 코드도 간결해진다고 생각합니다. 
```swift
} catch {
    if let error = error as? CalculatorError {
    resultLabel.text = error.message
    }
}
```


#### ***2. 서로 다른 코드를 합칠 때의 고민***
- 효율적이고 적합한 코드에 대해 고민을 많이 했습니다. 계산기 I에서 리뷰어분께 받은 코멘트를 바탕으로 완료한 리팩토링이 된 코드라 더 결정하기 어려웠습니다. 이 부분은 프로젝트 경험을 쌓아가면서 해결이 될 것 같습니다. 

  



    
## 📚 참고 링크
[Swift Language Guide - Protocols](https://docs.swift.org/swift-book/LanguageGuide/Protocols.html)<br>[Swift Language Guide - Extentions](https://docs.swift.org/swift-book/LanguageGuide/Extensions.html)<br>[Swift Language Guide - Error Handling](https://docs.swift.org/swift-book/LanguageGuide/ErrorHandling.html)<br>[NumberFormatter](https://developer.apple.com/documentation/foundation/numberformatter)<br>[오토레이아웃 정복하기 - 야곰닷넷](https://yagom.net/courses/autolayout/)
