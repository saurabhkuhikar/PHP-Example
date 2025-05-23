# PHP Interview Questions
- [Merge two sorted arrays using loops without using built-in sorting functions](#merge-two-sorted-arrays-using-loops-without-using-built-in-sorting-functions)
- [Reverse an array without using array functions using a loop](#reverse-an-array-without-using-array-functions-using-a-loop)
- [Check if a number is an Armstrong number using a loop](#check-if-a-number-is-an-armstrong-number-using-a-loop)
- [Find the sum of all elements in an array using a loop](#find-the-sum-of-all-elements-in-an-array-using-a-loop)
- [Find the largest and smallest elements in an array without using built-in functions](#find-the-largest-and-smallest-elements-in-an-array-without-using-built-in-functions)
- [Find duplicate elements from an array without using built-in functions](#find-duplicate-elements-from-an-array-without-using-built-in-functions)
- [Remove duplicate elements from an array without using built in functions](#remove-duplicate-elements-from-an-array-without-using-built-in-functions)
- [Find the second largest element in an array using a single loop](#find-the-second-largest-element-in-an-array-using-a-single-loop)
- [Sort the array without using built in functions](#sort-the-array-without-using-built-in-functions)
- [In PHP, what happens if a class uses two traits that both define a method with the same name? What happence in this case](#what-happens-if-a-class-uses-two-traits-that-both-define-a-method-with-the-same-name)
- [Is PHP a case-sensitive language? Which elements are case-sensitive, and which are not?](#Is-PHP-a-case-sensitive-language-Which-elements-are-case-sensitive-and-which-are-not)

 
   
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

## Reverse an array without using array functions using a loop

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

#Example 2
function reverse_array($arr) {
    $n = count($arr); // Get the length of the array
    $tempArr = [];
    // Loop through the array backwards
    for ($i = 0; $i < $n; $i++) {
        // Insert elements at the beginning of tempArr to reverse
        $tempArr[] = $arr[$n - $i - 1];
    }

    return $tempArr;
}

// Example usage:
$array = [1, 22, 13, 4, 5];
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
### Check if a number is an Armstrong number using a loop
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
````
153 is an Armstrong number.
````
----
### Find the sum of all elements in an array using a loop

```php

function sum_array($arr) {
    $sum = 0;  // Initialize the sum to 0
    
    // Loop through each element in the array and add it to the sum
    foreach ($arr as $element) {
        $sum += $element;  // Add each element to the sum
    }

    return $sum;  // Return the total sum
}

// Example usage:
$array = [1, 2, 3, 4, 5];
echo "The sum of the array elements is: " . sum_array($array);


function sum_array2($arr) {
    $sum = 0;
    
    // Loop through each index of the array
    for ($i = 0; $i < count($arr); $i++) {
        $sum += $arr[$i];  // Add the element at index $i to the sum
    }

    return $sum;
}

// Example usage:
$array = [1, 2, 3, 4, 5];
echo "The sum of the array elements is: " . sum_array2($array);
```
**Output**
````
The sum of the array elements is: 15
````
----

### Find the largest and smallest elements in an array without using built-in functions

```php
function find_min_max($arr) {
    // Initialize the first element as both the minimum and maximum
    $min = $arr[0];
    $max = $arr[0];

    // Loop through the array starting from the second element
    foreach ($arr as $element) {
        if ($element < $min) {
            $min = $element;  // Update min if a smaller element is found
        }
        if ($element > $max) {
            $max = $element;  // Update max if a larger element is found
        }
    }

    return ['min' => $min, 'max' => $max];  // Return an array with min and max values
}

// Example usage:
$array = [1, 2, 3, 4, 5];
$result = find_min_max($array);
echo "The smallest element is: " . $result['min'] . "\n";
echo "The largest element is: " . $result['max'] . "\n";

```

**Output**
````
The smallest element is: 1
The largest element is: 5
````
----
### Find duplicate elements from an array without using built-in functions
```php
   
function count_occurrences($arr) {
    $counts = [];  // Initialize an empty array to store counts

    // Loop through the array and directly count occurrences of each element
    foreach ($arr as $element) {
        // Increase count for the element in the associative array
        $counts[$element] = ($counts[$element] ?? 0) + 1;
    }

    return $counts;
}

// Example usage:
$array = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4];
$occurrences = count_occurrences($array);

// Display the result
foreach ($occurrences as $element => $count) {
    echo "Element $element occurs $count times.\n";
}

```

**Output**
````
Element 1 occurs 1 times.
Element 2 occurs 2 times.
Element 3 occurs 3 times.
Element 4 occurs 4 times.
````
----

### Remove duplicate elements from an array without using built in functions

```php
<?php
function remove_duplicates($arr) {
    $uniqueArray = [];  // Initialize an empty array to store unique elements

    // Loop through each element in the original array
    foreach ($arr as $element) {
        // Use the element as a key in the associative array
        // If the element is not already in the unique array, it will be added
        if (!isset($uniqueArray[$element])) {
            $uniqueArray[$element] = true;  // Mark the element as seen
        }
    }

    // Return the unique array as an indexed array (values only)
    return array_keys($uniqueArray);
}

// Example usage:
$array = [1, 2, 2, 3, 4, 3, 5, 1];
$uniqueArray = remove_duplicates($array);
print_r($uniqueArray);
?>

```
**Output**
````
Array
(
    [0] => 1
    [1] => 2
    [2] => 3
    [3] => 4
    [4] => 5
)
````
----

### Find the second largest element in an array using a single loop

```php

function find_second_largest($arr) {
    if (count($arr) < 2) {
        return null;  // If there are fewer than two elements, return null
    }

    $largest = $second_largest = null;

    foreach ($arr as $element) {
        if ($largest === null || $element > $largest) {
            $second_largest = $largest;
            $largest = $element;
        } elseif ($element !== $largest && ($second_largest === null || $element > $second_largest)) {
            $second_largest = $element;
        }
    }

    return $second_largest;
}

// Example usage:
$array = [1, 2, 3, 4, 5];
$secondLargest = find_second_largest($array);
echo "The second largest element is: " . ($secondLargest ?? "None") . "\n";
```

**Output**
````
The second largest element is: 4
````
----
### Sort the array without using built in functions
```php
$array = [50,12, 30, 10, 9, 14];
$count = 0;
foreach($array as $elem){
    $count++;
}
for ($i = 0; $i < $count; $i++) {
    for ($j = 0; $j < $count - $i - 1; $j++) {
        if ($array[$j] > $array[$j + 1]) { 
            $temp = $array[$j];
            $array[$j] = $array[$j + 1]; 
            $array[$j +1] = $temp; 
        }
    }
}
print_r($array);
````
----

**Output**
````
Array
(
    [0]=> 9
    [1] => 10
    [2] => 12
    [3] => 14
    [4] => 30
    [5] => 50
)
````
----

### what happens if a class uses two traits that both define a method with the same name?

When a class uses multiple traits that define methods with the same name, PHP will throw a fatal error due to the ambiguity. To resolve this conflict, you can use the insteadof operator to specify which trait's method should be used. Additionally, you can use the as operator to alias a method from a trait, allowing you to access both methods under different names

```php

trait TraitA {
    public function getData() {
        return "TraitA";
    }
}

trait TraitB {
    public function getData() {
        return "TraitB";
    }
}

class MyClass {
    use TraitA, TraitB {
        TraitA::getData insteadof TraitB;
        TraitB::getData as getDataFromB;
    }
}

$obj = new MyClass();
echo $obj->getData();        // Outputs: "TraitA"
echo $obj->getDataFromB();   // Outputs: "TraitB"


````
----

### Is PHP a case-sensitive language Which elements are case-sensitive and which are not

PHP is partially case-sensitive. Understanding which elements are case-sensitive and which are not is crucial for writing consistent and error-free code.

✅ Case-Sensitive Elements
Variables: Variable names are case-sensitive. For example, $name and $Name are considered distinct variables.
Constants: Constants are case-sensitive. By convention, constant identifiers are always uppercase. 
Class Constants and Properties: These are also case-sensitive. 

❌ Case-Insensitive Elements
Function Names: Function names are case-insensitive. Defining a function as function myFunc() allows it to be called as myfunc(), MYFUNC(), etc.
Class Names: Class names are case-insensitive. However, when using autoloaders on case-sensitive file systems (like ext4 on Linux), it's advisable to match the case of the class name with the filename to avoid issues.
Keywords and Language Constructs: PHP keywords and constructs (such as if, else, while, echo) are case-insensitive. 

```php
$var = "Hello";
echo $var;   // Outputs: Hello
echo $VAR;   // Notice: Undefined variable: VAR

````
----
