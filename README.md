# Find the link at:
  https://leetcode.com/problems/permutation-sequence/description/

# Problem Description:
  The set [1,2,3,...,n] contains a total of n! unique permutations.

  By listing and labeling all of the permutations in order, we get the following sequence for n = 3:
    1. "123"
    2. "132"
    3. "213"
    4. "231"
    5. "312"
    6. "321"
  
  Given n and k, return the kth permutation sequence.

  Note:
    Given n will be between 1 and 9 inclusive.
    Given k will be between 1 and n! inclusive.
  
  Example 1:
    Input: n = 3, k = 3
    Output: "213"
  Example 2:
    Input: n = 4, k = 9
    Output: "2314"
    
# Idea：
  1. Obviously:
  
     For the 1st digit: n possibilities;
  
     For the 2nd digit: n-1 possibilities;
     
     \...
     
  2. Think in another way:
  
     if the 1st digit is fixed, then there are (n-1)! possibilities of the remaining digits;
     
     \...
     
     if the d_st digit is fixed, then there are (n-d)! possibilities of the remaining digits;
     
  3. Since the permutations are listed in order, so we can consider digit by digit from left to right, the algorithm is as below. 
  
     Take n=3, k=3 as an example to explain:
     
     1 ）Decide the 1st digit:
     
        x = k/(n-1)!  =  3/2  =  1.5 
        
          Note: Since all the numbers are int by default, I added 0.0 to the (n-1)!, then we got the correct outcome.
          
        If the result is between (d,d+1], then the 1st_digit is d+1; here d=1, then the 1st_digit is 2.
        
     2） Then there are 2 digits to be decided.
     
        Since the 1st digit is fixed, we can let k minus the (1st_digit - 1)x(n-1)!. 
        
        Now, the 2nd digit can be regarded as the 1st digit in this round.
        
        Then, repeat the 1) step until all the digits are added to the result.
        
   
        
     
