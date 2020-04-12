---
layout: single
date: 2020-04-10 23:00 +0900
title: "Strassen Algorithm"
---

# **스트라센 알고리즘**

> **스트라센 알고리즘을 배우기 전에, 먼져 스트라센 알고리즘이 어떻게 생기게 되었는지 알 필요가 있다.** 

* 아무 크기의 행렬이 있다고 가정해보자 

  행렬 계산법만 아는 사람이라면 누구든지 시간을 투자해서 구할수 있을것이다.

  ex)                                                    


| 3(A1,1) | 2(A1,2) | -4(B1,1) | -2(B1,2) | -8(C1,1) | -12(C1,2) |
| :-----: | :-----: | :------: | :------: | :------: | :-------: |
| 0(A2,1) | 2(A2,2) | 2(B2,1)  | -3(B2,2) | 4(C2,1)  | -6(C2,2)  |

{% highlight ruby %}

(가)
A,B 가 2X2 행렬 이라고 생각해보면 

C1,1 = A1,1 X B1,1 + A1,2 X B2,1

C1,2 = A1,1 X B1,2 + A1,2 X B2,2

C2,1 = A2,1 X B1,1 + A2,2 X B2,1

C2,2 = A2,1 X B1,2 + A2,2 X B2,2 이 된다.

{% endhighlight %}



이것이 행렬을 구하는 계산법 이다.

​	** (가)에서, 총 8번의 곱셈과 4번의 덧셈이 발생했다. **

***

* 어느정도 크기의 행렬은 연산하는데 어려움이 없을 것이다.

  하지만 행렬의 크기가 커지면 커질수록 연산하는데에는  많은 시간이 필요하게 될 것이다. 

  연산하는데 시간을 단축하기 위해 개발된 알고리즘이 스트라센 알고리즘이다.

> **스트라센 알고리즘을 만들기 위해서는 스트라센 알고리즘이 어떤 방식으로 계산 되는지 알고있어야 한다**

* 위에 예시를 계산하면서 (가)라는 과정과 결과를 얻을 수 있었다. 

  (가)를 통해 **8번의 곱셈과 4번의 덧셈이 발생 했다는것도 알 수 있었다.** 

  일반적으로 곱셈이 많아질수록 어떤 식이든 계산하기 까다로워 진다.

  스트라센 알고리즘은 우리가 흔히 알고있는, 행렬을 계산하는 방법보다 곱셈 발생 횟수를 줄여서 계산했다.

{% highlight ruby %}

(나)

M1 = (A1,1 + A2,2) x (B1,1 + B2,2)

M2 = (A2,1 + A2,2) x (B1,1)

M3 = (A1,1) x (B1,2 - B2,2)

M4 = (A2,2) x (B2,1 - B1,1)

M5 = (A1,1 + A1,2) x (B2,2)

M6 = (A2,1 - A1,1) x (B1,1 + B1,2)

M7 = (A1,2 - A2,2) x (B2,1 + B2,2)

{% endhighlight %}



(나)를 통해



{% highlight ruby %}

(다)

C1,1 = M1 + M4 - M5 + M7

C1,2 = M3 + M5

C2,1 = M2 + M4

C2,2 = M1 - M2 + M3 + M6

{% endhighlight %}



(다)라는 결론에 다가갈수 있다.

* (나) 와 (다) 를 통해 총 7번의 곱셈과 18번의 덧셈뺏셈이 발생했다는 것을 알 수 있다. 

* 같은 행렬 계산에서 스트라센 알고리즘 계산 방법을 사용하게 되면 곱하기 계산을 덜 하고 덧셈뺏셈을 더 하게된다.**(곱하기를 덜 하는것보단 덧셈뺏셈을 더 하는 횟수가 많다)**

   행렬의 크기가 크지 않을때는 여러번 덧셈뺏셈을 하는것 보다는 까다롭더라도 곱셈을 조금 더 하는것이 효율적일 것이다.**((가) 방법을 사용한다)** 

  하지만 행렬의 크기가 클때는 곱하기를 하는 시간보다 덧셈뺏셈을 더 하는 시간이 더 효율적일 것이다**((나,다)방법을 사용한다.)** 



![https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fssl.pstatic.net%2Fimages.se2%2Fsmedit%2F2015%2F10%2F7%2Fifgkdfr2qjsuqs.jpg%22&type=w2]

 ![https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fssl.pstatic.net%2Fimages.se2%2Fsmedit%2F2015%2F10%2F7%2Fifgkf5tz3m7lu0.jpg%22&type=w2]

