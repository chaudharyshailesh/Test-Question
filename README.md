# 1 Test-Question
package com.textexp;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.Scanner;

public class Solution3LargestNo {
	private static ArrayList<String> longestWords(String[] a, int len) {
		String temp = "";
		ArrayList<String> arraylist = new ArrayList<>();

		if (len < 3) {
			if (a[0].length() > a[1].length()) {
				arraylist.add("#"+a[0]);
				arraylist.add("#"+a[1]);
			} else {
				swap(a, 0,1);
				arraylist.add("#"+a[0]);
				arraylist.add("#"+a[1]);
			}
			return arraylist;
		} else {

			bubbleSort(a);
			
			for (int k = 0; k < 3; k++) {
				arraylist.add("#" + a[k]);
			}
			return arraylist;
		}
	}
	
    public static void bubbleSort(String[] arr) {
        boolean swapped = false;
        do {
            swapped = false;
            for (int i = 0; i < arr.length - 1; i += 1) {
                if (arr[i].length() < arr[i + 1].length()) {
                    swap(arr, i, i + 1);
                    swapped = true;
                }
            }
        } while (swapped);
    }

    public static void swap(String[] arr, int index0, int index1) {
        String temp = arr[index0];
        arr[index0] = arr[index1];
        arr[index1] = temp;
    }

	public static void main(String[] args) {
		// String s="Why You Will Probably Pay More for Your Christmas Tree This Year";
		Scanner sc = new Scanner(System.in);
		System.out.println("Please Enter Sentence ");
		String s = sc.nextLine();
		String[] words = s.split(" ");
		int ln = words.length;
		System.out.println("Original String : " + Arrays.toString(words));
		System.out.println("Longest 3 word(s) of the above String: " + longestWords(words, ln));
		sc.close();
	}
}



# 2 Test-Question

package com.textexp;

import java.util.Scanner;

public class DescendantPalindrome {
	private static boolean PalindromDesendant(int num) {

		boolean isSum = false;
		while (num > 9) {
			if (isSymmetrical(num)) {
				isSum = true;
				break;
			}
			num = getSumOfTwoDigits(num);
		}
		return isSum;
	}

	private static int getSumOfTwoDigits(int n) {
		String str = Integer.toString(n);
		StringBuilder sb = new StringBuilder();
		for (int i = 0; i < str.length() - 1; i += 2) {
			int i1 = Integer.parseInt(Character.toString(str.charAt(i)));
			int i2 = Integer.parseInt(Character.toString(str.charAt(i + 1)));
			int sum = i1 + i2;
			sb.append(Integer.toString(sum));
			
		}
		System.out.println(Integer.parseInt(sb.toString()));
		return Integer.parseInt(sb.toString());
	}

	private static boolean isSymmetrical(int num) {
		int reversenum = 0, n = num;
		if (n < 0)
			n = n * -1;
		while (n != 0) {
			reversenum = reversenum * 10;
			reversenum = reversenum + n % 10;
			n = n / 10;
		}

		return (reversenum == num);
	}

	public static void main(String[] args) {

		Scanner sc=new Scanner(System.in);
		System.out.println("Please Enter number ");
		int desentNum=sc.nextInt();
		System.out.println(PalindromDesendant(desentNum));
		sc.close();
	}

}


