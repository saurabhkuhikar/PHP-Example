# PHP-Example
1. [Merge two sorted arrays using loops without using built-in sorting functions](Merge-two-sorted-arrays-using-loops-without-using-built-in-sorting-functionss)
2. [Reverse an array without using array functions using a loop.](Reverse-an-array-without-using-array-functions-using-a-loop.)
3. [Check if a number is an Armstrong number using a loop.](Check-if-a-number-is-an-Armstrong-number-using-a-loop.)
4. [Find the sum of all elements in an array using a loop.](Find the sum of all elements in an array using a loop.)
5. [Find the largest and smallest elements in an array without using built-in functions.](Find-the-largest-and-smallest-elements-in-an-array-without-using-built-in-functions.)
6. Reverse an array using a loop (without using array_reverse()).
7. Count occurrences of each element in an array using loops.
8. Remove duplicate elements from an array without using built-in functions.
9. Find duplicate elements from an array without using built-in functions.
10. Find the second largest element in an array using a single loop.
-----
### Merge two sorted arrays using loops without using built-in sorting functions
   <?php
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
   ?>
