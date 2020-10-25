---
title: "Swift Subscripts"
excerpt: "subscripts 공부"
categories:
 - iOS
 last_modified_at: 2020-10-25T13:00:00+09:00
 toc: true
---
# Subscripts(서브스크립트)
공식문서에서 class, structures 그리고 enumerations는 서브스크립트를 정의할 수 있다,  컬렉션 , 리스트 또는 순열의 멤버에 접근하기위한 shortcut이라고 공식문서에는 정의되어있습니다. 서브스크립트를 사용해서 설정과 검색을 위해 메소드를 나눌 필요없이 인덱스로 값을 설정하고 검색합니다. 예를 들어 let arr = [1,2,3]이 있으면 배열값 3을 얻기위해서는 arr[2]로 값을 찾는데 이렇게 [2]처럼 값을 더 쉽게 찾기 위해서 정의하는것을 서브스크립트라고 합니다. 

# 구현법 
- subscript 문법을 사용합니다 

  ```swift
  subscript(index: Int) -> Int {  
     get {        // return subscript value    
     }  
     set {        // perform setting action   
     }
  } 
  ```

- ## 구현2
  구구단 예제로 하겠습니다. 

  ```swift
  struct TimesTable {     
    let multiplier: Int   
    subscript(index: Int) -> Int {       
      return multiplier * index     
    }
  }
  let threeTimesTable = TimesTable(multiplier: 3) print("six times three is \(threeTimesTable[6])")  
  ```

앞서 보듯 timeTable struct를 3의 배수로 설정해주고 timeTable[6]을 불러주면 3이 곱해진 18이 출력됩니다. 이렇게 subscript는 array, list등을 조작해야할때 편리하게 쓰일 수 있습니다. 
