# Problem 1 -  Pow(x, n)
## Time Complexity :
O(logN)

## Space Complexity :
O(1)

## Did this code successfully run on Leetcode :
No.

## Any problem you faced while coding this :
Yes. Cannot figure out the problem.
        
### Solution:
    class Solution:
        def myPow(self, x: float, n: int) -> float: 
            if n<0:
                x=1/x
                n=-n
            def power(x: float,n: int):
                if n==0:
                    return 1
                if n==1:
                    return x
                value = power(x,n/2)
                if n%2==0:
                    return value*value
                else:
                    return x*value*value

            return power(x,n) 
