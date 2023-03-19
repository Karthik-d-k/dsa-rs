# Selection sort

## Steps
1. Loop through each index `i` of an array `arr`.
    - Find the index of minimum value (`min_idx`) in the array starting from index `(i + 1)` till the end, assuming `0`th element is the smallest.
    - Swap the elements of indexes `i` and `min_idx`.
    - Now, we will have minimum value in `i`th index.
2. Repeat this process till we reach end of an array.
3. Finally, the array will be sorted.

## Code
```rust
fn selection_sort<T: Ord>(arr: &mut [T]) {
    let len = arr.len();

    for i in 0..len {
        let mut min_idx = i;
        for j in (i + 1)..len {
            if arr[j] < arr[min_idx] {
                min_idx = j;
            }
        }
        arr.swap(i, min_idx);
    }
}

let mut arr = vec![5, 4, 3, 2, 1];
selection_sort(&mut arr);
assert_eq!(arr, vec![1, 2, 3, 4, 5]);
println!("Successfull !!");
```

> `T` is used so that this function works generically on all types of slices `[T]` which satifies [Ord](https://doc.rust-lang.org/std/cmp/trait.Ord.html) trait.
