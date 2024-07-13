class TreeNode:
    def __init__(self, data):
        self.data = data
        self.children = []

    def add_child(self, child):
        self.children.append(child)

def build_laptop_tree():
    # Membangun struktur tree yang merepresentasikan informasi laptop
    root = TreeNode({"RAM": "8GB", "Brand": "Dell", "Speed": "2.4GHz", "Depth": "15 inches", "Memory": "256GB"})
    node1 = TreeNode({"RAM": "16GB", "Brand": "HP", "Speed": "3.0GHz", "Depth": "14 inches", "Memory": "512GB"})
    node2 = TreeNode({"RAM": "32GB", "Brand": "Lenovo", "Speed": "3.2GHz", "Depth": "16 inches", "Memory": "1TB"})

    root.add_child(node1)
    root.add_child(node2)

    return root

def dfs_search(node, attribute):
    stack = [node]
    found_values = []
    while stack:
        current = stack.pop()
        if attribute in current.data:
            found_values.append(current.data[attribute])
        stack.extend(current.children)
    return found_values

# Main program
if __name__ == "__main__":
    laptop_tree = build_laptop_tree()

    # Pencarian menggunakan DFS
    print("Hasil pencarian:")
    print(f"RAM: {dfs_search(laptop_tree, 'RAM')}")
    print(f"Brand: {dfs_search(laptop_tree, 'Brand')}")
    print(f"Speed: {dfs_search(laptop_tree, 'Speed')}")
    print(f"Depth: {dfs_search(laptop_tree, 'Depth')}")
    print(f"Memory: {dfs_search(laptop_tree, 'Memory')}")
