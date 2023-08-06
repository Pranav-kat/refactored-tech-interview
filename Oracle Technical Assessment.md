---
share: true
---
1. GOOD, BAD, MIXED
 ```cpp
	#include "string.h"
	#include"iostream"
    using namespace std;

    bool alphabetcheck(char alphabet){
        if (alphabet >= 'a' && alphabet <= 'z')
            return true;
        return false;
    }

    int vowelcheck(char vowel)
    {
        if (vowel == 'a' || vowel == 'e' || vowel == 'i' || vowel == 'o' || vowel == 'u')
            return 0;
        return 1;
    }

    
 int main(void) {
    string X = "wayt?arack"; 
    int XLen = X.size();
    int Arr[2][20];
    memset(Arr, 0, sizeof(Arr[0][0]) * 2 * 20);
    int max0 = 0;
    int max1 = 0;
    int index;
    bool mixed_value = false;
    for (size_t i = 0; i < XLen; i++)
    {
        //alphabet check
        if (alphabetcheck(X[i]))
        {
            //vowel check fucntion:
            if ((vowelcheck(X[i])) == 0)
            {
                Arr[0][i+1] = Arr[0][i] + 1;
                if (Arr[0][i + 1] > max0)
                    max0 = Arr[0][i + 1]; //check for max 0
                if ((mixed_value == true) && (max0 >= 5) && (Arr[0][i + 1] >= 5)) 
                {
                    if ((i - index >= 5 || (Arr[1][index] + Arr[0][index + 5] == 7)))
                     mixed_value = false;
                }
            }
            else
            {
                Arr[1][i + 1] = Arr[1][i] + 1;
                if (Arr[1][i + 1] > max1)
                    max1 = Arr[1][i + 1]; //check for max 1
                if (mixed_value == true && max1 >= 3 && Arr[1][i + 1] >= 3 ) 
                {
                    if ((i - index >= 3 || (Arr[0][index] + Arr[1][index + 3] == 7)) )
                        mixed_value = false;
                }
            }
            if (mixed_value == false && (max0 >= 5 || max1 >= 3)){
                cout << " BAD " << endl;
                exit(0);
            }
        }
        
        else if (X[i] == '?'){
            Arr[0][i + 1] = Arr[0][i] + 1;
            if (Arr[0][i + 1] > max0)
                max0 = Arr[0][i + 1]; //check for max 1
            Arr[1][i + 1] = Arr[1][i] + 1;
            if (Arr[1][i + 1] > max1)
                max1 = Arr[1][i + 1]; //check for max 1
            index = i;
            mixed_value = true;
        }
    }

    
    if (mixed_value & (max0 >= 5 || max1 >= 3))
        cout << " MIXED " << endl;
    else cout << " GOOD " << endl;
    
    return 0;
 }
 ```
2. Maximum Volume
 ``` java
	static int maxvalue=-1;  
	public static void count(int a[],int low,int high,int index,int curr)  
    {  
    if(index==0)  
    {  
    if(curr+a[index]>high || curr+a[index]high || curr<low)  
    return;  
    maxvalue=Math.max(maxvalue, curr);

    if(index==a.length)  
    return;

    count(a, low, high, index+1, curr+a[index]);  
    count(a, low, high, index+1, curr-a[index]);  
    }
 ```
