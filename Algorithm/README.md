[Algorithms]
======================



# 1. Interval Scheduling



## 1.1 다양한 접근법

- Earliest start time (Earlist Job First) : 시작 시간이 가장 빠른 작업들로 스케쥴링, 하지만 이는 항상 최적해를 구하지 않는다. 정확하지 않은 알고리즘
- Shortest interval (Shortest Job First) : 가장 짧은 구간(시간이 적게 걸리는)을 가진 작업들로 스케쥴링, 하지만 이 또한 반례가 존재. 항상 최적해를 구할 수 없다.
- Earilest finish time : 작업 종료 시간이 가장 빠른 작업들로 스케쥴링, 몇가지 예시들을 생각해보면 최적이라는 것을 알 수 있다. [증명 1.2]

```
* 스케쥴링 문제의 해는 구간들의 부분집합으로 이루어진다. (Exaustive Scheduling)
  즉, 2^n개의 부분집합 각각 모두를 고려하면 해가 반드시 하나는 존재한다.
  하지만 시간복잡도가 커 문제를 해결하는데 시간이 오래걸린다.
```

-> 이보다 더 빠른 시간 안에 해결할 수 있는가?
   - Earilest finish time (Optimal Scheduling) : 수학적 귀납법으로 재귀적인 증명이 가능하다. 어떤 작업 E를 제외하고 최적의 해인 부분집합 I'이 있다고 생각할 때, (가정)
         작업 시간이 겹치는 다른 작업들(E, E', E'', ...)과 비교했을 때 가장 먼저 끝나는 작업 E를 포함하는 것이 최적의 해라는 것을 증명하면 된다.



## 1.2 최적의 접근법에 대한 증명과 고찰
```
즉, E를 포함하는 부분집합이 최대 구간의 수를 갖는다를 증명 (최대 구간의 수를 갖는 독립집합)  
// (독립집합 (Independent Set) : 집합 간에 서로소가 되는 집합)
```

: 그렇다면 E를 포함하지 않는 부분집합이 최적의 해가 아니라고 할 때 (E'을 포함한 부분집합이 최적이라면) E를 포함하도록 변형이 가능하다면 이를 증명할 수 있다.
E와 E' 작업을 뺀 부분집합은 E와 E'의 작업시간과는 겹치지 않는다. 그러므로 E'을 빼고 E를 포함해도 구간의 수는 똑같이 최적임을 알 수 있다. E를 포함한 부분집합과
E' 포함한 부분집합의 구간의 수는 같다는 말.

```
* 쉽게 생각해보면 빨리 시작하는 작업을 고르는 알고리즘과는 다르게 현재 가장 빨리 끝나는 작업(E)을 매 순간에 고르게 됐을 때,  
선택된 작업은 시작시간이 어떻게 됐든 간에 매 순간에 가장 빨리 끝나는 작업(E)을 고르는 것을 반복했기 때문에  
이전에 고른 가장 빨리 끝나는 작업(E') 시간이 현재 고른 가장 빨리 끝나는 작업(E)의 시작 시간보다 늦을 수가 없다는 이야기이다.  
즉, 가장 빨리 끝나는 작업들을 계속해서 고르게 되면 처리할 수 있는 가장 많은 작업의 수를 고를 수 있다는 것이다.
```



## 1.3 시간복잡도

- 시간복잡도는 O(NlogN)에 가능.

1) 입력 데이터를 정렬
2) 입력 데이터가 들어올 때마다 힙(Heap) 자료구조에 삽입하여 가장 빨리 끝나는 작업 시간을 가진 데이터가 먼저 pop되도록 구성

위의 두 가지 방법이 있다. 이후 각각 작업시간을 비교하여 겹치는지 여부를 확인해주며 최대 처리가능한 작업의 개수를 세면 된다.



## 1.4 심화



### 1.4.1 작업들에 가중치(비용)이 존재한다면?

