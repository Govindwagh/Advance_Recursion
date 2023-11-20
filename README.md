# Advance_Recursion

//problem 1: implementation of the Tower of Hanoi problem using recursion ??

//problem 2: Print a String in Reverse ??

//Problem 3: Check if an array is sorted (Strictly Increasing) {1. 2, 3, 4, 5}

//Problem 4: Move all 'x' to the end of the string  ( "Gxxoxxvxixxxnxd" )??

//Problem 5: Remove the All Duplicates from the given string ("abbdssfgjsshrrfisdojj").

//Problem 6: Print all the subsequences of a string "abc" ??

//Problem 7: Print all the unique subsequences of a string "aaa" ??

//Problem 8: Print keypad Combination of a mobile ??

//Problem 9: Print all permutations of a String "abc" ??

//Problem 10: Count total paths in a maze to move from (0,0) to (n,m) where n=3, m=4

//Problem 11: Place Tiles of size 1*m in a floor of size n*m, where n=4, m=2 ??

//Problem 12: Find the number of ways in which you can invite n people to your party, singles or in pairs ??

//Problem 13: Print all the subets of a set of first n natural numbers ?? 
///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

import java.util.ArrayList;
import java.util.HashSet;
//import javax.management.PersistentMBean;
//import javax.print.event.PrintEvent;

class Main {

  // problem 1:
  static void towerOfHanoi(int m, char fromRod, char toRod, char auxRod) {
    if (m == 1) {

      System.out.println("Move disk 1 from rod " + fromRod + " to rod " + toRod);
      return;
    }
    towerOfHanoi(m - 1, fromRod, auxRod, toRod);
    System.out.println("Move disk 1 from rod " + fromRod + " to rod " + toRod);
    towerOfHanoi(m - 1, toRod, fromRu ujjod, auxRod);
  }

  // problem 2:
  static void printRev(String str, int idx) {
    if (idx == 0) {
      System.out.println(str.charAt(idx));
      return;
    }
    System.out.print(str.charAt(idx));
    printRev(str, idx - 1);
  }

  // Problem 3:
  static boolean Sorting(int arr[], int idx) {
    if (idx == arr.length - 1) {
      return true;
    }
    if (arr[idx] >= arr[idx + 1]) {
      // array is unsorted
      return false;
    }
    return Sorting(arr, idx + 1);
  }

  // Problem 4:
  static void moveAllx(String str1, int idx, int count, String newString) {
    if (idx == str1.length()) {
      for (int i = 0; i < count; i++) {
        newString += 'x';
      }
      System.err.println(newString);
      return;
    }
    char currChar = str1.charAt(idx);
    if (currChar == 'x') {
      count++;
      moveAllx(str1, idx + 1, count, newString);
    } else {
      newString += currChar; // newString = newstring + currShar
      moveAllx(str1, idx + 1, count, newString);
    }
  }

  // Problem 5:

  static boolean[] map = new boolean[26];

  static void removeDuplicates(String str2, int idx, String newString) {
    if (idx == str2.length()) {
      System.out.println(newString);
      return;
    }
    char currChar = str2.charAt(idx);
    if (map[currChar - 'a']) {
      removeDuplicates(str2, idx + 1, newString);
    } else {
      newString += currChar;
      map[currChar - 'a'] = true;
      removeDuplicates(str2, idx + 1, newString);
    }

  }

  // Problem 6:
  static void subsequences(String str3, int idx, String newString) {
    if (idx == str3.length()) {
      System.out.println(newString);
      return;
    }

    char currChar = str3.charAt(idx);

    // to be
    subsequences(str3, idx + 1, newString + currChar);

    // or not to be

    subsequences(str3, idx + 1, newString);
  }

  // Problem 7:
  static void uniquesubsequences(String str4, int idx, String newString, HashSet<String> set) {
    if (idx == str4.length()) {
      if (set.contains(newString)) {
        return;
      } else {
        System.out.println(newString);
        set.add(newString);
        return;
      }
    }

    char currChar = str4.charAt(idx);

    // to be
    uniquesubsequences(str4, idx + 1, newString + currChar, set);

    // or not to be

    uniquesubsequences(str4, idx + 1, newString, set);
  }

