# Calculator - Personal

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
[Kyo](https://github.com/KyoPak)가 구현한 Calculater Step-1 입니다.


## 💻 개발환경 및 라이브러리
[![swift](https://img.shields.io/badge/swift-5.6-orange)]()
[![xcode](https://img.shields.io/badge/Xcode-13.4.1-blue)]()


## 🧑 팀원
<img src = "https://user-images.githubusercontent.com/59204352/187332158-a15815eb-3847-40e5-a6f0-93a373f21180.JPG" width=200 height=170>|
|:--:|
|[Kyo](https://github.com/KyoPak)|
  

## 🕖 타임라인

Step - 1 : 2022.09.20 ~ 09.22

## 🗺 UML


![UML](https://user-images.githubusercontent.com/59204352/191182565-8e07c1d3-7924-4fcb-8c61-db74697405fd.jpg)


## 💻 실행 화면 

추후에 추가 예정



## 🎯 트러블 슈팅 및 고민
### Step - 1 
   
#### ***1. LinkedList와 Array로 Queue를 구현할 때의 각각의 차이점에 대해서 고민***
- Array는 접근할때 시간복잡도 O(1)으로 매우 빠르기 때문에 탐색기능이 필요할 때는 Array로 구현이 더 적합할 것이라고 판단을 하였습니다. 
- 하지만 가장 앞의 요소를 제거하거나 중간 요소를 제거할 때는 Array의 경우에는 O(n)이고 LinkedList의 경우에는 O(1)으로 head부분만 바꿔주면 되기 때문에 LinkedList가 더욱 적합하다고 생각하였습니다.
- 하지만 Node타입의 적용한 배열을 사용한다면 탐색기능과 삭제기능 모두 좋지 않을까 라는 생각이 추후에 들었습니다.

### ***2. CalcutatorItemQueue와 LinkedList사이의 의존성 문제에 대한 고민***
- 사실 외부에서 CalcutatorItemQueue의 객체를 만들 때 LinkedList 인스턴스를 외부에서 주입하는 방식을 고민했습니다. 
- 하지만 단순히 외부에서 인스턴스, 객체를 주입한다고 해서 의존성이 떨어지는 효과를 기대할수 없다고 생각했습니다. 의존성을 분리해주는 프로토콜이 존재하지 않는 설계를 했기 때문이었습니다.
- 또한, 단순히 의존성을 낮추기 위해 의존성 주입을 사용하는 것이 아닌 얼만큼 CalcutatorItemQueue가 얼만큼 재사용이 되는지에 대한 고민도 같이 해보았을 때 의존성 주입은 불필요하다고 판단하였습니다.

    
## 📚 참고 링크
[LinkedList](https://blog.encrypted.gg/932?category=773649)

[Generic](https://docs.swift.org/swift-book/LanguageGuide/Generics.html)

[UntTest Tips](https://yagom.net/courses/unit-test-%EC%9E%91%EC%84%B1%ED%95%98%EA%B8%B0/)