: 결론부터 말하면 정점에 가중치가 존재하는 Interval Graph에서 특정한 가중독립집합을 구하는 문제가 된다.  
// 독립집합 <=> 클릭 (Clique) : 모든 가능한 변이 존재하는 꼭짓점들의 부분집합  
```
여기서 말하는 클릭은 Interval Graph에서 정점의 모든 쌍에 대해 간선이 존재하는 정점의 부분집합.  
* Coloring Problem : 지도가 있을 때 인접한 구간이면 서로 다른 색으로 색칠(서로 배타적인 구간을 최소 개수로 나눠라)하는 문제  
-> NP-Complete  
(구간을 정점으로 하고 인접한 구간에 대해 간선을 구성하면 최소 개수의 독립집합으로 그래프를 칠하는 문제라고 볼 수 있다.)  
Interval Graph에서는 Coloring 부분집합의 수와 Clique의 수가 같다. 평면 그래프는 어떤 경우이든 간에 4가지 색으로 해결 가능.  
star형 그래프의 경우는 5가지 색이 필요하다.  
```

모든 부분집합을 탐색할 필요없이 구간들의 관계를 나타내는 방향그래프를 구성한다.

왼쪽에 있는 구간에서 부터 오른쪽에 있는 구간으로 사이클이 없는 방향그래프(Directed Acyclic Graph)로 구성이 된다. // DAG라는 것은 다른 그래프들보다 빠른 시간 안에 해결 가능한 문제로 만들 수 있다는 의미.

위의 DAG를 위상정렬한 뒤, 정점의 가중치의 합이 최대가 되는 최대가중경로를 구하면 된다.
최대가중경로를 구하는 알고리즘은 모든 정점들에서 그 정점을 지나는 순간에 가장 큰 가중치를 가질 때의 값을 배열에 저장한 뒤,
배열에서 가장 큰 값에서 시작하여 역산(정점의 가중치는 빼고 해당 값을 배열에서 찾는 작업의 반복)으로 경로를 구할 수 있다.
구간에 대한 문제를 그래프 문제로 변형하였기 때문에 최악의 경우 O(N^2)의 시간복잡도를 갖는다.

* 조금 더 빠른 시간 안에 문제를 해결할 수 있는가? 다른 방안의 변형이 가능한가?

구간들의 관계를 나타내는 그래프를 전부 구성할 필요가 없다. 왼쪽 끝점 or 오른쪽 끝점을 기준으로 정렬하면 DAG를 구성하여 위상정렬할 필요없이 구간을 순차적으로 볼 수 밖에 없다.  
이것이 라인 스위핑 [Algorithm 2]  
구간을 순차적으로 보면서  

1. 겹치는 구간이 아닌지를 확인  
2. 이전 부분집합들 안에서 최대의 가중치의 값만을 따로 저장하여 확인  
3. 각 구간에서 가능한 경우에 대해서 가중치의 합들을 짝(끝점, 가중치의 합)을 지어 가장 먼저 오는 끝점을 기준으로 하는 최소힙에 저장한다. (현재 보고있는 구간의 시작점 좌표가 이전 구간들의 끝점 좌표를 비교하여 겹치는 구간을 확인해주기 위함.)  
4. 반복해서 힙에 push, pop을 반복하여 왼쪽부터 오른쪽 구간까지 모두 확인하여 최대 가중치를 구해주면 된다. 위에 나온 가중치를 합하는 과정에 대한 기록과 역산을 포함하면 경로 또한 구할 수 있다.  
> @ Search Keyword : 구간경로에서 최대가중치를 찾는 알고리즘



### 1.4.2 장소에 따른 제약조건이 존재한다면?



# 2. Line Sweep (Plane Sweep) 평면 소거법

가장 기본적인 라인 스위핑으로는 왼쪽에서 오른쪽 혹은 오른쪽에서 왼쪽으로 진행방향을 잡고 구간을 의미하는 시작점과 끝점들을 확인하며 문제에 맞게 해결하는 알고리즘.



# 3. Binary Search (Parametric Search)

양 끝 인덱스를 기준으로 하여 left, right index 값을 통해 middle 인덱스를 구해 middle에 저장되어 있는 값을 기준으로 구간을 반 씩 줄여가며 탐색하는 알고리즘.



## 3.1 One-sided Binary Search

- Idea : left나 right 인덱스 둘 중 하나가 무한대라는 큰 값을 갖는다면(열린 구간이라면) 열린 구간 쪽으로 limit를 두 배씩 늘려가면서 이진 탐색을 진행한다.  



