# Binary Tree and Devide Conquer
Lintcode: [Binary Tree and Devide Conquer](http://www.lintcode.com/en/problem/binary-tree-maximum-path-sum-ii/)

Given a binary tree, find the maximum path sum from root.

The path may end at any node in the tree.


---



左右找个大于0的 没有就不取

    public int maxPathSum2(TreeNode root){
        if(root == null){
            return 0;
        }
        
        int maxSum = root.val;
        int sumright = maxPathSum2(root.right);
        int sumleft = maxPathSum2(root.left);
        if(sumright < 0){   
            sumright = 0;
        }
        if(sumleft < 0){   
            sumleft = 0;
        }
        
        if(sumright>sumleft){
            maxSum +=sumright;
        }else{
            maxSum +=sumleft;
        }
        
        return maxSum;
    }

这样写超时了 我真2

    public int maxPathSum2(TreeNode root) {
        // Write your code here
        if(root == null){
            return 0;
        }
        
        int maxSum = root.val;
        int sumright = 0, sumleft = 0;
        
        if(root.right != null && maxPathSum2(root.right) > 0){
            sumright = maxPathSum2(root.right);
        }
        
        if(root.left != null && maxPathSum2(root.left) > 0){
            sumleft = maxPathSum2(root.left);
        }       
        
        if(sumright>sumleft){
            maxSum +=sumright;
        }else{
            maxSum +=sumleft;
        }
        
        return maxSum;
        
    }