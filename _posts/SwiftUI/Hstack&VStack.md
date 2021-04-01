---
title: "SwiftUI View Stack"
excerpt: "SwiftUI 기본"
categories: 
 - SwiftUI
last_modified_at: 2021-03-28T13:00:00+09:00
toc: true
---

# HStack?

> 하위 자식들을 수평으로 정렬하는 뷰를 의미합니다. 

---

## Declaration 

```swift
init(alignment: VerticalAlignment = .center, spacing: CGFloat? = nil, content: () -> Content)
```

## 예제 

---

```swift
var body: some View {
  HStack(alignment: .top, spacing: 10) {
    ForEach(1...5, id: \/self) {
      Text("Item \($0)")
    }
  }
}
```

## 결과

![Five text views, named Item 1 through Item 5, arranged in a](https://docs-assets.developer.apple.com/published/4d9bc52c0fbde5252c797d82d913a50b/6075/SwiftUI-HStack-simple@2x.png)

---

# VStack?

> 하위 자식들을 수직으로 정렬하는 뷰를 의미합니다.

## Declaration

```swift
init(alignment: HorizontalAlignment = .center, spacing: CGFloat? = nil, content: () -> Content)
```

## 예제

---

```swift
var body: some View {
    VStack(
        alignment: .leading,
        spacing: 10 //항목끼리의 간격
    ) {
        ForEach(
            1...10,
            id: \.self
        ) {
            Text("Item \($0)")
        }
    }
}
```

---

## 결과 

---

![Ten text views, named Item 1 through Item 10, arranged in a](https://docs-assets.developer.apple.com/published/93d31b000cb6f5419689a7b765474401/6075/SwiftUI-VStack-simple@2x.png)

---

# ZStack?

> 하위 자식들을 두 축으로 정렬하여 오버레이하는 뷰입니다. <- 이 말이 저는 이해가 잘... 😂 그래서 저는 자식뷰들을 특정한 두 축을 이용해서  중첩시키는 뷰라고 이해하였습니다.

## 에제 1

```swift
var body: some View {
    ZStack(alignment: .bottomLeading) {
        Rectangle() //사각형
            .fill(Color.red) //색 설정 
            .frame(width: 100, height: 50)//크기 설정 
        Rectangle()
            .fill(Color.blue)
            .frame(width:50, height: 100)
    }
    .border(Color.green, width: 1)
}
```

## 결과

![A green 100 by 100 square containing two overlapping rectangles: on the](https://docs-assets.developer.apple.com/published/b18f4156c9780e8200b05194bff17db4/6075/SwiftUI-ZStack-alignment@2x.png)

 처음에 빨간 가로100 세로 50의 사각형이 형성되고 그다음 가로 50 세로 100의 파란색 뷰가 빨간색 뷰 위로 중첩되는것을 볼 수 있습니다. 최종적으로 ZStack뷰의 크기를 BorderWidth로 확인해본 결과 100 * 100의 사각형인것을 확인할 수 있습니다. 



## 예제2

```swift
 let colors: [Color] = [.red, .orange, .yellow, .green, .blue, .purple]
    
    var body: some View {
        ZStack {
            ForEach(0..<colors.count) {
                Rectangle()
                    .fill(colors[$0])
                    .frame(width: 100, height: 100)
                    .offset(x: CGFloat($0) * 10.0, y: CGFloat($0) * 10.0) //offset을 이용해서 뷰를 일정거리 떨어지게 함 
            }
            .border(Color.green, width: 10)
        }
    }
```

## 결과

![Six squares of different colors, stacked atop each other, with a 10-point](https://docs-assets.developer.apple.com/published/5ce47ef59a84b346d733bcf2f4a7853e/6075/SwiftUI-ZStack-offset-rectangles@2x.png)

이 코드를 보면 6개 색의 사각형들이 **offset**에 의해 현재의 뷰의 x축 y축에서 곱하기 10 되면서 중첩되는것을 볼 수 있습니다 .

이것은 offset을 이용해서 중첩시켰기때문에 ZStack뷰의 크기와 위치는 는 처음 생성된 빨간색뷰와 같습니다. 

![스크린샷 2021-03-28 오후 5.43.25](/Users/gwonminjae/Library/Application Support/typora-user-images/스크린샷 2021-03-28 오후 5.43.25.png)