# 4. Bitmasking

데이터의 일정한 규칙을 2진수에 대응하여 정수 하나 혹은 하나의 배열에 여러 정보를 저장하여 공간복잡도를 절약하는 알고리즘. 연산 또한 &(AND), |(OR), ^(XOR) 등 비트 연산으로 간결해진다.



# 5. Harmonic number
Hn = 1/1 + 1/2 + 1/3 + ... + 1/n = ln(n) + euler's constant (오일러 상수)  
```
ln(n+1) <= Hn <= ln(n) + 1
```



# 6. Segment Tree (Range Minimum Query)

O(N) 공간복잡도를 이용, O(logN) 시간에 질의(Query)에 대한 답을 내는 것과 갱신(Update)가 가능하다. (구간 내의 최대/최소값 등등)



## 6.1 Lazy Propagation

- Idea : 기존의 세그먼트 트리에서 모든 요소에 값을 증감시키는 경우(Range Inc / Dec Update)에는 결국 트리 전체 노드에 대해 Inc / Dec 연산이 필요하다. 총 걸리는 시간은 O(NlogN) 시간.  
   이 때, 자식 노드에게 전달되어야 할 정보를 부모 노드에 저장해놓고 이 다음에 자식 노드들에 대해 정보가 필요한 쿼리가 들어올 경우에 그 정보를 전달해주자는 Idea.  
    부모 노드는 자식 노드가 몇 개 있는지도 알고, 늦게 전달되는 정보(값의 변화)에 대해서도 알고 있으므로  
    그에 따라 적절히 곱셈(노드 갯수 * 값의 변화)을 해서 자신이 갖고 있는 값과 더 해주면 정확한 결과도 알 수 있다.  
    만약 Range Update나 Range Query가 계속해서 이루어지는 도중에 이미 lazy 값(배열에 따로 저장)이 존재하고 자식 노드들 중 하나의 정보만 필요하다면  
    이 경우에는 해당 lazy 값을 정확한 정보가 필요한 노드의 높이까지만 전달을 하고, 반대쪽 자식 노드에도 높이 1씩 lazy 값을 전달해준다.  
    이후에 기존의 세그먼트 트리처럼 값을 더해주면서 올라오면 같은 방식으로 노드마다 정확한 값을 가질 수 있게 된다. lazy 값은 단말 노드의 값을 갱신하면 소멸된다.  



# 7. Bipartite Graph (이분 그래프)

두 개의 독립집합으로 나눌 수 있는 그래프. (예를 들어 모든 정점을 빨강색과 파랑색으로 색칠한다면 모든 변이 빨강색과 파랑색 꼭지점을 포함하도록 색칠할 수 있는 그래프.)  
$ BOJ-1707 이분 판정 문제. 2개의 독립집합으로 나타낼 수 있다면 이분그래프라고 할 수 있다.



# 8. Geometry (기하, Computational Geometry : 계산 기하)

일반적으로 알고리즘에서는 계산 기하 문제를 많이 다룬다.



## 8.1 Point
```c++
struct Point_i {
	int x, y;
	Point_i() { x = y = 0; }
	Point_i(int _x, int _y) : x(_x), y(_y) {}
}; // 좌표가 정수 값으로 주어질 때

struct Point {
	double x, y;

	Point() { x = y = 0.0; }

	Point(double _x, double _y) : x(_x), y(_y) {}

	bool operator < (Point p) const { // 연산자 재정의, EPS : 1e^-9와 같은 아주 작은 값 (문제에 따라 오차 범위 지정)
		if (fabs(x - p.x) > EPS) return x < p.x; // fabs() : double 자료형의 절대값
		return y < p.y;
	}

	bool operator == (Point p) const {
		return fabs(x - p.x) < EPS && fabs(y - p.y) < EPS;
	} // 두 점이 서로 같은지 비교
}; // 좌표가 실수 값으로 주어질 때

double hypot(double x, double y) { return sqrt(x * x + y * y); }
// 피타고라스의 정리에 의하여 z = root(x^2 + y^2)
double dist(Point p1, Point p2) { return hypot(p1.x - p2.x, p1.y - p2.y); }
// Get Euclidean Distance

Point rotate(Point p, double theta) {
	double rad = theta * (PI / 180.0); // degree를 radian으로 변환!
	// deg = rad * (180.0 / PI)
	return Point(p.x * cos(rad) - p.y * sin(rad), p.x * sin(rad) + p.y * cos(rad));
} // p를 원점(0, 0)을 중심으로 반시계 방향으로 theta도 회전한다.
```

