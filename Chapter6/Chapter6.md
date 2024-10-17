# Chapter 6. 완전 탐색 (Brute Force)

## 1. 개념 설명

* `완전 탐색 (Brute Force)` : 모든 경우의 수를 다 해보는 것을 말한다.

    * 경우의 수를 구할 때 순열 또는 조합을 사용할 수 있다.

        * 순서와 상관 있다면 순열이며 순서와 상관 없다면 조합이다.

    * 완전 탐색은 반복문 또는 재귀 함수를 활용하여 구현할 수 있다.

## 2. 연습 문제

### 2-1. 프로그래머스 - 최소직사각형

```java
public class Solution {
  public int solution(int[][] sizes) {
      int maxWidth = 0;
      int maxHeight = 0;

      for (int i = 0; i < sizes.length; i++) {
          int width = Math.max(sizes[i][0], sizes[i][1]); // 긴 부분
          int height = Math.min(sizes[i][0], sizes[i][1]); // 짧은 부분

          maxWidth = Math.max(maxWidth, width);
          maxHeight = Math.max(maxHeight, height);
      }

      return maxWidth * maxHeight;
  }
}
```

### 2-2. 프로그래머스 - 전력망을 둘로 나누기

```java

```
