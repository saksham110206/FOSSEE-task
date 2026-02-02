# OpenFOAM GUI Internship - Screening Task Submission

This repository contains solutions for both screening tasks required for the CFD-FOSSEE OpenFOAM GUI internship.

## 📋 Contents

1. **Task 1**: Binary Tree Implementation with YAML Integration
2. **Task 2**: Blender Addon for Cube Array Management and Mesh Merging

## 🚀 Quick Start

### Task 1: Binary Tree Package

Navigate to the task1 directory and install:

```bash
cd task1
pip install -r requirements.txt
pip install -e .
python main.py
```

### Task 2: Blender Addon

1. Open Blender (3.0.0 or higher)
2. Go to Edit → Preferences → Add-ons
3. Click "Install..." and select `task2/__init__.py`
4. Enable "3D View: Cube Array Manager"
5. Open sidebar with `N` key and find "Cube Manager" tab

## 📁 Repository Structure

```
.
├── README.md                 # This file
├── task1/                    # Binary Tree Implementation
│   ├── binarytree/          # Package source code
│   │   ├── __init__.py
│   │   ├── node.py
│   │   └── tree_operations.py
│   ├── setup.py             # Package installation config
│   ├── requirements.txt     # Python dependencies
│   ├── main.py             # Test script
│   ├── test.yaml           # Sample YAML file
│   └── README.md           # Task 1 documentation
│
└── task2/                   # Blender Addon
    ├── __init__.py         # Addon main file
    └── README.md           # Task 2 documentation
```

## 📝 Task 1: Binary Tree Package

### Features Implemented

#### Feature Set 1: Core Binary Tree Operations ✓
- ✅ Node class for binary tree construction
- ✅ Create new binary trees
- ✅ Add nodes to existing trees (by path notation)
- ✅ Delete nodes from trees
- ✅ Delete entire trees
- ✅ Print entire tree or specific ranges
- ✅ Edit node values

#### Feature Set 2: YAML Integration ✓
- ✅ Parse YAML files to generate trees
- ✅ Write tree data to YAML files

#### Bonus Feature Set ✓
- ✅ Extended to support general trees (N-ary trees)
- ✅ Modified Node class to handle multiple children
- ✅ Updated all helper functions accordingly

### Installation

```bash
cd task1
pip install -r requirements.txt
pip install -e .
```

### Usage Example

```python
from binarytree import Node, print_tree, add_node_by_path

# Create root
root = Node(10)

# Add nodes by path
add_node_by_path(root, "L", 5)
add_node_by_path(root, "R", 15)
add_node_by_path(root, "LL", 3)

# Print tree
print_tree(root)

# Load from YAML
from binarytree import build_tree_from_yaml
tree = build_tree_from_yaml("test.yaml")
```

### Running Tests

```bash
cd task1
python main.py
```

Expected output matches the sample output provided in the task specification.

## 🎨 Task 2: Blender Addon

### Features Implemented

#### Feature Set 1: Cube Array Management ✓
- ✅ UI Panel with input box for N cubes (N < 20)
- ✅ Validation with popup for out-of-range numbers
- ✅ Smart 2D array distribution (m×n grid)
- ✅ Cubes are 1 Blender unit in size
- ✅ Separate collection for organized cubes
- ✅ Delete selected cubes button
- ✅ Overlap prevention algorithm

#### Feature Set 2: Mesh Merging ✓
- ✅ Merge selected meshes button
- ✅ Common face detection
- ✅ Vertex merging at boundaries
- ✅ Common face deletion

### Installation

1. Open Blender (3.0.0+)
2. Edit → Preferences → Add-ons
3. Click "Install..."
4. Navigate to `task2/__init__.py`
5. Click "Install Add-on"
6. Enable the checkbox for "3D View: Cube Array Manager"

### Usage

1. Press `N` to open sidebar
2. Click "Cube Manager" tab
3. Enter number of cubes (1-20)
4. Click "Create Cube Array"
5. Select meshes and click "Merge Selected Meshes"