* 극좌표계 : 평면 위의 위치를 각도와 거리를 써서 나타내는 2차원 좌표계, 두 점 사이의 관계가 각이나 거리로 쉽게 표현되는 경우에 가장 유용하다. 
  직교 좌표계에서는 삼각함수로 복잡하게 나타나는 관계가 극좌표계에서는 간단하게 표현되는 경우가 많다. 
  2차원 좌표계이기 때문에 극좌표는 반지름 성분과  각 성분의 두 성분으로 결정되며 주로 r로 나타내는 반지름 성분은 극(원점)에서의 거리를 나타낸다.
  주로 Θ로 나타내는 각 성분은 0°(직교 좌표계에서 x축의 양의 방향에 해당)에서 반시계 방향으로 잰 각의 크기를 나타낸다.
* rotate에 대한 일반화 : 각도라는 개념이 없는 직교좌표계에서는 점 P(x, y)를 각 α만큼 회전시킨다고 하면 표현하기 어렵다.  
     하지만 극좌표계에서는 P(r, Θ) -> P'(r, Θ+α) 이처럼 쉽게 표현이 가능하다. 이렇게 표현한 극좌표를    
     		 삼각함수를 이용해 데카르트 좌표로 변환하면 P'(x', y') = P`(r * cos(Θ+α), r * sin(Θ+α))가 되고  
     		 삼각함수의 덧셈정리를 이용해 P'(r*cosΘcosα - r*sinΘsinα, r*sinΘcosα + r*cosΘsinα)가 된다.  
     		 위 식에서 r*cosΘ = P.x, r*sinΘ = P.y이므로 위의 rotate 함수처럼 일반화가 가능하다.



## 8.2 Line

```c++
struct Line {
	double a, b, c;

	Line(double _a, double _b, double _c) : a(_a), b(_b), c(_c) {}
}; // 선형 방정식의 x, y의 계수와 상수로 직선을 표현
// ax + by + c = 0

Line pointsToLine(Point p1, Point p2) {
	if (fabs(p1.x - p2.x) < EPS) return Line(1.0, 0.0, -p1.x);
	else {
		Line l;
		l.a = -(double)(p1.y - p2.y) / (p1.x - p2.x);
		l.b = 1.0; // b (y의 계수)를 1로 두어 나머지 값을 구한다. y = ax + b의 형태
		l.c = -(double)(l.a * p1.x) - p1.y;
		return l;
	}
}; // 기울기와 선형 방정식에 점의 대입을 통해 선형 방정식을 도출한다.

bool areParallel(Line l1, Line l2) {
	return fabs(l1.a - l2.a) < EPS && fabs(l1.b - l2.b) < EPS
} // 계수 a와 b를 비교하여 기울기가 같은지를 확인 (평행임을 확인)

bool areSame(Line l1, Line l2) {
	return areParallel(l1, l2) && fabs(l1.c - l2.c) < EPS
} // 평행하면서 상수항까지 같다면 일치

bool areIntersect(Line l1, Line l2, Point &p) { // 참조를 사용한 전달
	if (areParallel(l1, l2)) return false;
	p.x = (l2.b * l1.c - l1.b * l2.c) / (l2.a * l1.b - l1.a * l2.b);
	if (fabs(l1.b) > EPS) p.y = -(l1.a * p.x + l1.c);
	else p.y = -(l2.a * p.x + l2.c);
	return true;
} // 교차점이 있는지 여부와 교차점의 좌표를 구하는 함수
```

* Intersect (교차) : 만약 두 직선이 평행하지 않다면(당연히 일치할 수도 없다.) 어느 한 점에서 교차한다. 따라서 그 교점을 구하려면  
        미지수가 두 개인 선형 방정식 두 개로 이루어진 연립 방정식을 풀면 된다.
