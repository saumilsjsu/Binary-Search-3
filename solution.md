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

# Problem 2 -  Find K Closest Elements
## Time Complexity :
O(logN + k)

## Space Complexity :
O(1)

## Did this code successfully run on Leetcode :
Yes.

## Any problem you faced while coding this :
No.
        
### Solution:
                class Solution:
                    def findClosestElements(self, arr: List[int], k: int, x: int) -> List[int]:
                        right = self.find_upper_closest(arr, x)
                        left = right - 1

                        for _ in range(k) :
                            if left < 0  or right > len(arr) - 1:
                                break
                            if arr[right] - x < x - arr[left]:
                                right+= 1   
                            else:
                                left -= 1

                        if left < 0: 
                            return arr[0:k]
                        elif right > len(arr) - 1: 
                            return arr[-k:]
                        else: 
                            return arr[right - k:right]

                    def find_upper_closest(self, arr, x):
                        start, end = 0, len(arr) - 1
                        while start + 1 < end:
                            mid = (start + end) // 2
                            if arr[mid] >= x:
                                end = mid
                            else:
                                start = mid
                        if arr[start] >= x:
                            return start
                        if arr[end] >= x:
                            return end 

                        return len(arr)

# Problem 3 -  Optimize Air Routes
## Time Complexity :
O()

## Space Complexity :
O()

## Did this code successfully run on Leetcode :
N/A

## Any problem you faced while coding this :

        
### Solution:
def closestXDestionation(forward, backward, maximum):
  combined = [[i, j] for i in forward for j in backward]

  temp = []
  for i in range(len(combined)):
    if combined[i][0][1] + combined[i][1][1] <= maximum:
      temp.append([combined[i][0],combined[i][1]])

  largest = max(temp, key=lambda x:x[0][1] + x[1][1])
  route = [path[0] for path in largest]
  return route
