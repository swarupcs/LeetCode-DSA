## 48. Rotate Image


https://leetcode.com/problems/binary-tree-preorder-traversal/


```
You are given an n x n 2D matrix representing an image, rotate the image by 90 degrees (clockwise).

You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.
```

#### Example 1:
![alt text](image.png)
```
Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [[7,4,1],[8,5,2],[9,6,3]]

```

#### Example 2:
![alt text](image-1.png)
```
Input: matrix = [[5,1,9,11],[2,4,8,10],[13,3,6,7],[15,14,12,16]]
Output: [[15,13,2,5],[14,3,4,1],[12,6,8,9],[16,7,10,11]]
```

#### Constraints:
```
n == matrix.length == matrix[i].length
1 <= n <= 20
-1000 <= matrix[i][j] <= 1000
```

## Solutions
### Algorithm / Intuition
Intuition: By observation, we see that the first column of the original matrix is the reverse of the first row of the rotated matrix, so that’s why we transpose the matrix and then reverse each row, and since we are making changes in the matrix itself space complexity gets reduced to O(1).
### Approach:

Step 1: Transpose the matrix. (transposing means changing columns to rows and rows to columns)

Step 2: Reverse each row of the matrix.
* **Java**

```
class Solution {
    public void rotate(int[][] matrix) {
		TransposeMatrix(matrix);
        Reverse(matrix);
    }

    public static void Reverse(int[][] arr) {
	    int n = arr.length;
	    int m = arr[0].length;
	    for (int i = 0; i < n; i++) {
	        for (int j = 0; j < m / 2; j++) { // Iterate only over half of the columns
	            int temp = arr[i][j];
	            arr[i][j] = arr[i][m - j - 1];
	            arr[i][m - j - 1] = temp;
	        }
	    }
	}
	
	public static void TransposeMatrix(int[][] arr) {
		for(int i=0; i<arr.length; i++) {
			for(int j=i+1; j<arr[0].length; j++) {
				int temp = arr[i][j];
				arr[i][j] = arr[j][i];
				arr[j][i] = temp;
			}
		}
		
	}
}


```