* 선분은 양 끝점이 존재하며, 길이가 유한한 직선을 말한다.
* 벡터(Vector)는 선분에 방향이 더해진 것. 벡터의 x, y 성분의 크기를 멤버 변수로 하는 구조체로 표현한다.



## 8.3 Vector

```c++
struct Vec {
    double x, y;
    
    vec(double _x, double _y) : x(_x), y(_y) {}
}; // x와 y의 증감량을 통해 표현

Vec pointToVec(Point a, Point b) {
    return vec(b.x - a.x, b.y - a.y);
} // 두 점을 a -> b 방향의 벡터로 변환

Vec scale(Vec v, double s) {
    return Vec(v.x * s, v.y * s);
} // 벡터의 확대, 축소

Point translate(Point p, Vec v) {
    return Point(p.x + v.x, p.y + v.y);
} // 점을 벡터에 따라 평행이동
```

* 점 p와 직선 l (점 a, b에 의해 결정) 사이의 최소 거리를 구하는 알고리즘

  - 점 p와 가장 가까운 직선 l 위의 점 c를 구한다.

  - 점 p와 c 사이의 유클리드 거리를 구한다. 이 때, 점 c를 벡터 ab에 u 배율 곱한 것에 따라 평행이동시킨 점으로 생각할 수 있다.

  - u의 값을 구하기 위해서는 내적을 이용하여 벡터 ap를 ab로 스칼라 사영하면 된다.

  - ```c++
    double dotProduct(Vec a, Vec b) { return a.x * b.x + a.y * b.y; } // 벡터 크기의 내적
    double norm_sq(Vec v) { return v.x * v.x + v.y * v.y; } // 벡터 크기의 제곱
    double distToLine(Point p, Point a, Point b, Point& c) { // a, b로 벡터 구성
        Vec ap = pointToVec(a, p), ab = pointToVec(a, b); // 필요한 벡터 ap, ab 구성
        double u = dotProduct(ap, ab) / norm_sq(ab); // 단위 벡터
        // 배율을 구하기 위해 벡터 ap와 ab의 내적을 벡터 ab 제곱으로 나누어 비율을 구한다.
        c = translate(a, scale(ab, u));
        // 구한 비율에 따라 벡터를 확대, 축소한 뒤 점 a를 평행이동한 뒤
        return dist(p, c); // 점 p와 c 사이의 거리를 반환한다.
    } // 벡터 ab(로 구한 점 c)와 점 p사이의 거리
    ```

* 점 p와 선분 l 사이의 최소 거리를 구하는 알고리즘

  * 선분 위에 최소 거리가 되는 점이 존재한다면 직선에서의 문제와 같지만

  * 선분의 한 끝점까지의 거리가 최소거리인 경우에는 예외처리가 필요하다.

  * ```c++
    double distToLineSegment(Point p, Point a, Point b, Point& c) {
        Vec ap = pointToVec(a, p), ab = pointToVec(a, b);
        double u = dotProduct(ap, ab) / norm_sq(ab);
        if (u < 0) { // 단위 벡터에 의한 비율에 따라 a에 가까운지 b에 가까운지 결정된다.
            c = Point(a.x, a.y);
            return dist(p, a);
        }
        if (u > 1) {
            c = Point(b.x, b.y);
            return dist(p, b);
        }
        c = translate(a, scale(ab, u));
        return dist(p, c);
    }
    ```




# 9. Cut Vertex, Cut Edge (in Undirected Graph)

연결 요소가 두 개에서 하나가 되는 정점 혹은 간선. O(V * (V + E)) => O(V + E)  
Spanning Tree의 부모는 방문하지 않는다. 방향은 자식 노드 쪽으로. 루트는 자식 노드가 2개 이상이면 Cut Vertex가 될 수 있다.
```
* Back Edge : Spanning Tree에서 조상 노드로 올라가는 간선

* Cross Edge : Spanning Tree에서 형제 노드로 가로지르는 간선

* Forword Edge : Spanning Tree에서 자식 노드로 내려가는 간선 
```



# 10. Quick Sort

