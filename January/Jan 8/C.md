# *08. Count the number of possible triangles*
## Code (C)

```c
int compare(const void *a, const void *b) {
    return (*(int *)a - *(int *)b);
}

int countTriangles(int arr[], int n) {
    qsort(arr, n, sizeof(int), compare);
    int count = 0;
    for (int i = n - 1; i >= 2; --i) {
        int l = 0, r = i - 1;
        while (l < r) {
            if (arr[l] + arr[r] > arr[i]) count += (r-- - l);
            else ++l;
        }
    }
    return count;
}
```
