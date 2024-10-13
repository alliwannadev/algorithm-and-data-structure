# Chapter 5. 해시 테이블 (Hash Table)

## 1. 개념 설명

## 2. 연습 문제

### 2-1. 프로그래머스 - 폰켓몬

* 방법 1. HashSet으로 풀이하기

    ```java
    import java.util.*;
    
    class Solution {
      public int solution(int[] nums) {
          int max = nums.length / 2;
          Set<Integer> numSet = new HashSet<>();
    
          for (int num : nums) {
              numSet.add(num);
          }
    
          if (numSet.size() >= max) {
              return max;
          } else {
              return numSet.size();
          }
      }
    }
    ```

    * 폰켓몬을 선택하는 경우의 수는 폰켓몬의 종류가 모두 다를 때에도 최대 값이 `N / 2` 마리를 넘을 수 없다.
    
    * 문제에서 주어진 입출력 예시들을 이용하여 문제 풀이 방법을 찾아내보자.

        ```
        [3, 1, 2, 3]       ---> 최대는 2마리, 중복 없는 폰켓몬의 종류는 3마리 (3, 1, 2)  ---> 정답 : 2마리
        
        [3, 3, 3, 2, 2, 4] ---> 최대는 3마리, 중복 없는 폰켓몬의 종류는 3마리 (3, 2, 4)  ---> 정답 : 3마리
        
        [3, 3, 3, 2, 2, 2] ---> 최대는 3마리, 중복 없는 폰켓몬의 종류는 2마리 (3, 2)     ---> 정답 : 2마리
        ```
        
        * 폰켓몬의 종류가 최대 값 이상이면 최대 값을 정답으로 하고 아니면 폰켓몬의 종류를 정답으로 하면 된다는 것을 알아낼 수 있다.

### 2-2. 프로그래머스 - 의상


