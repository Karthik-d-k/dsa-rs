# Selection sort

## Steps
1. First we divide our array `arr` into sorted and unsorted, which is looped through indexes `i` and `j` respectively.
2. Find the index of minimum value (`min_idx`) in unsorted array `(i + 1)..len` assuming first element index (`i`) is minimum.
3. Swap the elements of indexes `i, min_idx`.
4. Repeat this process till we reach end of an array.
5. Finally, array will be sorted.

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

let mut arr = vec![2, 5, 1, 8, 4, 3];
selection_sort(&mut arr);
assert_eq!(arr, vec![1, 2, 3, 4, 5, 8]);
println!("Successfull !!");
```

> `T` is used so that this function works generically on all types of slices `[T]` which satifies [Ord](https://doc.rust-lang.org/std/cmp/trait.Ord.html) trait.
