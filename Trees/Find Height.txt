#include<vector>

int getHeight(TreeNode<int>* root) {
    // Write your code here
    //corner case 
    if(root == NULL) {
        return 0;
    }
    int count = 0;
	
    for(int i = 0; i < root ->children.size(); i++) {
        int temp = getHeight(root -> children[i]);
        count = max(temp,count);
    }
    return count + 1;
}