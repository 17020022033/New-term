# 205. 同构字符串
## 题目
给定两个字符串 s 和 t，判断它们是否是同构的。  
如果 s 中的字符可以被替换最终变成 t ，则两个字符串是同构的。  
所有出现的字符都必须用另一个字符替换，同时保留字符的顺序。两个字符不能映射到同一个字符上，但字符可以映射自己本身。  
例如，  
给定 "egg", "add", 返回 true.  
给定 "foo", "bar", 返回 false.  
给定 "paper", "title", 返回 true.  
注意：  
你可以假设 s 和 t 具有相同的长度。  
## 超出时间限制的算法
```ruby
bool isIsomorphic(char* s, char* t) {
    int n=0;
    n=strlen(s);
    for(int i=0;i<n;i++)
    for(int j=0;j<i;j++)
    if(s[i]==s[j]&&t[i]!=t[j]||s[i]!=s[j]&&t[i]==t[j])
    return false;
    return true;
}
```
## 哈希表算法
```ruby
bool isIsomorphic(string s, string t) {
        map<char,int> hash1;
        map<char,int> hash2;
        int len1=s.length();
        int len2=t.length();
        if(len1 != len2) return false;
        for(int i=0;i<len1;++i){
            if((hash1.find(s[i]) == hash1.end()) && (hash2.find(t[i]) == hash2.end())){
                hash1[s[i]]=i;
                        hash2[t[i]]=i;
            }
                   else if((hash1.find(s[i]) != hash1.end()) && (hash2.find(t[i]) != hash2.end())){
                   if(hash1[s[i]]!=hash2[t[i]])return false;
            }
                  else return false;
        }
        return true;
    }
```
## 分析
题目本身不算太难，我开始用的最简单的思路是逐个逐个比较一下看看对不对。
但是样例测试里面有一个特别长的样例，这个很烂的算法就超出时间限制了。  
然后上网找了一下大佬的代码，发现他们用了哈希表这个东西可以节省好多时间。 
今天想做移除元素的，但是数组出现了很奇怪的情况，一直没搞定，刚好新学了一下哈希表。  
明天要再试试哈希表，顺便把移除元素做出来。
## 总结
哈希表可以节省时间，快速地找出数据。  
头文件是hash_map.  
声明是map<类型,类型> namemap;   
hash_map里面的(namemap.find(key) == namemap.end()可以用来找关键字（key）  
