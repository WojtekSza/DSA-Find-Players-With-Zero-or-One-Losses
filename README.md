# DSA-Find-Players-With-Zero-or-One-Losses
You are given an integer array matches where matches[i] = [winneri, loseri] indicates that the player winneri defeated player loseri in a match.

Return a list answer of size 2 where:

answer[0] is a list of all players that have not lost any matches.
answer[1] is a list of all players that have lost exactly one match.
The values in the two lists should be returned in increasing order.

Note:

You should only consider the players that have played at least one match.
The testcases will be generated such that no two matches will have the same outcome.
```
Input: matches = [[1,3],[2,3],[3,6],[5,6],[5,7],[4,5],[4,8],[4,9],[10,4],[10,9]]
Output: [[1,2,10],[4,5,7,8]]
Explanation:
Players 1, 2, and 10 have not lost any matches.
Players 4, 5, 7, and 8 each have lost one match.
Players 3, 6, and 9 each have lost two matches.
Thus, answer[0] = [1,2,10] and answer[1] = [4,5,7,8].
```
```
from collections import defaultdict
class Solution:
    def findWinners(self, matches: List[List[int]]) -> List[List[int]]:
        ans=[]
        no_lost=set()
        one_lost=set()
        counts=defaultdict(int)
        #Time cost of iteration thru list O(n)
        for i in matches:
            counts[i[0]]+=0
            counts[i[1]]+=1
        #Time cost of iteration thru dict O(n)
        for x,y in counts.items():
            if y==0:
                no_lost.add(x)
            elif y==1:
                one_lost.add(x)
        #Total time cost O(n)+O(n)+O(log(n) = 2O(n) +O(log(n)=> O(n*log(n))
        ans.append(sorted(no_lost))
        ans.append(sorted(one_lost))
        #Space cost O(n)+O(n) = 2O(n)=> O(n)
        return ans
```
