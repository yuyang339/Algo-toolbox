
```c++
// record parent node for each node in a binary tree
        std::stack<TreeNode*> sk;
        std::unordered_map<TreeNode*, TreeNode*> parent;
        sk.push(root);
        parent[root] = NULL;
        while (!sk.empty()) {
            auto node = sk.top();
            sk.pop();
            if(node->left){
                sk.push(node->left);
                parent[node->left] = node;
            }
            if(node->right){
                sk.push(node->right);
                parent[node->right] = node;
            }
        }
        
```
