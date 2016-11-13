# -word-Wrap-
package QU10;

import java.util.*;
import java.io.*;

public class QU10 {

    public static void main(String[] args) throws FileNotFoundException {
        wordWrap(new Scanner(new File("lines.txt")));

        int[] list1 = {42, 16, 27, 33, 18, 50};
        int[] list2 = {19, 36, 24, 36, 44};

        System.out.println("list 1 indexOf 33 = " + indexOf(list1, 33));
        System.out.println("list 1 indexOf 20 = " + indexOf(list1, 20));
        System.out.println();
        System.out.println("list 1 unique? " + isUnique(list1));
        System.out.println("list 2 unique? " + isUnique(list2));
        System.out.println();
        System.out.println("list 1 running sum: " + Arrays.toString(runningSum(list1)));
        System.out.println("list 2 running sum: " + Arrays.toString(runningSum(list2)));
        System.out.println();
        rotateLeft(list1);
        System.out.println("list 1 rotated left: " + Arrays.toString(list1));
        rotateLeft(list2);
        System.out.println("list 2 rotated left: " + Arrays.toString(list2));
        System.out.println();
        rotateRight(list1);
        System.out.println("list 1 rotated right: " + Arrays.toString(list1));
        rotateRight(list2);
        System.out.println("list 2 rotated right: " + Arrays.toString(list2));
        System.out.println();
    }

    // Write a method called wordWrap that accepts a 
    // Scanner representing an input file as its parameter 
    // and outputs each line of the file to the console, 
    // word-wrapping all lines that are longer than 60 
    // characters. For example, if a line contains 112 
    // characters, the method should replace it with two 
    // lines: one containing the first 60 characters and 
    // another containing the final 52 characters. 
    public static void wordWrap(Scanner input) {
        // substring
        while (input.hasNextLine()) {
            String line = input.nextLine();
            while (line.length() > 60) {
                System.out.println(line.substring(0, 60));
                line = line.substring(60);
            }
            System.out.println(line);
        }
    }

    // Write a static method called indexOf that takes an 
    // array of integers and a value as parameters and 
    // that returns the index of the first occurrence of
    // the value in the array, returning -1 if not found
    public static int indexOf(int[] list, int value) {
        for (int i = 0; i < list.length; i++) {
            if (list[i] == value) {
                return i;
            }
        }
        return -1;
    }

    // Write a static method called isUnique that takes 
    // an array of integers as a parameter and that 
    // returns true if the values in the list are
    // unique and that returns false otherwise.  
    // The values in the list are considered unique 
    // if there is no pair of values that are equal.
    public static boolean isUnique(int[] list) {
        for (int i = 0; i < list.length; i++) {
            for (int j = i + 1; j < list.length; j++) {
                if (list[i] == list[j]) {
                    return false;
                }
            }
        }
        return true;
    }

    // Write a static method called runningSum that 
    // takes an array of integers as a parameter and 
    // that returns a new array that contains the
    // running sum of the numbers in the array (where 
    // the i-th value of the new array is the sum of 
    // the first i values of the original array)
    // 4, 3, -2, 6   -->   4, 7, 5, 11
    public static int[] runningSum(int[] list) {
        int[] sums = new int[list.length];
        sums[0] = list[0];

        for (int i = 1; i < list.length; i++) {
            sums[i] = sums[i - 1] + list[i];
        }

        return sums;
    }

    // Write a static method called rotateLeft that 
    // takes a nonempty array of integers as a parameter
    // and that rotates all values to the left by one
    // position, rotating the first value to the back of
    // the array.  For example, given the list 
    // {1, 2, 3, 4}, a call on rotateLeft should
    // yield {2, 3, 4, 1}.
    public static void rotateLeft(int[] list) {
        int first = list[0];
        for (int i = 0; i < list.length - 1; i++) {
            list[i] = list[i + 1];
        }
        list[list.length - 1] = first;
    }

    // Write a static method called rotateRight that 
    // takes a nonempty array of integers as a parameter
    // and that rotates all values to the right by
    // one position, rotating the last value to the front
    // of the array (e.g., given the list {1, 2, 3, 4}, 
    // a call on rotateRight should yield the
    // list {4, 1, 2, 3})
    public static void rotateRight(int[] list) {
        int last = list[list.length - 1];
        for (int i = list.length - 1; i > 0; i--) {
            list[i] = list[i - 1];
        }
        list[0] = last;
    }
}
