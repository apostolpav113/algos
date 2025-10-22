2-pointers partition with swaps

937. Reorder Data in Log Files: https://leetcode.com/problems/reorder-data-in-log-files/description/


Universal template, solves 90% of two pointers problems:

```c++
template <typename T, typename Pred, typename Action>
void twoPointers(std::vector<T>& data, Pred condition, Action process) {
    int left = 0;
    int right = data.size() - 1;
    while (left < right) {
        if (!condition(data[left])) {
            ++left;
            continue;
        }
        if (!condition(data[right])) {
            --right;
            continue;
        }

        process(data[left], data[right]);
        ++left;
        --right;
    }
}
```
