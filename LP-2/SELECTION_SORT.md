# ---------------- Selection Sort ----------------

for i in range(len(arr2)):

    # Assume current index has minimum element
    min_index = i

    # Find actual minimum element
    for j in range(i + 1, len(arr2)):

        if arr2[j] < arr2[min_index]:

            min_index = j

    # Swap elements
    arr2[i], arr2[min_index] = arr2[min_index], arr2[i]

print("\nArray after Selection Sort:")
print(arr2)
