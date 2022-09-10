#include<stack>
#include<string>

int countBracketReversals(string input){
    // Write your code here
    stack<char> st;
    int l = input.size();
    int count;
    if(!(l & 1)) {
        for(int i = 0; i < l; i++) {
            if(input[i] == '{') {
                //push onto stack
                st.push(input[i]);
                
            } else if(input[i] == '}' and !st.empty()) {
                if(st.top() == '{') {
                    st.pop();
                } else {
                    st.push(input[i]);
                }
            } else {
                st.push(input[i]); // when the first character is '}'
            }
        }
        count = 0;
        
        while(!st.empty()) {
            char c1 = st.top();
            st.pop();
            
            char c2 = st.top();
            st.pop();
            
            if(c1 == c2) {
                count++; // if the characters are same we need to invert one of them
            } else {    //	if they are different we need to invert both
                count += 2;
            }
        }
        
        return count;
    } else { // if the length is odd then we cannot balance them
        
        return -1;
    }
}