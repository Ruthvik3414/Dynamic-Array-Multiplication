# Dynamic-Array-Multiplication
This C++ program showcases dynamic memory allocation and pointer use. It multiplies every element of a C-style array with every element of a second array, storing the results in a new dynamic array. The code highlights key concepts like new and delete[] for memory management, and passing arrays to functions via pointers.

The result is stored in a newly created dynamic array. The program includes separate functions to perform the multiplication and to print the contents of an array. It's a great example for learning about pointers, dynamic memory allocation (`new`/`delete[]`), and passing C-style arrays to functions.

### Code

```cpp
#include<iostream>

using namespace std;

int *apply_all(const int *const arr1, size_t size1, const int *const arr2, size_t size2) {
    int *new_array {};

    new_array = new int[size1 * size2];

    int position{0};
    for(size_t i{0}; i < size2; ++i) {
        for(size_t j{0}; j < size1; ++j) {
            new_array[position] = arr1[j] * arr2[i];
            ++position;
        }
    }
    return new_array;
}

void print(const int *const arr, size_t size) {
    cout << "[ ";
    for(size_t i{0}; i < size; ++i)
        cout << arr[i] << " ";
    cout << "]" << endl;
}


int main() {
    const size_t array1_size(5);
    const size_t array2_size(3);

    int array1[] {1,2,3,4,5};
    int array2[] {10,20,30};

    cout << "Array 1: ";
    print(array1,array1_size);

    cout << "Array 2: ";
    print(array2,array2_size);

    int *result = apply_all(array1, array1_size, array2, array2_size);
    constexpr size_t result_size {array1_size * array2_size};

    cout << "Result: ";
    print(result, result_size);

    delete [] result;
    cout << endl;
    return 0;
}
