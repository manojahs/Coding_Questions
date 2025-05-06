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
