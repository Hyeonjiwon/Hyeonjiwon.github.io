---
title: '[Programmers] 코딩테스트 연습' 
excerpt: "Level 1"
categories:
    - Algorithm

tag:
    - Programmers
    - Algorithm

author_profile: true    #작성자 프로필 출력 여부

last_modified_at: 2021-04-02T19:00:00+09:00

toc: true   #Table Of Contents 목차 

toc_sticky: true
---

## K번째수

__문제__

배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다.

예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면

1. array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.
2. 1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.
3. 2에서 나온 배열의 3번째 숫자는 5입니다.

배열 array, [i, j, k]를 원소로 가진 2차원 배열 commands가 매개변수로 주어질 때, commands의 모든 원소에 대해 앞서 설명한 연산을 적용했을 때 나온 결과를 배열에 담아 return 하도록 solution 함수를 작성해주세요.

__제한사항__

- array의 길이는 1 이상 100 이하입니다.
- array의 각 원소는 1 이상 100 이하입니다.
- commands의 길이는 1 이상 50 이하입니다.
- commands의 각 원소는 길이가 3입니다.

__입출력 예__

| array | commands | return |
|---|---|---|
| [1, 5, 2, 6, 3, 7, 4] | [[2, 5, 3], [4, 4, 1], [1, 7, 3]] | [5, 6, 3] |

__풀이__

```java
import java.util.*;

class Solution {
    public static int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];

        for (int i = 0; i < commands.length; i++) {
            ArrayList<Integer> list = new ArrayList<Integer>();

            for (int j = commands[i][0]; j <= commands[i][1]; j++) {
                list.add(array[j-1]);
            }

            Collections.sort(list);
            int k = list.get(commands[i][2]-1);
            answer[i] = k;
        }

        return answer;
    }

    public static void main(String[] args) { 
        // test case
        int[] array = {1, 5, 2, 6, 3, 7, 4};
        int[][] commands = { {2, 5, 3}, {4, 4, 1}, {1, 7, 3} };

        int[] result = solution(array, commands);

        for (int i: result) {     
            System.out.println(i); 
        }
    }
}
```

<br>

## 완주하지 못한 선수

__문제__

수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.

__제한사항__

- 마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.
- completion의 길이는 participant의 길이보다 1 작습니다.
- 참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.
- 참가자 중에는 동명이인이 있을 수 있습니다.

__입출력 예__

| participant | completion | return |
|---|---|---|
| ["leo", "kiki", "eden"] | ["eden", "kiki"] | "leo" |
| ["marina", "josipa", "nikola", "vinko", "filipa"] | ["josipa", "filipa", "marina", "nikola"] | "vinko" |
| ["mislav", "stanko", "mislav", "ana"] | ["stanko", "ana", "mislav"] | "mislav" |

__풀이__

```java
import java.util.*;

class Solution {
    public static String solution(String[] participant, String[] completion) {
        String answer = "";
        HashMap<String, Integer> hm = new HashMap<String, Integer>();

        for (String name : participant) {
            hm.put(name, hm.getOrDefault(name, 0) + 1);
        }

        for (String name : completion) {
            if(hm.containsKey(name)){
                hm.put(name, hm.get(name) - 1);
            }
        }

        for (String name : hm.keySet()) {
            if(hm.get(name) == 1) {
                answer = name;
            }
        }

        return answer;
    }

    public static void main(String[] args) { 
        // test case
        String[] participant = {"mislav", "stanko", "mislav", "ana"};

        String[] completion = {"stanko", "ana", "mislav"};
        System.out.println(solution(participant, completion)); 
    }
}
```

<br>

## 2016년

__문제__

2016년 1월 1일은 금요일입니다. 2016년 a월 b일은 무슨 요일일까요? 두 수 a ,b를 입력받아 2016년 a월 b일이 무슨 요일인지 리턴하는 함수, solution을 완성하세요. 요일의 이름은 일요일부터 토요일까지 각각  [ SUN, MON, TUE, WED, THU, FRI, SAT ]

입니다. 예를 들어 a=5, b=24라면 5월 24일은 화요일이므로 문자열 "TUE"를 반환하세요.

__제한사항__

- 2016년은 윤년입니다.
- 2016년 a월 b일은 실제로 있는 날입니다. (13월 26일이나 2월 45일같은 날짜는 주어지지 않습니다)

__입출력 예__

| a | b | result |
|---|---|---|
| 5 | 24 | "TUE" |

__풀이__

```java
class Solution {
    
    public static String solution(int a, int b) {
        String answer = "";

        int[] month = { 31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
        String[] dayOfweek = { "THU", "FRI", "SAT", "SUN", "MON", "TUE", "WED" };

        int d = 0, result = 0;

        for (int i = 0; i < (a -1); i++) {
            d = d + month[i];
       }

        result = ((d + b) % 7);
        answer = dayOfweek[result];

        return answer;
    }

    public static void main(String[] args) { 
        // test case
        int a = 6;
        int b = 10;
        
        System.out.println(solution(a, b)); 
    }
}
```

<br>

## 모의고사

__문제__

수포자는 수학을 포기한 사람의 준말입니다. 수포자 삼인방은 모의고사에 수학 문제를 전부 찍으려 합니다. 수포자는 1번 문제부터 마지막 문제까지 다음과 같이 찍습니다.

