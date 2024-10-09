### Experiment 8: Multidimensional Arrays

---

#### **AIM**  
To study and implement 2-dimensional arrays in C++.

---

### **Theory**

A 2D array in C++ is essentially an array of arrays. It can be visualized as a table with rows and columns, where each element is accessed using two indices: the row index and the column index.

**General Declaration of a 2D Array:**  
```cpp
dataType arrayName[rowSize][columnSize];
```
- **dataType:** Type of data (e.g., `int`, `float`).
- **arrayName:** Name of the array.
- **rowSize:** Number of rows.
- **columnSize:** Number of columns.

---

### **Declaration and Initialization**

1. **Declaration:**  
   Example:
   ```cpp
   int matrix[3][4];  // A 2D array with 3 rows and 4 columns
   ```

2. **Initialization:**
   - **Static Initialization:**
     ```cpp
     int matrix[2][3] = { {1, 2, 3}, {4, 5, 6} };
     ```
   - **Dynamic Initialization:**
     ```cpp
     int rows = 2, cols = 3;
     int matrix[2][3] = {0};  // Initializes all elements to 0
     ```

---

### **Display of a 2D Array**

To display a 2D array, use nested loops to iterate through rows and columns.
```cpp
for (int i = 0; i < 2; i++) {
    for (int j = 0; j < 3; j++) {
        std::cout << matrix[i][j] << " ";
    }
    std::cout << std::endl;
}
```

---

### **Algorithms**

1. **Input and Display 2D Array (User Input):**
   - **Objective:** Read a 2D array from the user and display it.

   **Steps:**
   - **Input:**  
     Read the number of rows (`r`) and columns (`c`) from the user.
   - **Array Declaration:**  
     Declare a 2D array `arr[r][c]`.
   - **Input Elements:**  
     Loop through each row and column, prompting the user to input values.
   - **Display:**  
     Loop through the array to print its elements row-wise.

   **Code Example:**
   ```cpp
   #include <iostream>

   using namespace std;

   int main() {
       int r, c;
       cout << "Enter number of rows and columns: ";
       cin >> r >> c;

       int arr[r][c];

       // Input array elements
       for (int i = 0; i < r; i++) {
           for (int j = 0; j < c; j++) {
               cout << "Enter element (" << i+1 << ", " << j+1 << "): ";
               cin >> arr[i][j];
           }
       }

       // Display array elements
       cout << "The array elements are:" << endl;
       for (int i = 0; i < r; i++) {
           for (int j = 0; j < c; j++) {
               cout << arr[i][j] << " ";
           }
           cout << endl;
       }
       return 0;
   }
   ```

2. **Matrix Addition:**
   - **Objective:** Add two matrices if they have the same dimensions.

   **Steps:**
   - **Input:**  
     Read the dimensions of both matrices. Ensure the dimensions are compatible for addition.
   - **Declare Matrices:**  
     Declare two matrices `a` and `b` with the same dimensions.
   - **Addition:**  
     Loop through each element and compute the sum of corresponding elements from both matrices.
   - **Display:**  
     Print the resultant matrix.

   **Code Example:**
   ```cpp
   #include <iostream>

   using namespace std;

   int main() {
       int r, c;
       cout << "Enter number of rows and columns: ";
       cin >> r >> c;

       int a[r][c], b[r][c], sum[r][c];

       // Input elements for matrix a
       cout << "Enter elements of matrix A:" << endl;
       for (int i = 0; i < r; i++) {
           for (int j = 0; j < c; j++) {
               cin >> a[i][j];
           }
       }

       // Input elements for matrix b
       cout << "Enter elements of matrix B:" << endl;
       for (int i = 0; i < r; i++) {
           for (int j = 0; j < c; j++) {
               cin >> b[i][j];
           }
       }

       // Add matrices
       for (int i = 0; i < r; i++) {
           for (int j = 0; j < c; j++) {
               sum[i][j] = a[i][j] + b[i][j];
           }
       }

       // Display result
       cout << "The resultant matrix after addition is:" << endl;
       for (int i = 0; i < r; i++) {
           for (int j = 0; j < c; j++) {
               cout << sum[i][j] << " ";
           }
           cout << endl;
       }
       return 0;
   }
   ```