(가) 방법을 수열로 나타낸 것이다. `크기가 n x n인 두 정사각행렬` a,b 의 곱을 c로 나타냈다.

 하나의 c 원소를 구할때, 곱셈은 n번 발생하고 덧셈은 (n-1)번 발생한다. 

전체 c를 구할 때 곱셈은 n[^3] 번, 덧셈은 n[^2] (n-1)번 하게 된다. 

(나,다) 를 통해서도 점화식을 만들 수 있다. `크기가 n x n의 정사각 행렬의 크기는 2[^k] x 2[^k]이다. `   !(https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fssl.pstatic.net%2Fimages.se2%2Fsmedit%2F2015%2F10%2F7%2Fifgmttx5uq6pap.jpg%22&type=w2)  !(https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fssl.pstatic.net%2Fimages.se2%2Fsmedit%2F2015%2F10%2F7%2Fifgmve7rpku5qa.jpg%22&type=w2)

따라서, 행렬의 곱셈은 n/2 x n/2 크기의 행렬을 7번 곱하고, n/2 x n/2크기의 행렬을 18번 더한다. 더하기를 생략하고, 점화식으로 나타내보면 ![img](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fssl.pstatic.net%2Fimages.se2%2Fsmedit%2F2015%2F10%2F7%2Fifgn49i0ovefhs.jpg%22&type=w2)![img](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fssl.pstatic.net%2Fimages.se2%2Fsmedit%2F2015%2F10%2F7%2Fifgn4t6hcsos40.jpg%22&type=w2)

![img](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fssl.pstatic.net%2Fimages.se2%2Fsmedit%2F2015%2F10%2F7%2Fifgmntt48gttax.jpg%22&type=w2)![img](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fssl.pstatic.net%2Fimages.se2%2Fsmedit%2F2015%2F10%2F7%2Fifgn5g6l0g03ie.jpg%22&type=w2)

