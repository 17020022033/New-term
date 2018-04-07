# 419. 甲板上的战舰
## 题目
给定一个二维的甲板， 请计算其中有多少艘战舰。 战舰用 'X'表示，空位用 '.'表示。 你需要遵守以下规则：      
给你一个有效的甲板，仅由战舰或者空位组成。       
战舰只能水平或者垂直放置。换句话说,战舰只能由 1xN (1 行, N 列)组成，或者 Nx1 (N 行, 1 列)组成，其中N可以是任意大小。       
两艘战舰之间至少有一个水平或垂直的空位分隔 - 即没有相邻的战舰。        
示例 :      
X..X      
...X     
...X        
在上面的甲板中有2艘战舰。       
无效样例 :        
...X         
XXXX         
...X              
你不会收到这样的无效甲板 - 因为战舰之间至少会有一个空位将它们分开。           
进阶:            
你可以用一次扫描算法，只使用O(1)额外空间，并且不修改甲板的值来解决这个问题吗？           
## 思路
想到的方法是改board的值，把遍历过的船都改成‘.'，就 直接数船头。     
后来找了一下看到可以直接遍历，再观察一下这条船是不是船身，如果是就不加总数。 
别人的方法总是比自己的酷很多😯    
最后返回总数就好。    
## 代码一
```ruby
int countBattleships(vector<vector<char>>& board) {  
    int total = 0;  
    int x = board.size();  
    int y = board[0].size();  
    for(int i = 0;i<x;i++){  
        for(int j = 0;j<y;j++){  
            if(board[i][j] == 'X'){  
                if(i-1<0 || board[i-1][j] != 'X'){  
                    if(j-1<0 || board[i][j-1] != 'X'){  
                        total++;  
                    }  
                }  
            }  
        }  
    }  
    return total;  
}  
```
## 代码二
```ruby
class Solution {
public:
    int countBattleships(vector<vector<char>>& board) {
        int x=board.size();
        int y=board[0].size();
        int total=0;
        for(int i=0;i<x;i++)
            for(int j=0;j<y;j++)
            {
                int a=i;
                int b=j;
                if(board[i][j]=='X')
                {
                     while(a!=x)
                    {
                        board[a][j]='.';
                        a++;
                        if(board[a][j]=='.'||a==x)
                            break;
                    }
                    while(b!=y)
                    {
                        board[i][b]='.';
                        b++;
                        if(board[i][b]=='.'||b==y)
                            break;
                    }
                total++;
                }
            }
        return total;
    }
};
```
