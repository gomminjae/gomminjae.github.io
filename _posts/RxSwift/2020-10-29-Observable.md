---
title: "RxSwift Observable"
excerpt: "RxSwift Observable"
categories: 
 - RxSwift
last_modified_at: 2020-10-29T13:00:00+09:00
toc: true
---

# Observable? 

![img](http://reactivex.io/assets/operators/legend.png)

Observable은 Reactivex에서 중요한 개념입니다. Reactivex에서는 옵저버에 의해 임의의 순서에 따라 병렬로 실행되고 결과는 나중에 연산됩니다. 메소드 호출보다는 Observable안에 데이터를 조회하고 변환하는 작업을 정의한 후 Observable이 이벤트를 발생시키면 옵저버의 관찰자가 감지하고 준비된 연산을 실행시켜 결과를 리턴합니다. 이 방법은 의존관계가 없고 코드량이 많을때 한번에 여러개의 코드를 실행 시킬 수 있어서 실행기간이 짧아진다는 장점이 있습니다. 

# Observable 생성

**비동기 코드 흐름** 

1. 비동기 메소드 호출로 결과를 리턴받고 필요한 동작을 처리하는 메서드를 정의한다: 이 메서드는 *옵저버*의 일부가 된다.
2. *Observable*로 비동기 호출을 정의한다.
3. *구독*을 통해 옵저버를 Observable 객체에 연결 시킨다(또한, 동시에 Observable의 동작을 초기화 한다).
4. 필요한 코드를 계속 구현한다; 메서드 호출로 결과가 리턴될 때마다, 옵저버의 메서드는 리턴 값 또는 (Observable이 배출하는)*항목들*을 사용해서 연산을 시작한다.

```swift
import RxSwift 

func ObservableItem(element: [Int]) -> Observable<Int> {
  return Observable<Int>.create { observer -> Disposable in
         for item in items {
           observer.onError(print(error))
           break
         }
         observer.onNext(item)
         }
     observer.onCompleted()
     return Disposable.create()
}
```

이 코드에서 우리는 Int 타입의 observable을 생성하였습니다. 여기서 중요한 메소드인 onNext, onError, onCompleted에 대하여 설명하겠습니다. 

- onNext - Observable은 새로운 항목들을 배출할때마다 미 베소드를 호출합니다. Observable이 배풀하는 항목을 파라미터로 전달 받습니다. 
- onError - Observabled이 기대하는 데이터가 생성되지 않았거나 다른 이유로 오류가 발생하였을때 오류를 알리기 위해서 이 메소드를 호출합니다. **이 메소드가 호출되면 더이상 onNext와 onCompleted가 호출되지 않습니다.**
- onCompleted - 오류가 발생하지 않았다면 Observable은 마지막 onNext를 호출한후 이 메소드를 호출합니다. 

# Cold Observable & Hot Observable 

- **Cold Observable**  - *옵저버가 subscribe되는 시점부터 이벤트를 생성하여 방출하기 시작합니다.* 옵저버마다 별도의 Observable이 필요합니다. 대표적인 예로는 HTTP요청이 있습니다.
- **Hot Observable** - *생성과 동시에 이벤트를 방출하기 시작합니다. 그리고 subscribe와는 상관없이 옵저버들에게 이벤트를 중간부터 전송해줍니다.* 여러 옵저버가 하나의 Observable을 공유할 수 있습니다.  대표적인 예로는 UIEvent, Property, Timer등이 있습니다. 

​     -  

