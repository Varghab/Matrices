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