## 🛠️ Technical Implementation

### Task 1 Highlights

**Object-Oriented Design**:
- Clean separation of concerns (Node class, tree operations)
- Type hints for better code documentation
- Comprehensive error handling

**YAML Integration**:
- Recursive tree building from nested dictionaries
- Symmetric serialization and deserialization
- Preserves tree structure perfectly

**Algorithms**:
- BST deletion with proper handling of all cases
- Post-order traversal for tree deletion
- Efficient path-based node insertion

### Task 2 Highlights

**Blender API Usage**:
- Proper operator registration and properties
- UI panel with custom layout
- Collection management for organization

**Smart Grid Algorithm**:
- Calculates optimal m×n dimensions: m = ⌈√N⌉, n = ⌈N/m⌉
- Creates most square-like arrangement
- Adaptive spacing and positioning

**Overlap Prevention**:
- Grid-based position tracking
- Collision detection with existing meshes
- Automatic position adjustment

**Mesh Merging**:
- BMesh operations for precise control
- Vertex deduplication by distance threshold
- Interior face cleanup

## 📦 Dependencies

### Task 1
- Python >= 3.7
- PyYAML >= 5.4.1

### Task 2
- Blender >= 3.0.0 (includes all required modules)

## ✅ Testing

### Task 1
The `main.py` script provides comprehensive testing:
1. Basic tree creation
2. Path-based node addition
3. YAML import/export
4. Node value editing
5. Tree range printing
6. Node deletion

Run with:
```bash
cd task1
python main.py
```

### Task 2
Manual testing in Blender:
1. Install and enable addon
2. Test cube array creation with various N values
3. Test validation (try N > 20)
4. Test overlap prevention
5. Test mesh merging with adjacent cubes
6. Test delete functionality

## 📖 Documentation

Each task includes detailed README files:
- `task1/README.md`: Complete API reference, examples, and usage guide
- `task2/README.md`: Installation guide, features, and troubleshooting

## 🎯 Code Quality

**Best Practices Followed**:
- ✅ Clear, readable code with meaningful variable names
- ✅ Comprehensive docstrings for all functions/classes
- ✅ Type hints for better IDE support
- ✅ Error handling and validation
- ✅ Modular design with separation of concerns
- ✅ Follows PEP 8 style guidelines

**Design Patterns**:
- Separation of concerns (data structures vs. operations)
- Factory pattern (tree building from YAML)
- Visitor pattern (tree traversal operations)

## 🎓 Learning Outcomes

Through this project, I demonstrated:
1. **Python Proficiency**: OOP, file I/O, package development
2. **Data Structures**: Binary trees, recursive algorithms
3. **API Integration**: YAML parsing and generation
4. **Blender Development**: Python API, UI panels, operators
5. **3D Mathematics**: Spatial positioning, mesh operations
6. **Software Engineering**: Documentation, testing, code quality

## 💡 Future Enhancements

### Task 1
- Add tree balancing algorithms (AVL, Red-Black)
- Implement tree visualization with matplotlib
- Add more tree traversal methods
- Support for additional formats (JSON, XML)

### Task 2
- Variable cube sizes and shapes
- Custom spacing controls
- More sophisticated merge algorithms
- Batch operations on multiple collections
- Advanced overlap resolution strategies

## 📧 Submission Details

**Submitted by**: [Your Name]
**Email**: [Your Email]
**Date**: [Current Date]

## 📄 License

MIT License - Feel free to use and modify as needed.

## 🙏 Acknowledgments

Thank you to the CFD-FOSSEE team for this comprehensive and educational screening task. It provided an excellent opportunity to demonstrate both theoretical knowledge and practical implementation skills across different domains (data structures, GUI development, and 3D programming).

---

**Note**: This submission represents original work completed independently. All code has been tested and documented to professional standards.
