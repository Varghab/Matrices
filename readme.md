# Solutions of popular problems on matrices

## 1. Sum Of Zeroes
```cpp
#include <bits/stdc++.h> 
int coverageOfMatrix(vector<vector<int>> &mat) {
    int coverage = 0;
    int y = mat.size();
    int x = mat[0].size();
    int i = 0;
    while (i < y) {
        int j = 0;
        while (j < x) {
            if (mat[i][j] == 0) {
                // Left check
                if ((j != 0) && (mat[i][j - 1] == 1)) coverage++;
                // Right check
                if ((j < x - 1) && (mat[i][j + 1] == 1)) coverage++;
                // Top check
                if ((i != 0) && (mat[i - 1][j] == 1)) coverage++;
                // Bottom check
                if ((i < y - 1) && (mat[i + 1][j] == 1)) coverage++;
            }
            j++;
        }
        i++;
    }
    return coverage;
}
```


## 2. Matrix Is Symmetric

```cpp
#include <bits/stdc++.h> 
bool isMatrixSymmetric(vector<vector<int>> matrix){
    // Write your code here.
    int n = matrix.size();
    int m = matrix[0].size(); 
    bool ans = true;
    for(int i=0;i<n;i++){
        for(int j=i;j<m;j++){
            if(matrix[j][i]!=matrix[i][j])ans=false;
        }
    }
    return ans;
}
```

## 3. Inplace rotate matrix 90 degree (anti clockwise)

```cpp
#include <bits/stdc++.h> 
void inplaceRotate(vector<vector<int>> &inputArray)
{
    //First find transpose by moving diagonally
    int n = inputArray.size();
    int m = inputArray[0].size();
    for(int i=0;i<n;i++){
        for(int j=i;j<m;j++){
            swap(inputArray[j][i],inputArray[i][j]);
        }
    }
    // Swap the elements
    for(int i=0;i<n-1;i++){
        for(int j=0;j<m;j++){
            swap(inputArray[i][j],inputArray[n-1][j]);
        }
        n--;
    }
}
```
## 4. Spiral Matrix

```cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int>res;
        if(matrix.size()==0)return res;
        int rowStart = 0;
        int rowEnd = matrix.size()-1;
        int colStart = 0;
        int colEnd = matrix[0].size()-1;
        while(rowStart<=rowEnd&&colStart<=colEnd){
            //Move Right
            for(int i=colStart;i<=colEnd;i++){
                res.push_back(matrix[rowStart][i]);
            }
            rowStart++;
            // Move Down
            for(int i=rowStart;i<=rowEnd;i++){
                res.push_back(matrix[i][colEnd]);
            }
            colEnd--;
            // Move left
            if(rowStart<=rowEnd){
                for(int i=colEnd;i>=colStart;i--){
                    res.push_back(matrix[rowEnd][i]);
                }
            }
            rowEnd--;
             // Move up
            if(colStart<=colEnd){
                for(int i=rowEnd;i>=rowStart;i--){
                    res.push_back(matrix[i][colStart]);
                }
            }
            colStart++;      
        }
        return res;
    }
};
```

## 5. Set Matrix Zeros

```cpp
#include <bits/stdc++.h>

void setZeros(vector<vector<int>> &matrix)
{

	int n = matrix.size();
	int m = matrix[0].size();
	vector<int>col(m,0);
	vector<int>row(n,0);
	for(int i=0;i<n;i++){
		for(int j=0;j<m;j++){
			if(matrix[i][j]==0){
				col[j] = -1;
				row[i] = -1;
			}
		}
	}	
	for(int i=0;i<n;i++){
		for(int j=0;j<m;j++){
			if(col[j]==-1||row[i]==-1)matrix[i][j] = 0;
		}
	}

}
```
