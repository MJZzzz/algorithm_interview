# Array and Numbers
lintcode: [Majority Number](http://www.lintcode.com/en/problem/majority-number/)

Given an array of integers, the majority number is the number that occurs more than half of the size of the array. Find it.

Have you met this question in a real interview? Yes
Example
Given [1, 1, 1, 1, 2, 2, 2], return 1

Challenge
O(n) time and O(1) extra space



使用哈希表统计不同数字出现的次数，超过二分之一即返回当前数字.
占据过多空间

```
 public int majorityNumber(ArrayList<Integer> nums) {
        // write your code
        if(nums == null || nums.size() == 0){
            return -1;
        }
        
        HashMap<Integer,Integer> map = new HashMap<Integer,Integer>();
        for(int i =0; i < nums.size(); i++){
            if(map.containsKey(nums.get(i))){
                map.put(nums.get(i), map.get(nums.get(i)) + 1);
            }else{
                map.put(nums.get(i), 1);
            }
            if(map.get(nums.get(i)) > nums.size()/2){
                return nums.get(i);
            }
            
            
        }
        
        return -1;
        
    }```
两两抵消
```
    public int majorityNumber(ArrayList<Integer> nums) {
        int count = 0, candidate = -1;
            
            for(int i : nums){
                if(count == 0){
                    candidate = i;
                    count++;
                }else if(i == candidate){
                    count++;
                }else{
                    count --;
                }
            }
            
            return candidate;
    }    
```    
    
两两抵消 第二种 这个过不了
```
    public int majorityNumber(ArrayList<Integer> nums) {
        // write your code
        /*
        ArrayList<Integer> mynum = nums;
        if(mynum == null || mynum.size() == 0){
            return -1;
        }
        int move = 1;
        //int i = 0; i < mynum.size(); i++
        while(move < mynum.size()){
            if(mynum.get(0) != mynum.get(move) && move > 0){
                mynum.remove(move);
                mynum.remove(0);
                move--;
            }else{
                move++;
            }
        }
        return mynum.get(0);
    }
```

