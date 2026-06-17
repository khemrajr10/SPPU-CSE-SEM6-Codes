Practical3_InsertionSort&SelectionSort

Code:

# Insertion Sort and Selection Sort

# Original Array
arr1 = [64, 25, 12, 22, 11]
arr2 = [64, 25, 12, 22, 11]

print("Original Array:")
print(arr1)

# ---------------- Insertion Sort ----------------

for i in range(1, len(arr1)):

    # Current element
    key = arr1[i]

    # Previous index
    j = i - 1

    # Shift larger elements to right
    while j >= 0 and arr1[j] > key:

        arr1[j + 1] = arr1[j]

        j = j - 1

    # Insert key at correct position
    arr1[j + 1] = key

print("\nArray after Insertion Sort:")
print(arr1)