3. **Matrix Multiplication:**
   - **Objective:** Multiply two matrices if their dimensions are compatible for multiplication.

   **Steps:**
   - **Input:**  
     Read dimensions of matrices and ensure the number of columns of the first matrix equals the number of rows of the second matrix.
   - **Declare Matrices:**  
     Declare matrices `A`, `B`, and `C` for the result.
   - **Multiply Matrices:**  
     Compute the product using matrix multiplication logic.
   - **Display Result:**  
     Print the resultant matrix.

   **Code Example:**
   ```cpp
   #include <iostream>

   using namespace std;

   int main() {
       int r1, c1, r2, c2;
       cout << "Enter rows and columns of the first matrix: ";
       cin >> r1 >> c1;
       cout << "Enter rows and columns of the second matrix: ";
       cin >> r2 >> c2;

       if (c1 != r2) {
           cout << "Matrix multiplication is not possible." << endl;
           return 0;
       }

       int A[r1][c1], B[r2][c2], C[r1][c2] = {0};

       // Input matrices
       cout << "Enter elements of matrix A:" << endl;
       for (int i = 0; i < r1; i++) {
           for (int j = 0; j < c1; j++) {
               cin >> A[i][j];
           }
       }

       cout << "Enter elements of matrix B:" << endl;
       for (int i = 0; i < r2; i++) {
           for (int j = 0; j < c2; j++) {
               cin >> B[i][j];
           }
       }

       // Multiply matrices
       for (int i = 0; i < r1; i++) {
           for (int j = 0; j < c2; j++) {
               for (int k = 0; k < c1; k++) {
                   C[i][j] += A[i][k] * B[k][j];
               }
           }
       }

       // Display result
       cout << "The resultant matrix is:" << endl;
       for (int i = 0; i < r1; i++) {
           for (int j = 0; j < c2; j++) {
               cout << C[i][j] << " ";
           }
           cout << endl;
       }
       return 0;
   }
   ```

4. **Transpose of a Matrix:**
   - **Objective:** Compute and display the transpose of a matrix.

   **Steps:**
   - **Input:**  
     Read matrix dimensions.
   - **Transpose:**  
     Swap rows with columns to obtain the transpose.
   - **Display Result:**  
     Print the transposed matrix.

   **Code Example:**
   ```cpp
   #include <iostream>

   using namespace std;

   int main() {
       int r, c;
       cout << "Enter number of rows and columns: ";
       cin >> r >> c;

       int arr[r][c], trans[c][r];

       // Input matrix elements
       cout << "Enter elements of the matrix:" << endl;
       for (int i = 0; i < r; i++) {
           for (int j = 0; j < c; j++) {
               cin >> arr[i][j];
           }
       }

       // Compute transpose
       for (int i = 0; i < r; i++) {
           for (int j = 0; j < c; j++) {
               trans[j][i] = arr[i][j];
           }
       }

       // Display transpose
       cout << "The transposed matrix is:" << endl;
       for (int i = 0; i < c; i++) {
           for (int j = 0; j < r; j++) {
               cout << trans[i][j] << " ";
           }
           cout << endl;
       }
       return 0;
   }
   ```

 5. **Diagonal Sum of a Square Matrix:**
   - **Objective:** Compute and display the sum of the principal and secondary diagonals of a square matrix.

   **Steps:**
   - **Input:**  
     Read matrix dimensions and check if it is a square matrix (i.e., rows = columns).
   - **Declare Matrix:**  
     Declare a matrix to hold the elements.
   - **Compute Diagonal Sums:**  
     Loop through the matrix to calculate the sum of the principal and secondary diagonals.
   - **Display Result:**  
     Print the sums of the principal and secondary diagonals.

   **Code Example:**
   ```cpp
   #include <iostream>

   using namespace std;

   int main() {
       int n;
       cout << "Enter the number of rows and columns (for a square matrix): ";
       cin >> n;

       int matrix[n][n];
       int principalSum = 0, secondarySum = 0;

       // Input matrix elements
       cout << "Enter elements of the matrix:" << endl;
       for (int i = 0; i < n; i++) {
           for (int j = 0; j < n; j++) {
               cin >> matrix[i][j];
           }
       }

       // Compute sums of the principal and secondary diagonals
       for (int i = 0; i < n; i++) {
           principalSum += matrix[i][i];           // Principal diagonal: where row == column
           secondarySum += matrix[i][n - i - 1];   // Secondary diagonal: where row + column == n - 1
       }

       // Display results
       cout << "Sum of the principal diagonal: " << principalSum << endl;
       cout << "Sum of the secondary diagonal: " << secondarySum << endl;

       return 0;
   }
   ```

---

### **Conclusion**

From this experiment, we have learned:
1. How to declare and initialize 2D arrays.
2. How to perform operations like addition, multiplication, and transpose on matrices.
3. How to compute and sum the elements of the principal and secondary diagonals of a square matrix.
