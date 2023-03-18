# Insertion sort

## Steps
1. Assume 0th element is always sorted in a given array (`arr`).
2. Take each element one by one from 1st index till the end of an array (`1..arr.len()`).
    - Copy current element (`arr[i]`) into a variable (`x`).
    - Use index `j` which should point to previous elements from current index `i`.
    - Loop through previous indexes one by one (`arr[j - 1]`).
        - if value is grater than current value `x`, then we will swap those values (`arr[j] = arr[j - 1]`).
        - Decrement `j` so that it points to next previous value and so on.
        - Once we found that `x` is greater than `arr[j - 1]` or we reach the start of an arry (`j == 0`), we will exit out of the loop and insert `x` into `j`th index (arr[j] = x).
    - We repeat this till we each the end of an array.
3. Finally, the array will be sorted.

## Code
```rust
fn insertion_sort<T: Ord + Copy>(arr: &mut [T]) {
    for i in 1..arr.len() {
        let mut j = i;
        let x = arr[i];
        while j > 0 && arr[j - 1] > x {
            arr[j] = arr[j - 1];
            j -= 1;
        }
        arr[j] = x;
    }
}

let mut arr = vec![2, 5, 1, 8, 4, 3];
insertion_sort(&mut arr);
assert_eq!(arr, vec![1, 2, 3, 4, 5, 8]);
println!("Successfull !!");
```

> `T` is used so that this function works generically on all types of slices `[T]` which satifies [Ord](https://doc.rust-lang.org/std/cmp/trait.Ord.html) and [Copy](https://doc.rust-lang.org/std/marker/trait.Copy.html) traits.
