# New-term
class Solution {
public:
    bool isPowerOfThree(int n) {
        int i=0;
        if(n==0||n==2)
            return false;
        if(n==1)
            return true;
        while(n!=3&&i==0)
        {
            i=n%3;
            n=n/3;
        }
        if(i==0)
            return true;
        else 
            return false;
    }
};
