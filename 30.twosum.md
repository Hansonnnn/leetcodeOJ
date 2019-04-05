### twoSum

Question:
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,

return [0, 1].
code:
```
public int[] twoSum(int[] nums, int target) {
    int[] res=new int[2];
    int len=nums.length;
    for(int i=0;i<len;i++)
      for(int j=len-1;j<len&&j>=0;j--)
    {
        if(nums[i]+nums[j]==target&&i!=j) {
            res[0]=i;
            res[1]=j;
            break;
        }
    }
      return res;
}
