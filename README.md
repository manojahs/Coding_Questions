# Coding_Questions
-----------------------

Reverse a string
---------------------------

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
