# degree-of-an-array
📝 Problem
Find the smallest subarray with the same degree as the original array.
🚀 Approach
- Store frequency and first index
- Find degree
- Calculate minimum length

⏱ Complexity
Time: O(n)
Space: O(n)

code:
class Solution {
    public int findShortestSubArray(int[] nums) {

        HashMap<Integer, Integer> count = new HashMap<>();
        HashMap<Integer, Integer> first = new HashMap<>();
        HashMap<Integer, Integer> last = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {

            int num = nums[i];

            first.putIfAbsent(num, i);
            last.put(num, i);

            count.put(num, count.getOrDefault(num, 0) + 1);
        }

        int degree = 0;
        for (int val : count.values()) {
            degree = Math.max(degree, val);
        }

        
        int minLen = nums.length;

        for (int num : count.keySet()) {
            if (count.get(num) == degree) {
                int len = last.get(num) - first.get(num) + 1;
                minLen = Math.min(minLen, len);
            }
        }

        return minLen;
    }
}

Dry Run
nums = [1,2,2,3,1]

👉 For 1:

first = 0, last = 4
length = 5

👉 For 2:

first = 1, last = 2
length = 2 ✅ (smallest

If you found this helpful, give it a ⭐ and follow for more such solutions 🚀
