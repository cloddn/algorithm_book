# Algorithmic analysis

## Overview

- Goal : insertion sort / merge sort
- pseudo code
- running time analysis 분석
- divide and conquer 학습 in merge sort

## Insertion sort

![스크린샷 2023-04-14 오후 4.18.57.png](Algorithmic%20analysis%20fb45b6bea66349b2b13532b6e44b6dd4/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-04-14_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_4.18.57.png)

- the sequence → array 형태로 지정
- Keys = N (갯수)
- 각각의 키가 - satellite data

특징 

- 작은 수의 배열 요소를 소팅하기 좋음
- -비유
    1. 왼쪽에 빈 손 / 테이블에 카드들이 놓여있음
    2. 테이블에서 하나를 왼손에다 놓음
    3. 적절한 위치를 찾기 위해 각 카드와 이미 있는 손에 있는 카드와 비교함
    4. 왼손에 있는 카드가 정렬되고 계속 정렬됨
    
    즉, 손에 있는 카드를 한번에 한장씩 확인하며 정렬 되어 있는 카드 사이 적절한 위치에 삽입할때 사용하는 방법이다
    
    삽입정렬은 요소를 삽입하기 전 대상 요소보다 큰 요소의 자리를 오른쪽으로 밀어서 빈 공간을 만들고, 만들어진 공간에 해당 요소를 삽입한다.
    
    ![스크린샷 2023-04-14 오후 4.31.40.png](Algorithmic%20analysis%20fb45b6bea66349b2b13532b6e44b6dd4/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-04-14_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_4.31.40.png)
    
    1. j = key  2부터 n 만큼 정렬 탐색
    2. key 부여
    3. 만약 정렬해야될 애가 .. 있는 것 i=j-1
    
    **A[i]자리에 삽입해야하면 A[i+1]=A[i]로 변경 / A[i+1]=key 두개 값을 swap 해주는 부분**
    
    i=i-1 빈공간 삭제 ?
    
    ![스크린샷 2023-04-14 오후 4.39.49.png](Algorithmic%20analysis%20fb45b6bea66349b2b13532b6e44b6dd4/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-04-14_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_4.39.49.png)
    
    사진 기준
    
    1. j - left hand 역할
    2. 만약 j-1보다 키보다 크다면 (j보다 크다면) 옮겨준다 (left A[j] greater than A[j] i = j-1 )
    3. 그 다음 key 값을 증가 ( j를 증가시킴) 
    
    heavy vertical line 기준으로 Iteration 영향 O / 뒤쪽은 iteration 영향을 받지 않음 
    
    key 값 뒤로는 영향을 받지 않음
    
    ### correctness
    
    - loop invariant 를 통해 적절한지를 알 수 ㅣㅇㅆ음
    - A[1…j-1]까지의 루프가 필요함 → 순서대로
        
        ![스크린샷 2023-04-14 오후 4.45.46.png](Algorithmic%20analysis%20fb45b6bea66349b2b13532b6e44b6dd4/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-04-14_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_4.45.46.png)
        
    
    ### Best case
    
    ![스크린샷 2023-04-14 오후 5.26.19.png](Algorithmic%20analysis%20fb45b6bea66349b2b13532b6e44b6dd4/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-04-14_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_5.26.19.png)
    
    ### Worse case
    
    > 최선의 조건에서는 *N*−1 번의 비교와 0 번의 교환을 수행한다.(*n*−1)+(*n*−2)+(*n*−3)+⋅ ⋅ ⋅ +2+1=*n*(*n*−1)/2=*O*(*N*2) 최악 *O*(*N*2) 평균 *O*(*N*2) 최선 *O*(*N*)
    > 
    
    > 삽입정렬의 공간복잡도는 주어진 배열안에서 교환을 수행하는 제자리 정렬 이기 때문에 *O*(*N*) 이다.
    > 
    
    ## Analyzing algorithms
    
    - Random Access machine model - RAM model
        - 동시에 수행되지 않고 하나씩 처리됨
        - in real computers:
            1. Arithmetic: add, subtract, multiply, divide, remainder, floor, ceiling). Also,
            shift left/shift right (good for multiplying/dividing by 2^k ).
            2. • Data movement: load, store, copy.
            3. • Control: conditional/unconditional branch, subroutine call and return.
        - RAM model : uses integer and floating-point types.
    
    → the time : input 수에 비례함