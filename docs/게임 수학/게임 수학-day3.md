# 게임 수학 학습 정리

**2025/03/07 [포텐업] 게임 개발자 양성 과정**

---

### 1시간

벡터 : 수는 직선으로 표시되지만 2차원부터는 벡터로 표현



### 2시간

직선의 방정식 

a1P1 + a2P2 = v3

a1P1 + (1-a1)P2 = P3

선형조합식은 2개의 식만 쓰는 게 아니다

a1P1 + a2P2 + a3P3 = v 이게 점이 되기 위해선

a1+ a2 + a3 = 1이어야 한다.

a1P1 + a2P2 + (1 - a1 - a2)P3 = P4

a1(P1 - P3) + a2(P2 - P3) = P4 - P3

즉, a1V1 + a2V2 = V3

기본적인 조건은 모두 선형독립이어야 한다.



삼각형을 만들어 주는 수식

a1P1 + a2P2 + (1 - a1 - a2)P3

0<= a1 <= 1

0<= a2 <= 1

삼각형이 가진 유용한 특징

1. 내 삼각형 영역 안에 있는 두 점을 연결했을 때 그 선은 언제나 삼각형 안에 있다.(Convex)



Barycentric Coordinate

Point : affine

Vertex : position, color, uv, normal, tangent



### 3시간

텍스쳐링

