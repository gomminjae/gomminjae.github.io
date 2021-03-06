---
title: "ViewController의 생명주기"
excerpt: "Life cycle of VC"
categories:
 - iOS
last_modified_at: 2020-10-25T13:00:00+09:00
toc: true
---

ios개발을 시작하면서 개발에 흥미를 붙이기 위해서 코드만 보고 따라하는식으로 공부를 하였는데 그러다 보니 기본적인 개념, 앱이 어떻게 실행되고 종료되는지에 대한 내용 숙지가 제대로 되지 않아 개발하는데 힘이 들었습니다. 그러다 보니 기초개념, cs공부를 시작하게 되었고 오늘은 ios개발에서 중요한 부분 중 하나인 ViewController 생명주기, 앱 생명주기에 대하여 공부를 하겠습니다. 


## 앱 생명주기 <App Lifecycle>
앱 생명주기는 흔히 background상태와 foreground상태로 나눠져있습니다. background상태는 우리가 흔히 홈버튼을 눌렀을때 화면상에는 보이지 않지만 실행되고 있는 상태이고 foreground는 말 그대로 앱이 전면에 실행되고 있는 상태입니다. 앱의 실행상태는 다음과 같습니다. 
- __Not Running (앱이 실행되지 않은 상태)__
- __Inactive (앱이 실행중인 상태이나 발생한 이벤트가 없는 상태)__
- __Active (앱이 실행중이며 이벤트가 발생한 상태)__
- __background (앱이 백그라운드에서 상태이고 실행되는 코드가 있는 상태)__
- __Suspended (앱이 백그라운드에 있고 실행되는 코드가 없는 상태)__
---

## ViewController 생명주기
ios어플은 여러개의 ViewController가 모여 하나의 앱을 이룹니다. 한 화면에서 다음화면으로 전환될때 기종의 화면위에 새로운 화면이 쌓이는 방식으로 전환합니다 이 때 각각의 뷰컨트롤러는 자신만의 생명주기를 가지고있습니다. 
![view](https://miro.medium.com/max/1850/1*etDLgjBamDJoiaM3_hie9A.png)
- __viewDidLoad: ViewController가 처음 호출 될때__
- __viewWillAppear: ViewController가 화면에 나타나기 직전에 호출__
- __viewDidAppear: ViewController가 화면에 나타난 직후에 호출__
- __viewWillDisappear: ViewController가 화면에 사라지기 직전에 호출__
- __viewDidDisappear: ViewController가 화면에 사라진 직후에 호출__

ViewDidLoad는 앱을 실행한 후 처음으로 호출되며 그 이후에는 호출되지 않습니다. 그 후 __viewWillAppear -> viewDidAppear -> viewWillDisappear -> viewDidDisappear순으로 호출되고 실행됩니다. 이 생명주기를 이용하여 보다 효율적인 개발을 할 수 있습니다.

## 마무리
이렇게 간단하게 생명주기에 관하여 공부해 보았습니다. 어려운 내용은 아니지만 확실히 숙지하지 못하면 큰 단접이 될거같다는 생각이 들었습니다. 오류가 있거나 수정해야할 내용이 있으면 피드백 부탁드립니다!



