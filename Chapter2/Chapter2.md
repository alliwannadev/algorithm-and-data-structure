# Chapter 2. 배열

## 1. 개념 설명

* `배열 (Array)`은 데이터가 연속적(순차적)으로 저장되어 있는 자료구조를 말한다.

    * 배열은 한 번 만들면 그 길이를 변경할 수 없다.

    * 시간 복잡도는 다음과 같다.

        * 접근은 `O(1)`, 탐색은 `O(N)`, 맨 앞과 중간에서의 삽입 및 삭제는 `O(N)`이다.  (단, 맨 뒤에서 삽입 및 삭제를 하는 경우에는 `O(1)`이다.)

* `동적 배열 (Dynamic Array)`은 자동으로 길이가 조절되는 배열을 말한다.

    * 대표적으로 자바에서는 `ArrayList`가 있다.

## 2. 연습 문제

### 2-1. 프로그래머스 - 두 개 뽑아서 더하기

```java
import java.util.*;

class Solution {
    public int[] solution(int[] numbers) {
      Set<Integer> uniqueNumbers = new HashSet<>();
      for (int i = 0; i < numbers.length; i++) {
          for (int j = 0; j < numbers.length; j++) {
              if (i == j) {
                  continue;
              }
              uniqueNumbers.add(numbers[i] + numbers[j]);
          }
      }

      return uniqueNumbers.stream()
              .sorted()
              .mapToInt(Integer::intValue)
              .toArray();
    }
}
```

### 2-2. 프로그래머스 - 두 개 뽑아서 더하기

* 방법 1. 2차원 배열을 직접 만들어 풀이하기 - 메모리 초과

    ```java
    import java.util.*;
    
    class Solution {
        public int[] solution(int n, long left, long right) {
            int[][] numbers2DArr = new int[n][n];
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < n; j++) {
                    numbers2DArr[i][j] = Math.max(i + 1, j + 1);
                }
            }
    
            List<Integer> numbers = new ArrayList<>();
            for (int i = 0; i < numbers2DArr.length; i++) {
                for (int j = 0; j < numbers2DArr[i].length; j++) {
                    numbers.add(numbers2DArr[i][j]);
                }
            }
    
            List<Integer> answer = numbers.subList((int) left, (int) right + 1);
            return answer.stream()
                    .mapToInt(Integer::intValue)
                    .toArray();
        }
    }
    ```

* 방법 2. 규칙을 찾아서 1차원 배열(ArrayList)로 풀이하기
    
    ```java
    import java.util.*;
    
    class Solution {
        public int[] solution(int n, long left, long right) {
            List<Long> numbers = new ArrayList<>();
            for (long i = left; i <= right; i++) {
                long row = i / n + 1;
                long col = i % n + 1;
                numbers.add(Math.max(row, col));
            }
    
            return numbers.stream()
                    .mapToInt(Long::intValue)
                    .toArray();
        }
    }
    ```

