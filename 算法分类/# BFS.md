### 127. 最短单词路径

**Word Ladder**

A **transformation sequence** from word `beginWord` to word `endWord` using a dictionary `wordList` is a sequence of words `beginWord -> s1 -> s2 -> ... -> sk` such that:

- Every adjacent pair of words differs by a single letter.
- Every `si` for `1 <= i <= k` is in `wordList`. Note that `beginWord` does not need to be in `wordList`.
- `sk == endWord`

Given two words, `beginWord` and `endWord`, and a dictionary `wordList`, return *the **number of words** in the **shortest transformation sequence** from* `beginWord` *to* `endWord`*, or* `0` *if no such sequence exists.*

```java
Input: beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log","cog"]
Output: 5
Explanation: One shortest transformation sequence is "hit" -> "hot" -> "dot" -> "dog" -> cog", which is 5 words long.
```



#### 【BFS】

// Typora打数学符号 用ctrl + shift + m
$$
O(NC^2)
$$ {N是wordList的长度，C为列表中单词的长度}

$$
O(NC^2)
$$



```java
class Solution {

    public int ladderLength(String beginWord, String endWord, List<String> wordList) {
        // 第 1 步：先将 wordList 放到哈希表里，便于判断某个单词是否在 wordList 里
        Set<String> wordSet = new HashSet<>(wordList);
        if (wordSet.size() == 0 || !wordSet.contains(endWord)) {
            return 0; //如果endword不在worldlist里，则无法完成路径
        }
        wordSet.remove(beginWord);
        
        // 第 2 步：图的广度优先遍历，必须使用队列和表示是否访问过的 visited 哈希表
        //queue用于存取需要遍历的值
        //visited是set表，不重复，用于判断是否包含
        //将beginword存放进队列和set集合中，首先搜索beginword
        Queue<String> queue = new LinkedList<>();
        queue.offer(beginWord);
        Set<String> visited = new HashSet<>();
        visited.add(beginWord);
        
        // 第 3 步：开始广度优先遍历，包含起点，因此初始化的时候步数为 1
        int step = 1;
        while (!queue.isEmpty()) {
            int currentSize = queue.size(); //每次if语句后会将更改过的不等于endword的字符串加入queue, queuesize会有变化
            for (int i = 0; i < currentSize; i++) { //i为下标
                // 依次遍历当前队列中的单词
                //将currentword赋值为队列的头并移除
                String currentWord = queue.poll(); 
                // 如果 currentWord 能够修改 1 个字符与 endWord 相同，则返回 step + 1，加上endword本身的位置
                if (changeWordEveryOneLetter(currentWord, endWord, queue, visited, wordSet)) {
                    return step + 1; 
                }
            }
            step++; //如果遍历到的都不与endword相同，则可能是中间的一步，需要step++；
        }
        return 0;
    }

   //需要用到当前的String去修改每个字符，与endWord匹配，用queue和visited存放已经枚举过的所有可能
    private boolean changeWordEveryOneLetter(String currentWord, String endWord,
        Queue<String> queue, Set<String> visited, Set<String> wordSet) {
        char[] charArray = currentWord.toCharArray(); //将字符串对象中的字符转换为一个字符数组
       //将当前需要遍历的字符串数组，从下标0-endWord.length()每个字母都从a-z更改一次，每次都判断是否wordSet里是否包含 
       for (int i = 0; i < endWord.length(); i++) {
            // 先保存原来的字符，然后恢复
            char originChar = charArray[i];
            for (char k = 'a'; k <= 'z'; k++) { //这里是char类型的k
                if (k == originChar) {
                    continue; //如果当前字母相同，则continue执行时，continue下面的代码不执行，直接进入下一循环，k++继续枚举所有可能性
                }
                charArray[i] = k;
                String nextWord = String.valueOf(charArray); //将charArray转换成字符串和endword比较
                if (wordSet.contains(nextWord)) {
                    if (nextWord.equals(endWord)) { //如果nextWord等于endWord,则找到了一条路径
                        return true;
                    }
                    //如果已访问过的hashSet里未包含nextWord,则加入队列
                    if (!visited.contains(nextWord)) {
                        queue.add(nextWord);
                        // 注意：添加到队列以后，必须马上标记为已经访问
                        visited.add(nextWord);
                    }
                }
            }
            // 恢复，接着遍历i+1个char
            charArray[i] = originChar;
        }
        return false;
    }
}
```





#### 【双向BFS】



```java
class Solution {
    public int ladderLength(String beginWord, String endWord, List<String> wordList) {
        // 第 1 步：先将 wordList 放到哈希表里，便于判断某个单词是否在 wordList 里
        Set<String> wordSet = new HashSet<>(wordList);
        if (wordSet.size() == 0 || !wordSet.contains(endWord)) return 0;
        // 第 2 步：已经访问过的 word 添加到 visited 哈希表里
        Set<String> visited = new HashSet<>();
        // 分别用左边和右边扩散的哈希表代替单向 BFS 里的队列，它们在双向 BFS 的过程中交替使用
        Set<String> beginVisited = new HashSet<>();
        beginVisited.add(beginWord);
        Set<String> endVisited = new HashSet<>();
        endVisited.add(endWord);

        // 第 3 步：执行双向 BFS，左右交替扩散的步数之和为所求
        int step = 1;
        while (!beginVisited.isEmpty() && !endVisited.isEmpty()){
            // 优先选择小的哈希表进行扩散，考虑到的情况更少
            if (beginVisited.size() > endVisited.size()){
                Set<String> temp = beginVisited;
                beginVisited = endVisited;
                endVisited = temp;
            }
            // 逻辑到这里，保证 beginVisited 是相对较小的集合，nextLevelVisited 在扩散完成以后，会成为新的 beginVisited
            Set<String> nextVisited = new HashSet<>();
            for (String word : beginVisited){
                if (changeEveryLetter(word, endVisited, visited, wordSet, nextVisited)){
                    return step + 1;
                }
            }
            // 原来的 beginVisited 废弃，从 nextLevelVisited 开始新的双向 BFS
            beginVisited = nextVisited;
            step++;
        }
        return 0;
    }
    
    
    //尝试对 word 修改每一个字符，看看是不是能落在 endVisited 中，扩展得到的新的 word 添加到 nextLevelVisited 里    
    	private boolean changeEveryLetter(String word, Set<String> endVisited,
        Set<String> visited,
        Set<String> wordSet,
        Set<String> nextVisited) {
        char[] charArray = word.toCharArray();
        for (int i = 0; i < word.length(); i++) {
            char originChar = charArray[i];
            for (char c = 'a'; c <= 'z'; c++) {
                if (originChar == c) {
                    continue;
                }
                charArray[i] = c;
                String nextWord = String.valueOf(charArray);
                if (wordSet.contains(nextWord)) {
                    if (endVisited.contains(nextWord)) {
                        return true;
                    }
                    if (!visited.contains(nextWord)) {
                        nextVisited.add(nextWord);
                        visited.add(nextWord);
                    }
                }
            }
            // 恢复，下次再用
            charArray[i] = originChar;
        }
        return false;
    }
}
```

