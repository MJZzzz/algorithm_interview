# Array and Numbers
lintcode: [Majority Number](http://www.lintcode.com/en/problem/majority-number/)

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
    
    
这个过不了

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