1번 수포자가 찍는 방식: 1, 2, 3, 4, 5, 1, 2, 3, 4, 5, ...
2번 수포자가 찍는 방식: 2, 1, 2, 3, 2, 4, 2, 5, 2, 1, 2, 3, 2, 4, 2, 5, ...
3번 수포자가 찍는 방식: 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, ...

1번 문제부터 마지막 문제까지의 정답이 순서대로 들은 배열 answers가 주어졌을 때, 가장 많은 문제를 맞힌 사람이 누구인지 배열에 담아 return 하도록 solution 함수를 작성해주세요.

__제한사항__

- 시험은 최대 10,000 문제로 구성되어있습니다.
- 문제의 정답은 1, 2, 3, 4, 5중 하나입니다.
- 가장 높은 점수를 받은 사람이 여럿일 경우, return하는 값을 오름차순 정렬해주세요.

__입출력 예__

| answers | return |
|---|---|
| [1,2,3,4,5] | [1] |
| [1,3,2,4,2] | [1,2,3] |

__풀이__

```java
import java.util.ArrayList;

class Solution {
    public static int[] solution(int[] answers) {
        int[] answer = {};

        int[] tnvhwk1 = { 1, 2, 3, 4, 5, 1, 2, 3, 4, 5 }; 
        int[] tnvhwk2 = { 2, 1, 2, 3, 2, 4, 2, 5 }; 
        int[] tnvhwk3 = { 3, 3, 1, 1, 2, 2, 4, 4, 5, 5 }; 

        int[] count = new int[3];

        for (int i = 0; i < answers.length; i++) {
            if ((tnvhwk1[i % tnvhwk1.length]) == answers[i]) {
                count[0]++;
            }
            if (tnvhwk2[i % tnvhwk2.length] == answers[i]) {
                count[1]++;
            }
            if (tnvhwk3[i % tnvhwk3.length] == answers[i]) {
                count[2]++;
            }
        }

        ArrayList<Integer> list = new ArrayList<Integer>();

        // 최고 점수 찾기
        int max = Math.max(Math.max(count[0], count[1]), count[2]); 

        // 최고점자만 add 
        if(max==count[0]) list.add(1); 
        if(max==count[1]) list.add(2);
        if(max==count[2]) list.add(3);

        System.out.println("list " + list);
        
        // answer 리스트 길이만큼 초기화
        // answer = list.toArray(new Int[list.size()]); => toArray는 Object 형식으로 반환
        // Stream API를 사용하면 실행 시간이 오래걸림
        answer = list.stream().mapToInt(i -> i).toArray();

        return answer;
    }

    public static void main(String[] args) { 
        // test case
        int[] answers = { 1, 2, 3, 4, 5 };

        int[] answer = solution(answers);

        for (int i = 0; i < answer.length; i++) {
            System.out.println(answer[i]); 
        }
    }
}
```

<br>

## 2016년

__문제__

2016년 1월 1일은 금요일입니다. 2016년 a월 b일은 무슨 요일일까요? 두 수 a ,b를 입력받아 2016년 a월 b일이 무슨 요일인지 리턴하는 함수, solution을 완성하세요. 요일의 이름은 일요일부터 토요일까지 각각  [ SUN, MON, TUE, WED, THU, FRI, SAT ]

입니다. 예를 들어 a=5, b=24라면 5월 24일은 화요일이므로 문자열 "TUE"를 반환하세요.

__제한사항__

- 2016년은 윤년입니다.
- 2016년 a월 b일은 실제로 있는 날입니다. (13월 26일이나 2월 45일같은 날짜는 주어지지 않습니다)

__입출력 예__

| a | b | result |
|---|---|---|
| 5 | 24 | "TUE" |

__풀이__

```java
class Solution {
    
    public static String solution(int a, int b) {
        String answer = "";

        int[] month = { 31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
        String[] dayOfweek = { "THU", "FRI", "SAT", "SUN", "MON", "TUE", "WED" };
        int d = 0, result = 0;

        for (int i = 0; i < (a -1); i++) {
            d = d + month[i];
       }

        result = ((d + b) % 7);
        answer = dayOfweek[result];

        return answer;
    }

    public static void main(String[] args) { 
        // test case
        int a = 6;
        int b = 10;
        
        System.out.println(solution(a, b)); 
    }
}
```

<br>

## 수박수박수박수박수박수?

__문제__

길이가 n이고, "수박수박수박수...."와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 예를들어 n이 4이면 "수박수박"을 리턴하고 3이라면 "수박수"를 리턴하면 됩니다.

__제한사항__

- n은 길이 10,000이하인 자연수입니다.

__입출력 예__

| n | return |
|---|--------|
| 3 | "수박수" |
| 4 | "수박수박" |

__풀이__

```java
class Solution {
    public static String solution(int n) {
        String answer = "";

        StringBuilder sb = new StringBuilder();

        for (int i = 0; i <= (n/2); i++) {
            sb.append("수박");
        }
        
        answer = sb.substring(0, n);
        
        return answer;
    }

    public static void main(String[] args) { 
        // test case
        int n = 3;

        System.out.println(solution(n));
    }
}
```

<br>

## 

__문제__



__제한사항__

- 


__입출력 예__



__풀이__

```java

```

<br>

## 참고

> [출처: 프로그래머스 코딩 테스트 연습](https://programmers.co.kr/learn/challenges)