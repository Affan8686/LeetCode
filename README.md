# LeetCode
class Solution(object):
    def minSubArrayLen(self, target, nums):
        n = len(nums)
        start = 0
        current_sum = 0
        min_length = float('inf')
        for end in range(n):
            current_sum += nums[end]
            # Shrink the window as much as possible while the sum is >= target
            while current_sum >= target:
                min_length = min(min_length, end - start + 1)
                current_sum -= nums[start]
                start += 1
        # If min_length is not updated, return 0 (no such subarray exists)
        return min_length if min_length != float('inf') else 0
