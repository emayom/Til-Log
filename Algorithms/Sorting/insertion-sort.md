# 삽입 정렬(Insertion Sort)  

| `Algorithm` | :thumbsup: `Best` | `Avg` | :thumbsdown: `Worst` | `Space Complexity` | `stable`| `in-place` |
| :---      |   :----:  |   :----:   |   :----:   |   :----:   |   :----:   |   :----:   |
| 삽입 정렬(Insertion Sort) | O($n$) | O($n^2$) | O($n^2$) | O(1) | :white_check_mark: | :white_check_mark: |

## 동작 원리 

삽입 정렬은 `정렬된 배열`과 `비교`, `삽입`이 기본 동작 원리이다.  
**첫 번째 요소를 정렬된 부분으로 간주**, 배열의 두 번째 요소부터 한 번에 하나를 취해서 정렬된 배열 사이의 올바른 위치를 찾아 삽입한다.  
배열의 과반을 점차적으로 만들어 정렬을 구축하며, 과반은 항상 정렬되어 있다. 

<br>

## 구현
#### 의사코드(pseudo code)
- 배열의 두 번째 요소부터 선택하여 정렬에 삽입을 시작한다.
- 정렬할 요소를 이미 정렬된 배열의 항목들과 비교하는 과정이 필요하여 이중 `for`문(반복문)으로 구현한다. 
- 반복함에 따라 점차 비교해야하는 정렬된 배열이 늘어가는 것을 구현하기 위해서 
    - 내부 반복문(Inner)의 초기식 제어 변수 j의 값은 i - 1 부터 시작하여 감소한다.  
- 정렬할 요소와 정렬된 배열의 값을 비교, 
    - 정렬할 요소가 더 작은 값일 경우 ➡️ 비교 위치의 값을 덮어씌우며 반복한다. 
    - 정렬할 요소가 더 작은 값이 아닐 경우 ➡️ 멈추고 정렬할 요소를 올바른 위치에 삽입한다.  
- 위의 과정을 배열의 길이만큼, 정렬될 때까지 반복한다. 

<br>

```js
const array = [25, 4, 49, 22, 27, 32, 14, 7, 12, 40];

const insertionSort = (arr) => {
  for (let i = 1; i < arr.length; i++) {
    let currentVal = arr[i];
    let flag = i;

    for (let j = i - 1; j >= 0; j--) {
      if (currentVal >= arr[j]) break;

      arr[j + 1] = arr[j];
      flag = j;
    }

    if (flag != i) arr[flag] = currentVal;
  }
};
```

<br>

## 시간 복잡도 
선택 정렬의 시간 복잡도는 `Best`의 경우 시간 복잡도는 O($n$)이고, `Worst`, `Average`의 경우 O($n^2$)이다. 


## 공간 복잡도 
주어진 배열 안에서 정렬이 수행되므로 공간복잡도는 O(1)이다.

<br>

## 결론 
삽입 정렬은 선택 정렬과 거품 정렬에 비해서는 상대적으로 효율적일 수 있다.  
특히 삽입 정렬은 **필요할 때만 삽입하는 특징**을 가지고 있어 <u>데이터가 거의 정렬된 경우</u> 혹은 이미 정리된 데이터에 새로운 데이터가 들어와서 재정렬하고, 실행 중인 정렬을 유지하여 최신 상태로 두어야 할 경우 효율적이다. 