이 식을 통해 ![img](https://dthumb-phinf.pstatic.net/?src=%22https%3A%2F%2Fssl.pstatic.net%2Fimages.se2%2Fsmedit%2F2015%2F10%2F7%2Fifgnj7vpdn8pdg.jpg%22&type=w2) 인 것을 알 수 있다.

대략적인 수로 비교해보면 일반적인 행렬 계산법으로는 n[^3]의 효율을 볼 수 있고, 스트라센 알고리즘은 n[^2.807]의 효율을 볼 수 있다. 

하지만 이건 곱하기만 생각했을 때의 경우이다. 

위에서도 말했듯이 상황에 맞게 적절한 계산법을 사용하는 것이 가장 현명 할 것이다.

```
이 식들에는 n x n 이 정사각 행렬이라는 가정이 있었다.정사각 행렬이 아닐때에는 가로 세로에 0으로 채워진 가로, 세로 줄을 추가해서 정사각행렬로 만들어 계산 하면 된다.
```





{% endhighlight %}

>**스트라센 알고리즘**

```
public class Strassen {

 

       public static void main(String[] args) {

            

             int n = 1024;

            

             int[][] x = initMetrix(n);

             int[][] y = initMetrix(n);

            

             int[][] nomalResult = Strassen.metrixMul(n, x, y);

            

             Strassen strassen = new Strassen();

            

             int[][] strassenReslut = strassen.excuteStrassen(x, y);

            

             boolean checkMetrix = true;

             for (int i = 0; i < n; i++) {

                   

                    for (int j = 0; j < n; j++) {

                          

                           if (nomalResult[i][j] != strassenReslut[i][j]) {

                                 checkMetrix = false;

                           }

                    }

                   

             }

            

            

             System.out.println("결과 : " + checkMetrix);

            

       }

      

       public static int[][] initMetrix(int n) {

            

             Random r = new Random();

            

             int[][] resultMetrix = new int [n][n];

            

             for (int i = 0; i < n; i++) {

                    for (int j = 0; j < n; j++) {

                           resultMetrix[i][j] = r.nextInt(30);

                    }

             }

             return resultMetrix;

       }

      

      

       public int[][] excuteStrassen(int[][] metrixX, int[][] metrixY) {

            

             // 스트라센의 경우 n*n 행렬로 연산

             int n = metrixX.length;

            

             // 임계 차원 보다 작을 경우 기존 메트릭스 곱으로 풀이

             if (n <= 2) {

                    return metrixMul(n, metrixX, metrixY);

             }

            

             // 4 등분

             int rank = n / 2;

            

             // 배열 분해

             int[][] a11 = subMetrix(rank, 0, 0, metrixX);

             int[][] a12 = subMetrix(rank, 0, rank, metrixX);

             int[][] a21 = subMetrix(rank, rank, 0, metrixX);

             int[][] a22 = subMetrix(rank, rank, rank, metrixX);

             int[][] b11 = subMetrix(rank, 0, 0, metrixY);

             int[][] b12 = subMetrix(rank, 0, rank, metrixY);

             int[][] b21 = subMetrix(rank, rank, 0, metrixY);

             int[][] b22 = subMetrix(rank, rank, rank, metrixY);

                          

             int[][] m1 = excuteStrassen(metrixSum(a11, a22), metrixSum(b11, b22)); // m1=(a11+a11)(b11+b22)

             int[][] m2 = excuteStrassen(metrixSum(a21, a22), b11); // m2=(a21+a22)b11

             int[][] m3 = excuteStrassen(a11, metrixSub(b12, b22)); // m3=a11(b12-b22)

             int[][] m4 = excuteStrassen(a22, metrixSub(b21, b11)); // m4=a22(b21-b11)

             int[][] m5 = excuteStrassen(metrixSum(a11, a12), b22); // m5=(a11+a12)b22

             int[][] m6 = excuteStrassen(metrixSub(a21, a11), metrixSum(b11, b12)); // m6=(a21-a11)(b11+b12)

             int[][] m7 = excuteStrassen(metrixSub(a12, a22), metrixSum(b21, b22)); // m7=(a12-a22)(a21+b22)

            

             // 결과 생성

             int[][] c11 = metrixSum(metrixSub(metrixSum(m1, m4), m5), m7); // c11 = m1 + m4 - m5 + m7

             int[][] c12 = metrixSum(m3, m5); // c12 = m3 + m5

             int[][] c21 = metrixSum(m2, m4); // c21 = m2 + m4

             int[][] c22 = metrixSum(metrixSub(metrixSum(m1, m3), m2), m6); // c22 = m1 + m3 - m2 + m6

            

             // 결합

             return combin(c11, c12, c21, c22);

       }

      

       private int[][] combin(int[][] c11, int[][] c12, int[][] c21, int[][] c22) {

             int n = c11.length;

 

             int[][] resultMetrix = new int [n*2][n*2];

            

             for (int i = 0; i < n; i ++) {

                    for (int j = 0; j < n; j++) {

                           resultMetrix[i][j] = c11[i][j]; // 11

                           resultMetrix[i][j + n] = c12[i][j]; // 12

                           resultMetrix[i + n][j] = c21[i][j]; // 21

                           resultMetrix[i + n][j + n] = c22[i][j]; // 22

                    }

             }

             return        resultMetrix;

       }

      

       private int[][] subMetrix(int n, int startX, int startY, int[][] metrix) {

            

             int[][] subMetirx = new int[n][n];

            

             for (int i = 0, x = startX; i < n; i++, x++) {

                    for (int j = 0, y = startY; j < n; j++, y++) {

                           subMetirx[i][j] = metrix[x][y];

                    }

             }

             return subMetirx;

       }

      

       private int[][] metrixSum(int[][] metrixX, int[][] metrixY) {

             int n = metrixX.length;

             int[][] metrixResult = new int[n][n];

            

             for (int i = 0; i < n; i++) {

                    for (int j = 0; j < n; j++) {

                           metrixResult[i][j] = metrixX[i][j] + metrixY[i][j];

                    }

             }

            

             return metrixResult;

       }

      

       private int[][] metrixSub(int[][] metrixX, int[][] metrixY) {

             int n = metrixX.length;

             int[][] metrixResult = new int[n][n];

            

             for (int i = 0; i < n; i++) {

                    for (int j = 0; j < n; j++) {

                           metrixResult[i][j] = metrixX[i][j] - metrixY[i][j];

                    }

             }

             return metrixResult;

       }

      

       public static int[][] metrixMul(int n, int[][] metrixX, int[][] metrixY) {

            

             int [][] result = new int[n][n];

            

             for (int i = 0; i < n; i++) {

                    for (int j = 0; j < n; j++) {

                           for (int k = 0; k < n; k++) {

                                 result[i][j] += metrixX[i][k] * metrixY[k][j];

                           }

                    }

                   

             }

            

             return result;

       }

}
```







[^3]: 