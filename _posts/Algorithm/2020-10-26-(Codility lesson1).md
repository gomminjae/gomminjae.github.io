---
title: "(Codility) Lesson1 Iterations [Swift4]"
excerpt: "swift algorithm"
categories: 
 - Algorithm
last_modified_at: 2020-10-26T13:00:00+09:00
toc: true
---

# Codility Iterations(Lesson1)

![img](https://blog.kakaocdn.net/dn/cIqPjH/btqFAO7xUBz/fs0itjGKKG7pvZGjTQUux1/img.png)

*이문제는 int타입의 n을 2진수로 바꿔서 1과 1 사이의 0의길이의 최댓값을 구하는 문제입니다*

```swift
public func solution(_ N : Int) -> Int {
    
    let a = String(N, radix: 2)
    var cnt: Int = 0
    var maxCount: Int = 0
    var check: Bool = false
    
    
    for i in 0..<a.count {
        let index = a.index(a.startIndex, offsetBy: i)
        if(a[index] == "1") {
            if(cnt > maxCount) {
                maxCount = cnt
            }
            check = true
            cnt = 0
        }else {
            if(check) {
                cnt += 1
            }
        }
    }
    return maxCount
}
```

다음과 같이 구현하였습니다. 2진수는 String함수를 이용하여 문자열형태의 2진수를 만들었습니다. String 타입은 반복문에서 index이동이 번거롭습니다. index함수를 이용해서 시작부분과 offset을 정해주어야 합니다. ***2진수 변경 방법과 String iterator부분***만 숙지하시면 쉽게 풀 수 있습니다.😄

