```python
class TrieNode:
# Initialize your data structure here.
def __init__(self):
    self.children = collections.defaultdict(TrieNode)
    self.is_word = False

class Trie:

    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        current = self.root
        for letter in word:
            current = current.children[letter]
        current.is_word = True

    def search(self, word):
        current = self.root
        for letter in word:
            current = current.children.get(letter)
            if current is None:
                return False
        return current.is_word

    def startsWith(self, prefix):
        current = self.root
        for letter in prefix:
            current = current.children.get(letter)
            if current is None:
                return False
        return True

```
```java
class TrieNode {
    Map<Character, TrieNode> children = new HashMap<>();
    boolean isWord = false;
    String word = null;
    
    public void setChildren(Character ch) {
        children.put(ch, new TrieNode());
    }
    
    public TrieNode getChildren(Character ch) {
        if (children.containsKey(ch))
        return children.get(ch);
        else
            return null;
    }
    
    public void setIsWord(String w){
        isWord = true;
        word = w;
    }
    
    public boolean getIsWord() {
        return isWord;
    }
         
}


class Trie {
    public TrieNode root;
    /** Initialize your data structure here. */
    public Trie() {
        root = new TrieNode();
    }
    
    /** Inserts a word into the trie. */
    public void insert(String word) {
        var node = root;
        for (char ch: word.toCharArray()) {
            if (node.getChildren(ch) == null) {
                node.setChildren(ch);
            }
            node = node.getChildren(ch) ;
            // node.setChildren(ch);
            // node = node.getChildren(ch);
        }
        node.setIsWord(word);
    }
    
    /** Returns if the word is in the trie. */
    public boolean search(String word) {
        var node = root;
        for (char ch: word.toCharArray()) {
            node = node.getChildren(ch);
            if (node == null) {
                return false;
            }
        }
        return node.getIsWord();
    }
    
    /** Returns if there is any word in the trie that starts with the given prefix. */
    public boolean startsWith(String prefix) {
        var node = root;
        for (char ch: prefix.toCharArray()) {
            node = node.getChildren(ch);
            if (node == null) {
                return false;
            }
        }
        return true;
    }
}
```

```c++
class TrieNode
{
public:
    TrieNode *next[26];
    bool is_word;
    
    // Initialize your data structure here.
    TrieNode(bool b = false)
    {
        memset(next, 0, sizeof(next));
        is_word = b;
    }
};

class Trie
{
    TrieNode *root;
public:
    Trie()
    {
        root = new TrieNode();
    }

    // Inserts a word into the trie.
    void insert(string s)
    {
        TrieNode *p = root;
        for(int i = 0; i < s.size(); ++ i)
        {
            if(p -> next[s[i] - 'a'] == NULL)
                p -> next[s[i] - 'a'] = new TrieNode();
            p = p -> next[s[i] - 'a'];
        }
        p -> is_word = true;
    }

    // Returns if the word is in the trie.
    bool search(string key)
    {
        TrieNode *p = find(key);
        return p != NULL && p -> is_word;
    }

    // Returns if there is any word in the trie
    // that starts with the given prefix.
    bool startsWith(string prefix)
    {
        return find(prefix) != NULL;
    }

private:
    TrieNode* find(string key)
    {
        TrieNode *p = root;
        for(int i = 0; i < key.size() && p != NULL; ++ i)
            p = p -> next[key[i] - 'a'];
        return p;
    }
};

```
