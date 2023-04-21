# quick-sort
QuickSort is a sorting algorithm based on the Divide and Conquer algorithm that picks an element as a pivot and partitions the given array around the picked pivot by placing the pivot in its correct position in the sorted array.

#include <iostream>
#include <vector>

using namespace std;

void quickSort(vector<int>& arr, int left, int right) {
    int i = left, j = right;
    int pivot = arr[(left + right) / 2];
    
    // Partition
    while (i <= j) {
        while (arr[i] < pivot)
            i++;
        while (arr[j] > pivot)
            j--;
        if (i <= j) {
            swap(arr[i], arr[j]);
            i++;
            j--;
        }
    }
    
    // Recursion
    if (left < j)
        quickSort(arr, left, j);
    if (i < right)
        quickSort(arr, i, right);
}

int main() {
    vector<int> arr = {5, 1, 4, 2, 8, 9};
    
    cout << "Original array:" << endl;
    for (int num : arr)
        cout << num << " ";
    cout << endl;
    
    quickSort(arr, 0, arr.size() - 1);
    
    cout << "Sorted array:" << endl;
    for (int num : arr)
        cout << num << " ";
    cout << endl;
    
    return 0;
}
