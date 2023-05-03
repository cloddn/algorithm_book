# Divide and conquer 1

Designing algorithms : Divid and conquer(3주차)

## Insertion sort

→ •  Big-**Ω : 빅 오메가 표기법 : 하한선 표시 /**알고리즘이 상한선 없이 *최소한*
 어느 정도 걸린다

# Divid and conquer: Merge sort

- divide : break the current problem into smaller (easier) sub-problems
- conquer : Solve the smaller problems and collect the results to solve the current problem.
    
    ![스크린샷 2023-04-18 오후 4.33.12.png](Divide%20and%20conquer%201%20Designing%20algorithms%20Divid%20an%20ebf19f88647149c1b3fba778099cf4fc/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-04-18_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_4.33.12.png)
    

recurrence relation ( 재귀 함수 )

- `Code 구현`

:  `merge Sort (int arr[], int l , int r):`

→ l부터 r까지  재귀 → mergeSort(arr,l,m);  mergeSort(arr,m+1,r); = l부터 m까지 m+1부터 r까지 정렬

⇒ 끝까지 conquer 후 , 그 다음 merge

## **Proving Correctness  ⇒ 잘 작동하는가?**

`유도 증명` 

merge sort가 길이가 1부터 i인 모든 리스트를 정렬할 수 있다고 하자

이때 길이가 i+1인 리스트에 대해 merge sort를 실행 → Merge sort : 좌측, 우측부분 리스트를 매개변수로 하는 mergesort를 재귀함수함 

- MergeSort(arr,1,i) → 이미 정렬되어있음
- MergeSort(arr,i+1,i+1) →

1) Inductive Hypothesis merge sort : 1 to i 까지 정렬된 리스트를 통해 i+1인 리스트를 정렬할 수 있을 것이다.

2) Base case (i=1) merge sort: 길이가 1인 리스트는 자체적으로 정렬되있음이 자명하다.

⇒ MergeSort(arr,1,i+1) → 정렬되있음이 증명됨 **( Proving Correctness )** 

![스크린샷 2023-04-18 오후 4.51.49.png](Divide%20and%20conquer%201%20Designing%20algorithms%20Divid%20an%20ebf19f88647149c1b3fba778099cf4fc/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-04-18_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_4.51.49.png)

//38page

## Analyzing Runtime ⇒ 속도가 빠른가? (시간복잡도 증명)

### (1) Using Recursion tree method : **O(n* log(n))**

***T(n)=T(⌈n/2⌉) + T(⌊n/2⌋)***

**merge** : At most len(L) + len(R) which is n iters : 적어도 L,R를 더한 값 - N개의 iteration이 runtime 최대임 (T(n) - N개의 iteration : 두개의 값 비교)

1. • a total runtime of **T(**⌈**n/2**⌉**) + T(**⌊**n/2**⌋**)** 
2. what is the runtime of merge?

⇒ **O(n)** 
T(0) = O(1)

T(1) = O(1)

T(n)= **T(**⌈**n/2**⌉**) + T(**⌊**n/2**⌋**) + merge**

**Runtime $cn log2
n 
+ cn$ = O(n* log(n))**

![스크린샷 2023-04-18 오후 5.11.49.png](Divide%20and%20conquer%201%20Designing%20algorithms%20Divid%20an%20ebf19f88647149c1b3fba778099cf4fc/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-04-18_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_5.11.49.png)

### (2) Iteration method : **O(n* log(n))**

![스크린샷 2023-04-18 오후 5.13.48.png](Divide%20and%20conquer%201%20Designing%20algorithms%20Divid%20an%20ebf19f88647149c1b3fba778099cf4fc/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-04-18_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_5.13.48.png)

→ 반복하는 (iteration ) → 귀납법 : 등비수열의 합으로 계산 

- what is k? : the number of times to divide n by 2 to get 1
    - N을 계속해서 2로 나눠 1이 될때까지의 시간 = 즉 log2n
        
        ![스크린샷 2023-04-18 오후 5.16.43.png](Divide%20and%20conquer%201%20Designing%20algorithms%20Divid%20an%20ebf19f88647149c1b3fba778099cf4fc/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-04-18_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_5.16.43.png)
        

### (3) Master method

[알고리즘) 4. Master Method 연습](https://m.blog.naver.com/babobigi/221807706228)

### (4) Substitution method :

- T(n) = 10n, when 1 ≤ n ≤ 10
- T(n) = 3n + T(n/5) + T(n/2), otherwise
    
    ![스크린샷 2023-04-18 오후 5.26.19.png](Divide%20and%20conquer%201%20Designing%20algorithms%20Divid%20an%20ebf19f88647149c1b3fba778099cf4fc/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-04-18_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_5.26.19.png)
    

![스크린샷 2023-04-18 오후 5.26.41.png](Divide%20and%20conquer%201%20Designing%20algorithms%20Divid%20an%20ebf19f88647149c1b3fba778099cf4fc/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-04-18_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_5.26.41.png)

Correctness , Efficiency 고려

최적화 되어있다 - Optimal함 : 

# Linear-Time Selection

- Task : k번째로 작은 요소를 정렬되어있지않은 리스트에서 O(n) 시간내에 찾아야함 (Find the k smallest element in an unsorted list in O(n)-time.)
    
    ![스크린샷 2023-04-18 오후 7.57.08.png](Divide%20and%20conquer%201%20Designing%20algorithms%20Divid%20an%20ebf19f88647149c1b3fba778099cf4fc/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-04-18_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_7.57.08.png)
    
    ***→ Sorting 한 후에 index 이용해서 찾도록 하자.***
    
    Not quite Linear-time selection
    
    ```python
    def naive_select(A,k):
    	A=mergesort(A)
    	return A[k]
    
    ```
    
    **KEY : select a pivot(랜덤으로 하나 골라), partition around it  : (pivot기준으로 쪼개 (구분역할)) ,recurse (반복)**
    
    ![스크린샷 2023-04-18 오후 8.33.49.png](Divide%20and%20conquer%201%20Designing%20algorithms%20Divid%20an%20ebf19f88647149c1b3fba778099cf4fc/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-04-18_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_8.33.49.png)
    
    ```cpp
    // Returns k'th (k = 0, 1, ..) smallest element in arr[l..r] in worst case // linear time. ASSUMPTION: ALL ELEMENTS IN ARR[] ARE DISTINCT
    int select(int arr[], int l, int r, int k)
    {
    	// If k is smaller than number of elements in array
    	if (k >= 0 && k < r - l + 1) {
    	int n = r-l+1; // Number of elements in arr[l..r] int pivot = arr[l + rand() % n];
    	// Partition the array around a random element and 
    	// get position of pivot element in sorted array 
    	int pos = partition(arr, l, r, pivot);
    	 // If position is same as k
    	if (pos-l == k) 
    			return arr[pos];
    	if (pos-l > k)// If position is more, recur for left 
    			return select(arr, l, pos-1, k); "Recurse"
    			else // Else recur for right subarray
    			return select(arr, pos+1, r, k-pos+l-1); "Recurse"
    }
     }
    ```
    
    ```cpp
    // It searches for x in arr[l..r], and partitions the array around x.
    int partition(int arr[], int l, int r, int x) {
        // Search for x in arr[l..r] and move it to end
    int i;
    for (i=l; i<r; i++)
    if (arr[i] == x) break;
        swap(&arr[i], &arr[r]);
        // Standard partition algorithm
    i = l;
    for (int j = l; j <= r - 1; j++) {
    	if (arr[j] <= x) {
                swap(&arr[i], &arr[j]);
    i++; }
    }
    swap(&arr[i], &arr[r]); return i;
    }
    ```
    
    ![스크린샷 2023-04-18 오후 8.41.21.png](Divide%20and%20conquer%201%20Designing%20algorithms%20Divid%20an%20ebf19f88647149c1b3fba778099cf4fc/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-04-18_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE_8.41.21.png)
    
    **Worst-case runtime = O(n^2)**
    
    ********
    
    ## ****Proving Correctness****
    
    ![Untitled](Divide%20and%20conquer%201%20Designing%20algorithms%20Divid%20an%20ebf19f88647149c1b3fba778099cf4fc/Untitled.png)
    
    - iterative 관점 : loop 불변 key값 ( 배열의 갯수라든가..)
    - recursive 관점 : inductive hypothesis 재귀식 유도 ( 귀납법을 통해 )
    
    가정 :  **4 components** ( 증명을 위한 4가지 요소)
    
    1. Inductive Hypyothesis : ***length 1 to i*** 
        1. select (A,k)  : correctly finds the kth-smallest element for inputs of length 1 to i. 1부터 i까지의 리스트에서 k번째로 작은 요소를 정확하게 찾아낼 수 있다.
    2. Base case : ***length 1***
        1.  **select(A,k) :** correctly finds the smallest element for inputs of length **1**; it returns the element itself which is trivially the **smallest**. 무조건 K값 Return → 1
    3. Inductive step : ***length i + 1***
    4. Conclusion : ***length n to entire list***
    
    ## ****Analyzing Runtime****