3. Subsequences of string 'Vowel - Consonant'
	```java
 import java.util.HashSet;
 public class Subsequence {
    // Set to store all the subsequences
    static HashSet<String> st = new HashSet<>();
    // It computes all the possible substring that
    // starts with vowel and end with consonent
    static void subsequence(String str)
    {
        // iterate over the entire string
        for (int i = 0; i < str.length(); i++) {
        
            // test ith character for vowel
            if (isVowel(str.charAt(i))) {
        
                // if the ith character is vowel
                // iterate from end of the string
                // and check for consonant.
                for (int j = (str.length() - 1); j >= i; j--) {
                    
                    // test jth character for consonant.
                    if (isConsonant(str.charAt((j)))) {
                    
                        // once we get a consonant add it to
                        // the hashset
                        String str_sub = str.substring(i, j + 1);
                        st.add(str_sub);
                        // drop each character of the substring
                        // and recur to generate all subsquence
                        // of the substring
                        for (int k = 1; k < str_sub.length() - 1; k++) {
                            StringBuffer sb = new StringBuffer(str_sub);
                            sb.deleteCharAt(k);
                            subsequence(sb.toString());
                        }
                    }
                }
            }
        }
    }
    // Utility method to check vowel
    static boolean isVowel(char c)
    {
        return (c == 'a' || c == 'e' || c == 'i' || c == 'o'
                                              || c == 'u');
    }
    // Utility method to check consonant
    static boolean isConsonant(char c)
    {
        return !(c == 'a' || c == 'e' || c == 'i' || c == 'o'
                                              || c == 'u');
    }
    // Driver code
    public static void main(String[] args)
    {
        String s = "xabcef";
        subsequence(s);
        System.out.println(st);
    }
 }

 ```
4. Election Winner
	```java
	// Java program to find winner in an election.
 import java.util.*;
 public class ElectoralVotingBallot {
	/* We have four Candidates with name as 'John',
	'Johnny', 'jamie', 'jackie'.
	The votes in String array are as per the
	votes casted. Print the name of candidates
	received Max vote. */
	public static void findWinner(String votes[])
	{
		// Insert all votes in a hashmap
		Map<String, Integer> map
			= new HashMap<String, Integer>();
		for (String str : votes) {
			if (map.keySet().contains(str))
				map.put(str, map.get(str) + 1);
			else
				map.put(str, 1);
		}

		// Traverse through map to find the candidate
		// with maximum votes.
		int maxValueInMap = 0;
		String winner = "";
		for (Map.Entry<String, Integer> entry :
			map.entrySet()) {
			String key = entry.getKey();
			Integer val = entry.getValue();
			if (val > maxValueInMap) {
				maxValueInMap = val;
				winner = key;
			}

			// If there is a tie, pick lexicographically
			// smaller.
			else if (val == maxValueInMap
					&& winner.compareTo(key) > 0)
				winner = key;
		}
		System.out.println(winner);
	}

	// Driver code
	public static void main(String[] args)
	{
		String[] votes
			= { "john", "johnny", "jackie", "johnny",
				"john", "jackie", "jamie", "jamie",
				"john", "johnny", "jamie", "johnny",
				"john" };

		findWinner(votes);
	}
 }
 ```
5. Min pan cakes
	``` python
	def count(n,m):  
		arr = [0]*n  
        i=0  
        while(sum(arr)!=4):  
	        if arr[i]==1:  
		        return(‘NO ‘+str(sum(arr)))  
	        break  
	        else:  
		        arr[i]+=1  
		        i = m+i  
	            if i>=n:  
			        i = i-n  
        return(‘YES’)
	```
6. Row with max 1s
	```python
	def rowWithMaxOnes (X, row, col):
	     maxRowIndex = -1
	     currCol = col - 1
	     for i in range (row):
	         while currCol >= 0 and x[i][ [currCol] == 1:
	             currCol = currCol - 1
	             maxRowIndex
	     return maxRowIndex
	```
7. Set Matrix zeroes
	 ```java
     public class Solution {
 public void setZeroes(ArrayList<ArrayList<Integer>> a) {
 int row = a.size();
 int col = 0;
 if (row > 0)
 {
 col = a.get(0).size();
 }
 //this means a is empty
 else{
 return;
 }
 HashSet<Integer> row_list = new HashSet<>();
 HashSet<Integer> col_list = new HashSet<>();
 // This iteration is to get a list of all rows and column # to be changed
 for (int i = 0; i < row; i++)
 {
 for (int j = 0; j < col; j++)
 {
 if (a.get(i).get(j) == 0)
 {
 row_list.add(i);
 col_list.add(j);
 }
 }
 }
 // This iteration is to change the element the row and column derived above
 for (int l = 0; l < row; l++)
 {
 for (int m = 0; m < col; m++)
 {
 if (row_list.contains(l) || col_list.contains(m))
 {
 a.get(l).set(m,0);
 }
 }
 }
 }
 }
 ```