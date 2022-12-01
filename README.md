# max_depth_of_tree_py


````py
recursive solution: 
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if root is None:
            return 0
        return 1 + max(self.maxDepth(root.left), self.maxDepth(root.right))
                        
====================================with stack DFS: 

    # stack with tuple with height, while, pop and append if available sub tree and update 
    
    def maxDepth(self, root: Optional[TreeNode]) -> int: 
        
        # DFS with stack
        if not root: return 0
        
        ans = 1
        stack = [(root, 1)] # assuming root length  = 1
        while stack: 
            node, height  = stack.pop()   
            
            if node: 
                ans = max(ans, height)
                stack.append([node.left, height+1])
                stack.append([node.right, height+1]) 
                
        return ans
 
 ========================================with queue BFS
  # structure: queue, then while, then for to iterate neighbors, count level
  def maxDepth(self, root: Optional[TreeNode]) -> int: 
        
        # BFS with queue
        
        if not root: return 0
        q = deque([root]) # must use deque 
        level = 0
        while q: 
            for i in range(len(q)):
                node = q.popleft() # mus use popleft
                if node.left: 
                    q.append(node.left)
                if node.right: 
                    q.append(node.right)
            
            level += 1
        return level
 
 
````
