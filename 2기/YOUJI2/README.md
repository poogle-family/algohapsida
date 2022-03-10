
# 문제
[렌선 자르기](https://www.acmicpc.net/problem/1654)

# 설명
![image](https://user-images.githubusercontent.com/43923432/157226741-e8b8091a-da79-4d4f-9ed9-46c11858e57f.png)
> 문제에서 max는 **2^31-1**로 **int**형의 최댓값을 가지고 있다.
> mid 값을 구하는 연산에서 **mid = (min + max) / 2** 의 부분에서 **int** 형의 범위를 넘어가기 때문에
> **long** 형으로 바꿔주어야 **OverFlow**를 피할 수 있다.

# 문제풀이
```java
import java.util.Scanner;

public class Solution {
	
	public static long solution(int n, int[] arr) {
				
		long min=0,mid=0;
		long max=0;
		for(int i=0;i<arr.length;i++) {
			if(max < arr[i]) max = arr[i];
		}
		max+=1;
		while(min < max) {
			mid = (max + min) / 2;
			int count =0;

			for(int x : arr) count += x / mid;
			
			if(count < n) {
				max = mid; 
			}else {
				min = mid+1;
			}
		}
		return min-1;
	}
	
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner sc = new Scanner(System.in);
		
		int k = sc.nextInt();
		int n = sc.nextInt();
		int arr[] = new int[k];

		for(int i=0;i<k;i++) {
			arr[i] = sc.nextInt();
		}
		long result = solution(n, arr);
		System.out.println(result);
	}
}



```


