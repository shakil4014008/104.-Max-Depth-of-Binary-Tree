# max_depth_of_tree_py


````py
recursive solution: 
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if root is None:
            return 0
        return 1 + max(self.maxDepth(root.left), self.maxDepth(root.right))
                        
====================================with BFS 

      def maxDepth(self, root: Optional[TreeNode]) -> int: 
        
        if not root: return 0         
        ans = 0
        q = [(root, 1)] # assuming root length  = 1
        while q: 
            node, d  = q.pop(0)  # d is the depth ; pop could be O(n)          
           
            ans = max(ans, d)
            
            if node.left:  # must be node not root
                q.append((node.left, d+1))
            if node.right: 
                q.append((node.right, d+1))
        return ans
 
 ========================================with dequeu
      def maxDepth(self, root: Optional[TreeNode]) -> int: 
        
        if not root: return 0         
        ans = 0
        q = deque([(root, 1)]) # assuming root length  = 1
        while q: 
            node, d  = q.popleft()  # d is the depth  ; pop is O(1)        
           
            ans = max(ans, d)
            
            if node.left:  # must be node not root
                q.append((node.left, d+1))
            if node.right: 
                q.append((node.right, d+1))
        return ans
 
 
````
