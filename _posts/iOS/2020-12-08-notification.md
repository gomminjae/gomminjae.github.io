---
title: "NotificationCenter"
excerpt: "notificationCenter with observer"
categories:
 - iOS
last_modified_at: 2020-12-09T13:00:00+09:00
toc: true
---
# Norification Center
>   ***Notification에 등록된 Event가 발생하면 해당 Event를 처리할 Observer들이 Event에 대한 행동을 취하는 것이 NotificationCenter의 방식입니다. Notification이 앱 내에서 이벤트 메시지를 보내면 어디서든 이 observer가 받아서 처리합니다.***

## - Notification Center 

![Imgur](https://i.imgur.com/CtMGiqY.png)(

위 그림과 같이 객체에서 이벤트가 발생하면 Notification Center로 Post를 하고 그 이후 등록된 observer들에게 전달해줍니다. 

**NotificationCenter은 Delegate패턴(지정된 오브젝트 끼리만 상호작용)와는 달리 앱 어디든, 어느 객체와도 상호작용이 가능합니다. **

## - Usage

- 첫번째로 해당 객체 Event를 Notification center에 등록합니다
- 해당 Event를 처리할 Observer를 등록합니다. 

## **NotificationCenter등록**

```swift
@objc func buttonTapped() {
  NotificationCenter.default.post(name: "noti", object: nil)//object에는 전달할 값 또는 특정 객체를 같이 넘김 
}
```

***button이 클릭되면 notification 이벤트가 실행되도록 작성하였습니다.***

---

## **observer 등록**

```Swift
NotificationCenter.default.addObserver(self, selector: #selector(btnTapped()), name: "noti", object: nil)

@objc func btnTapped() {
  label.layer.isHidden = true 
}

```

***notificationCenter에서 noti라는 이벤트가 감지되면 Observer은 이벤트를 받아 label을 숨기도록 작성하였습니다.***

****

**selector:** 해당 이벤트를 감지했을때 처리할 액션을 넣어줍니다

**name:** 등록한 notificationcenter의 이름을 적어줍니다. 
**object:** 전달할 값을 넣어줍니다.

---

## **observer 제거**

```swift
NotificationCenter.default.removeObserver(_ observer: Any, 
                    name aName: NSNotification.Name?, 
                    object anObject: Any?)
```





