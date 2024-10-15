# Chapter 5. 해시 테이블 (Hash Table)

## 1. 개념 설명

* `해시 테이블 (Hash Table)`은 키 (key)에 대응되는 값 (value)을 저장하는 자료구조다.

    * 시간 복잡도 : 탐색, 삽입, 삭제의 시간 복잡도는 평균적으로 `O(1)`이며 최악의 경우에는 충돌로 인해 `O(N)`이 될 수도 있다.

## 2. 연습 문제

### 2-1. 프로그래머스 - 폰켓몬

* HashSet으로 풀이하기

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

* HashMap으로 풀이하기
    
    ```java
    import java.util.*;
    
    class Solution {
      public int solution(String[][] clothes) {
          Map<String, Integer> map = new HashMap<>();
    
          for (String[] cloth : clothes) {
              String key = cloth[1];
              map.put(key, map.getOrDefault(key, 0) + 1);
          }
    
          int answer = 1;
    
          for(String key : map.keySet()) {
              answer *= (map.get(key) + 1); 
          }
    
          return answer - 1;
      }
    }
    ```
    
    * HashMap을 key는 옷의 종류, value는 개수로 구성한다.
    
    * 경우의 수를 한 번 계산 해보자.
    
        * headgear는 총 2개 있으니, 총 3 가지 경우의 수가 있다.
    
            * 1번을 입는다, 2번을 입는다, headgear를 아무것도 입지 않는다.
    
        * eyewear는 총 1개 있으니, 총 2 가지의 경우의 수가 있다.
    
            * 1번을 입는다, eyewear를 아무것도 입지 않는다.
    
        * 따라서 총 3 x 2 가지의 경우의 수 인 6 가지가 존재하고, 이 중 한 가지는 headgear도 입지 않고 eyewear도 입지 않은 경우가 있기 때문에 이 경우를 제외한 5 가지가 정답이 된다.