  // Problem 8:
  static String[] keypad = { ".", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tu", "vwx", "yz" };

  static void printComb(String str5, int idx, String combination) {
    if (idx == str5.length()) {
      System.out.println(combination);
      return;
    }
    char currChar = str5.charAt(idx);
    String mapping = keypad[currChar - '0'];

    for (int i = 0; i < mapping.length(); i++) {
      printComb(str5, idx + 1, combination + mapping.charAt(i));
    }
  }

  // Problem 9:
  static void printPerm(String str6, String permutation) {
    if (str6.length() == 0) {
      System.out.println(permutation);
      return;
    }
    for (int i = 0; i < str6.length(); i++) {
      char currChar = str6.charAt(i);
      // "abc" -> "ab"
      String newStr = str6.substring(0, i) + str6.substring(i + 1);
      printPerm(newStr, permutation + currChar);
    }
  }

  // Problem 10:
  static int countPaths(int i, int j, int n, int m1) {
    if (i == n || j == m1) {
      return 0;
    }
    if (i == n - 1 && j == m1 - 1) {
      return 1;
    }
    // move downwards
    int downpath = countPaths(i + 1, j, n, m1);

    // move right
    int rightpath = countPaths(i, j + 1, n, m1);
    return downpath + rightpath;
  }

  // Problem 11:
  static int placeTiles(int n1, int m2) {
    if (n1 == m2) {
      return 2;
    }
    if (n1 < m2) {
      return 1;
    }

    // for vertically placement
    int vertPlacements = placeTiles(n1 - m2, m2);

    // for horizontally placement
    int horPlacement = placeTiles(n1 - 1, m2);
    return vertPlacements + horPlacement;
  }

  // Problem 12:
  static int callGuests(int n2) {
    if (n2 <= 1) {
      return 1;
    }

    // for single pairs
    int ways1 = callGuests(n2 - 1);
    // for pairs
    int ways2 = (n2 - 1) * callGuests(n2 - 2);
    return ways1 + ways2;
  }

  // Problem 13:
  static void printsubset(ArrayList<Integer> subset) {
    for (int i = 0; i < subset.size(); i++) {
      System.out.print(subset.get(i) + " ");
    }
    System.out.println();
  }

  static void findSubsets(int n3, ArrayList<Integer> subset) {
    if (n3 == 0) {
      printsubset(subset);
      return;
    }

    // Should add
    subset.add(n3);
    findSubsets(n3 - 1, subset);

    // should not add
    subset.remove(subset.size() - 1);
    findSubsets(n3 - 1, subset);

  }

  public static void main(String[] args) {

    // Problem 1:
    int m = 3;
    char fromRod = 'A', toRod = 'C', auxRod = 'B';
    System.out.println("1)The implementation of Tower of Hanoi is: ");
    towerOfHanoi(m, fromRod, toRod, auxRod);
    System.out.println();

    // Problem 2:
    String str = "ABCD";
    System.out.print("2)the reverse string is: ");
    printRev(str, str.length() - 1);
    System.out.println();

    // Problem 3:
    int arr[] = { 1, 2, 4, 6 };
    System.out.println("3)The given Array is Sorted i.e.: " + (Sorting(arr, 0)));
    System.out.println();

    // Problem 4:
    String str1 = "Gxxoxxvxixxxnxd";
    System.out.print("4)the final String after moving 'x' at the end is : ");
    moveAllx(str1, 0, 0, "");
    System.out.println();

    // Problem 5:
    String str2 = "abbdssfgjsshrrfisdojj";
    System.out.print("5)the final String after removing the duplicates from the given String is: ");
    removeDuplicates(str2, 0, "");
    System.out.println();

    // Problem 6:
    String str3 = "abc";
    System.out.println("6)The Subsequences of string (abc) is: ");
    subsequences(str3, 0, "");
    System.out.println();

    // Problem 7:
    String str4 = "aaa";
    HashSet<String> set = new HashSet<>();
    System.out.println("7)The Unique Subsequences of string (aaa) is: ");
    uniquesubsequences(str4, 0, "", set);
    System.out.println();

    // Problem 8:
    String str5 = "23";
    System.out.println("8)The keypad Combination of a mobile is: ");
    printComb(str5, 0, "");
    System.out.println();

    // Problem 9:
    String str6 = "abc";
    System.out.println("9)The permutations of a String (abc) is:");
    printPerm(str6, "");
    System.out.println();

    // Problem 10:
    int n = 3, m1 = 3;
    int totalPaths = countPaths(0, 0, n, m1);
    System.out.println("10)The total paths in a maze to move from (0,0) to (n,m) is: " + totalPaths);
    System.out.println();

    // Problem 11:
    int n1 = 4, m2 = 2;
    System.out.println("11)The Tiles can be placed in " + placeTiles(n1, m2) + " ways !!!");
    System.out.println();

    // Problem 12:
    int n2 = 4;
    System.out.println(
        "12)The number of ways in which you can invite people to your party is: " + callGuests(n2) + " ways !!!");
    System.out.println();

    // Problem 13:
    int n3 = 3;
    ArrayList<Integer> subset = new ArrayList<>();
    System.out.println("13)The subets of a set of first n natural numbers is: ");
    findSubsets(n3, subset);
  }
}
