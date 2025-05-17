# Coding_Questions
-----------------------

Reverse a string
---------------------------
```C#
using System;
class Program
{
    static void Main()
    {
        string input = "Manoj";
        char[] chars = input.ToCharArray();

        int left = 0;
        int right = chars.Length - 1;

        while (left < right)
        {
            // Swap characters
            char temp = chars[left];
            chars[left] = chars[right];
            chars[right] = temp;

            left++;
            right--;
        }

        string reversed = new string(chars);

        Console.WriteLine("Original: " + input);
        Console.WriteLine("Reversed: " + reversed);
    }
}

or 

using System;

class Program
{
    static void Main()
    {
        string a = "Manoj";
        string reversed = "";

        for (int i = a.Length - 1; i >= 0; i--)
        {
            reversed += a[i];
        }

        Console.WriteLine("Original: " + a);
        Console.WriteLine("Reversed: " + reversed);
    }
}


2 in the given integer array place all the 0 element at last
---------------------------------------------------------------

using System;

class Program
{
    static void Main()
    {
        int[] a = { 1, 4, 0, 4, 0 };
        MoveZerosToEnd(a);

        Console.WriteLine(string.Join(", ", a));  // Output: 1, 4, 4, 0, 0
    }

    static void MoveZerosToEnd(int[] arr)
    {
        int index = 0;

        // First pass: move non-zero elements to the front
        for (int i = 0; i < arr.Length; i++)
        {
            if (arr[i] != 0)
            {
                arr[index] = arr[i];
                index++;
            }
        }

        // Fill remaining positions with 0
        while (index < arr.Length)
        {
            arr[index] = 0;
            index++;
        }
    }
}

Check the 2nd string is it present in first string example string a ="vikram" string b = "ram"
-----------------------------------------------------------------------

using System;

class Program
{
    static void Main()
    {
        string str1 = "vikram"; // Source string
        string str2 = "ram";    // Characters to check

        bool result = AreAllCharactersPresent(str1, str2);

        Console.WriteLine(result
            ? "All characters of str2 are present in str1."
            : "Not all characters of str2 are present in str1.");
    }

    static bool AreAllCharactersPresent(string source, string target)
    {
        int[] charCount = new int[26]; // a-z only (assuming lowercase)

        foreach (char c in source)
        {
            charCount[c - 'a']++;
        }

        foreach (char c in target)
        {
            if (charCount[c - 'a'] == 0)
                return false;

            charCount[c - 'a']--;
        }

        return true;
    }
}


Find the 2nd largest element in the given array
---------------------------------------
using System;

class Program
{
    static void Main()
    {
        int[] numbers = { 45, 12, 84, 75, 84, 30 };

        int largest = numbers[0];
        int secondLargest = numbers[0];

        for (int i = 1; i < numbers.Length; i++)
        {
            if (numbers[i] > largest)
            {
                secondLargest = largest;
                largest = numbers[i];
            }
            else if (numbers[i] < largest && (secondLargest == largest || numbers[i] > secondLargest))
            {
                secondLargest = numbers[i];
            }
        }

        if (largest == secondLargest)
            Console.WriteLine("No second largest number found.");
        else
            Console.WriteLine("Second largest number is: " + secondLargest);
    }
}

Simple Quick Sort algo
----------------------
using System;

class Program
{
    static void Main()
    {
        int[] arr = { 25, 2, 7, 1, 9, 6 };
        Console.WriteLine("Original Array: " + string.Join(", ", arr));

        QuickSort(arr, 0, arr.Length - 1);

        Console.WriteLine("Sorted Array:   " + string.Join(", ", arr));
    }

    static void QuickSort(int[] arr, int low, int high)
    {
        if (low < high)
        {
            int pivotIndex = Partition(arr, low, high);
            QuickSort(arr, low, pivotIndex - 1);   // Left part
            QuickSort(arr, pivotIndex + 1, high);  // Right part
        }
    }

    static int Partition(int[] arr, int low, int high)
    {
        int pivot = arr[low]; // Pivot as first element
        int i = low + 1;
        int j = high;

        while (i <= j)
        {
            while (i <= j && arr[i] <= pivot) i++;
            while (i <= j && arr[j] > pivot) j--;

            if (i < j)
                Swap(arr, i, j);
        }

        Swap(arr, low, j); // Put pivot in the correct position
        return j;
    }

    static void Swap(int[] arr, int i, int j)
    {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}

Coding question Linq get the 2nd highest salary based on the dept
-----------------------

using System;
using System.Linq;

public class Employee
{
    public int Id { get; set; }
    public string Name { get; set; }
    public decimal Salary { get; set; }
    public string Dept { get; set; }

}


public class Dept
{
    public static void Main(String[] args)
    {
        List<Employee> employees = new List<Employee>()
        {
         new Employee { Id = 1, Name = "John", Salary = 50000, Dept = "HR" },
         new Employee { Id = 2, Name = "Jane", Salary = 60000, Dept = "IT" },
         new Employee { Id = 3, Name = "Sam", Salary = 55000, Dept = "Finance" },
         new Employee { Id = 4, Name = "Sara", Salary = 70000, Dept = "IT" },
         new Employee { Id = 5, Name = "Tom", Salary = 45000, Dept = "HR" }
         };

        var secondHighestPerDept = employees
       .GroupBy(e => e.Dept)
       .Select(g => g.OrderByDescending(e => e.Salary).Skip(1).FirstOrDefault());

        foreach (var emp in secondHighestPerDept)
        {
            if (emp != null)
            {
                Console.WriteLine($"Dept: {emp.Dept}, Name: {emp.Name}, Salary: {emp.Salary}");
            }
        }

        var secondHighestSalary = employees.OrderByDescending(a=>a.Salary).Skip(1).FirstOrDefault();
        if (secondHighestSalary != null)
        {
            Console.WriteLine($"Name is {secondHighestSalary.Name}, salary is: {secondHighestSalary.Salary}");
        }

    }
}


my name is manoj i my work is developing things how to get number of all the words counts in c sharp
-----------------------------------------------------------------------------------------------------

using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        string input = "my name is manoj i my work is developing things";

        string[] words = input.Split( ' ' );

        Dictionary<string, int> wordCount = new Dictionary<string, int>();

        foreach (string word in words)
        {
            // Get current count or default to 0, then increment
            wordCount[word] = wordCount.GetValueOrDefault(word, 0) + 1;
        }

        foreach (var pair in wordCount)
        {
            Console.WriteLine($"Word: {pair.Key}, Count: {pair.Value}");
        }
    }
}


K most frequency Integer value
------------------------------------

using System;
using System.Collections.Generic;
using System.Linq;

public class KMostFrequentElements
{
    public static List<int> FindKMostFrequentElements(int[] nums, int k)
    {
        var frequencyMap = new Dictionary<int, int>();
        
        // Count frequency
        foreach (var num in nums)
            frequencyMap[num] = frequencyMap.GetValueOrDefault(num, 0) + 1;

        // Sort by frequency & take top k elements
        return frequencyMap.OrderByDescending(x => x.Value)
                           .Take(k)
                           .Select(x => x.Key)
                           .ToList();
    }

    static void Main()
    {
        int[] nums = { 1, 1, 1, 2, 2, 3 };
        int k = 2;
        var result = FindKMostFrequentElements(nums, k);
        Console.WriteLine(string.Join(", ", result));
    }
}


```