임의의 pivot 값을 고르고 pivot을 기준으로 pivot의 좌측에는 pivot 보다 작은 값, 우측에는 큰 값을 놓는 행위를 재귀적으로 반복했을 때,  
결국 정렬이 완성된다는 방법론.

* Average-case Analysis : pivot 값에 따라 비교 횟수가 많을 수도 적을 수도 있다. 때문에 중앙에서 분할될 가능성이 높은  
  		  좌측 끝, 중앙, 우측 끝 세 값의 중위법을 이용하여 pivot을 정하고 분할하는 방법을 대부분 채택한다.  
  		  평균적인 시간 복잡도는 O(nlogn)이다.



# 11. Closest Pair

2차원 평면 위에 n개의 점이 존재할 때, 가장 거리가 가까운 점 한 쌍을 구하는 문제.

모든 경우를 탐색하게 되면 O(n^2)의 시간복잡도가 나온다. 시간을 더 줄일 수 있는가? 

* 줄일 수 있다. 




# 12. Graph

- 대칭(Symmetric) 관계 - 무방향 그래프, 전이(Transition) 관계 - 방향 그래프
- 반사(Reflexive) 관계
- 동치 (Equivalence Relation)
- 분할 (Decomposition Partition)




# 13. Master Theorem

재귀적으로 표현한 알고리즘의 동작 시간을 점근적으로 계산하여 간단하게 계산하는 방법

![수식](.\img\수식.PNG)

이러한 동작 시간을 갖는 재귀적인 알고리즘이 있다고 하자. 이를 통해 Recursion Tree로 표현하게 되면

![트리](.\img\1.PNG)

이러한 Ternary Tree(삼원트리)로 표현할 수 있다. 그렇다면 전체 시간 복잡도는 트리의 높이(level)에 따라

- level 0
  - ![수식1](.\img\수식1.PNG)
- level 1
  - ![수식2](.\img\수식2.PNG)
- level k
  - ![수식3](.\img\수식3.PNG)

나타낼 수 있다. 그렇다면 아래 식처럼 변형이 가능하며

![수식4](.\img\수식4.PNG)

k를 극한까지 보내면 공비 r = 3/4 < 1

![수식5](.\img\수식5.PNG)

4로 수렴하는 것을 알 수 있다. 그러므로

![수식6](.\img\수식6.PNG)

따라서 재귀적 알고리즘의 시간 복잡도는 아래처럼 나타낼 수 있다.

![수식7](.\img\수식7.PNG)

이를 통해 알아낼 수 있는 것은 시간 복잡도의 지배(Domination)가 아래와 같다면

![수식8](.\img\수식8.PNG)

![수식9](.\img\수식9.PNG)



[Algorithm Design Process]
======================



# Combinatorial Objects (조합 객체)

1. Permutation (순열)
2. Subsets (부분 집합)
3. Trees (트리 / 루트가 있는 트리, 루트가 없는 트리)
4. Graphs (그래프)
5. Points (점)
6. Polygons (다각형)
7. Strings (문자열)

이들은 모두 Recursive Objects (재귀 객체)이다.

1. 순열에서 어떤 원소 하나를 제거하더라도 또 다른 순열을 얻게 된다.
2. 부분 집합에서도 어떤 원소 하나를 제거하더라도 또 다른 부분집합이다.
3. 트리의 루트를 제거하더라도 subtree들로 나뉘어진다. 혹은 단말 노드 하나를 제거하더라도 하나의 작은 트리가 남게 된다.
4. 그래프는 그룹으로도 나눌수 있고 어느 한 정점을 제거해도 작은 그래프가 남는다.
5. 한 무리의 점을 그룹으로 쪼갤 수 있다.
6. n 개의 꼭지점을 가진 단순 다각형에서 서로 인접하지 않은 두 꼭지점을 이어주면 작은 두 다각형으로 나뉘어진다.
7. 문자열에서 어느 한 글자를 지우면 길이 1이 줄어든 문자열이 된다.

```
재귀적 알고리즘으로 해결 가능한 문제들이라는 말이다.
이처럼 문제를 알고리즘을 설계하기 용이하게 모델링하는 것이 중요하다.
```