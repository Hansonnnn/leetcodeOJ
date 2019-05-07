## BST
因为96题的原因，就使用C++版本重新实现了一下BST树。首先介绍一下BST树。

二叉查找树（BST：Binary Search Tree）是一种特殊的二叉树，它改善了二叉树结点查找的效率。二叉查找树有以下性质：

对于任意一个节点 n，

- 其左子树（left subtree）下的每个后代结点（descendant node）的值都小于结点 n 的值；
- 其右子树（right subtree）下的每个后代结点的值都大于结点 n 的值。
- 所谓结点 n 的子树，可以将其看作是以节点 n 为根结点的树。子树的所有结点都是结点 n 的后代，而子树的根则是结点 n 本身。

**BST树插入**

向BST树插入一个新结点n时，该结点总是作为叶子结点。所以需要去寻找该结点的父结点。现将遍历的当前结点记为c，要插入的新结点记为n，所以在遍历开始时c即作为BST树的根结点。
```
1. 如果结点c为空，则将结点c的父节点作为结点n的父节点。如果结点 n 的值小于该父结点的值，则结点 n 将作为该父节点的左孩子；否则结点 n 将作为该父结点的右孩子。

2. 比较结点c与结点n的值。

3. 如果结点n的值大于结点c的值，则结点必在结点c的右子树中。将父结点设置为结点c，并将结点n设置为结点c的右孩子。返回1

4. 如果结点n的值小于结点c的值，则结点n必在结点c的左子树中，将父节点设置为结点c，并将结点n设置为结点c的左孩子。返回1

5. 如果结点n的值等于结点c。则为插入重复值，需剔除重复值或抛出异常。
```

## Code
```C++
//
// Created by hansonnnnn on 2019/5/5.
//
#include <iostream>
#include <vector>
#include <string>

using namespace std;


class TreeNode {
public:
    int key;
    TreeNode *left;//指向左结点
    TreeNode *right;//指向右结点
    TreeNode *p;//指向父节点
public:
    TreeNode();
    TreeNode(int val);
};

TreeNode::TreeNode() {
    key = 0;
    left = right = p = NULL;
}

TreeNode::TreeNode(int val) {
    key = val;
    left = right = p = NULL;
}

void tree_insert(TreeNode *T, TreeNode *z) {
    TreeNode *y, *x = T;
    //将根结点指针移到叶结点的根结点上
    while (x) {
        y = x;//哨兵
        if (z->key < x->key) {
            x = x->left;
        } else {
            x = x->right;
        }
    }
    //将插入元素的父指针元素指向叶结点的根结点上
    z->p = y;
    if (!y) {
        T = z;//即树为空，则将插入元素赋为根节点
    } else if (z->key < y->key) {
        y->left = z;
    } else {
        y->right = z;
    }

}



/**
 * 递归中序遍历BST树
 * @param x
 */
void inorder_tree_walk(TreeNode *x) {
    if (x != NULL) {
        inorder_tree_walk(x->left);
        cout << x->key << " ";
        inorder_tree_walk(x->right);
    } else {
        return;
    }
}

bool search_in_tree(TreeNode *T, int n) {
    TreeNode *x = T;
    if (x == NULL) {
        return false;
    }
    while (x) {
        if (x->key > n) {
            x = x->left;
        } else if (x->key < n) {
            x = x->right;

        } else {
            return true;
        }
    }
    return false;
}

int main() {
    TreeNode *T = new TreeNode(15);
    int a[10] = {6, 18, 3, 7, 17, 20, 2, 4, 13, 9};
    for (int i = 0; i < 10; i++) {
        TreeNode *z = new TreeNode(a[i]);
        tree_insert(T, z);
    }
    inorder_tree_walk(T);
    cout<<endl;
    cout<<"search result:"<<to_string(search_in_tree(T,18));

}
