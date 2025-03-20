# PHP-Example
- [Merge two sorted arrays using loops without using built-in sorting functions](#merge-two-sorted-arrays-using-loops-without-using-built-in-sorting-functions)
- [Reverse an array without using array functions using a loop.](#Reverse-an-array-without-using-array-functions-using-a-loop.)
- [Check if a number is an Armstrong number using a loop.](#Check-if-a-number-is-an-Armstrong-number-using-a-loop.)
- [Find the sum of all elements in an array using a loop.](#Find-the-sum-of-all-elements-in-an-array-using-a-oop.)
- [Find the largest and smallest elements in an array without using built-in functions.](#Find-the-largest-and-smallest-elements-in-an-array-without-using-built-in-functions.)
- [Reverse an array using a loop without using built-in function.](#Reverse-an-array-using-a-loop-without-using-built-in-function.)
- [Count occurrences of each element in an array using loops.](#Count-occurrences-of-each-element-in-an-array-using-loops.)
- [Remove duplicate elements from an array without using built in functions.](#Remove-duplicate-elements-from-an-array-without-using-built-in-functions.)
- [Find duplicate elements from an array without using built-in functions.](#Find-duplicate-elements-from-an-array-without-using-built-in-functions.)
- [Find the second largest element in an array using a single loop.](#Find-the-second-largest-element-in-an-array-using-a-single-loop.)
   
---
## Merge two sorted arrays using loops without using built-in sorting functions
Here's the code implementation:
```php
function mergeSortedArrays($arr1, $arr2) {
    $merged = [];
    $i = 0; // Pointer for first array
    $j = 0; // Pointer for second array

    // Loop through both arrays
    while ($i < count($arr1) && $j < count($arr2)) {
        if ($arr1[$i] < $arr2[$j]) {
            $merged[] = $arr1[$i];
            $i++;
        } else {
            $merged[] = $arr2[$j];
            $j++;
        }
    }

    // If any elements are left in the first array, append them
    while ($i < count($arr1)) {
        $merged[] = $arr1[$i];
        $i++;
    }

    // If any elements are left in the second array, append them
    while ($j < count($arr2)) {
        $merged[] = $arr2[$j];
        $j++;
    }

    return $merged;
}
   
// Example usage
$arr1 = [1, 3, 5, 7];
$arr2 = [2, 4, 6, 8];

$result = mergeSortedArrays($arr1, $arr2);

echo "Merged Array: ";
print_r($result);
```
**Output**
```
Array
(
    [0] => 1
    [1] => 2
    [2] => 3
    [3] => 4
    [4] => 5
    [5] => 6
    [6] => 7
    [7] => 8
)
````
----

## Reverse an array without using array functions using a loop.

```php
function reverse_array($arr) {
    $n = count($arr); // Get the length of the array
    
    // Loop through the first half of the array
    for ($i = 0; $i < $n / 2; $i++) {
        // Swap the elements at positions $i and $n - $i - 1
        $temp = $arr[$i];
        $arr[$i] = $arr[$n - $i - 1];
        $arr[$n - $i - 1] = $temp;
    }

    return $arr;
}

// Example usage:
$array = [1, 2, 3, 4, 5];
$reversedArray = reverse_array($array);
print_r($reversedArray);
```
**Output**
```
Array
(
    [0] => 5
    [1] => 4
    [2] => 3
    [3] => 2
    [4] => 1
)
````
----
### Check if a number is an Armstrong number using a loop.
An **Armstrong number** (also known as a **Narcissistic number**) for a given number of `n` is a number that is equal to the sum of its own digits each raised to the power of the number of digits.

### For example:
- **153** is an Armstrong number because:
  - It has 3 digits.
  - \( 1^3 + 5^3 + 3^3 = 153 \)

```php
<?php
function is_armstrong($num) {
    $originalNum = $num;  // Store the original number
    $numDigits = strlen((string)$num);  // Find the number of digits in the number
    $sum = 0;

    // Loop to extract each digit and add its power to the sum
    while ($num > 0) {
        $digit = $num % 10;  // Get the last digit
        $sum += pow($digit, $numDigits);  // Add the digit raised to the power of numDigits
        $num = (int)($num / 10);  // Remove the last digit from the number
    }

    // Check if the sum of the powers of the digits equals the original number
    return $sum == $originalNum;
}

// Example usage:
$number = 153;
echo is_armstrong($number) ? "$number is an Armstrong number." : "$number is not an Armstrong number.";
```

**Output**
```
153 is an Armstrong number.

````
----
