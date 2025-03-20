# PHP-Example

1. Merge two sorted arrays using loops without using built-in sorting functions
   Solution :
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
