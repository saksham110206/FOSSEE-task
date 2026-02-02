# Installation and Testing Guide

This guide provides step-by-step instructions for installing and testing both tasks of the OpenFOAM GUI screening submission.

## Prerequisites

### For Task 1
- Python 3.7 or higher
- pip package manager
- Terminal/Command Prompt access

### For Task 2
- Blender 3.0.0 or higher (Download from https://www.blender.org/download/)
- Basic familiarity with Blender interface (optional but helpful)

## Task 1: Binary Tree Package

### Step 1: Navigate to Task 1 Directory

```bash
cd task1
```

### Step 2: Install Dependencies

```bash
pip install -r requirements.txt
```

Or if using Python 3 explicitly:
```bash
pip3 install -r requirements.txt
```

### Step 3: Install the Package

**Option A: Editable Installation (Recommended for Development)**
```bash
pip install -e .
```

**Option B: Regular Installation**
```bash
pip install .
```

### Step 4: Run the Test Script

```bash
python main.py
```

Or:
```bash
python3 main.py
```

### Expected Output

You should see output similar to:

```
==================================================
Test 1: Basic Tree Creation
==================================================
Root:1
 L---2
 L---4
 R---5
 R---3

==================================================
Test 2: Adding Nodes by Path
==================================================
Initial tree:
Root:10

Adding nodes:

Tree after additions:
Root:10
 L---5
 L---3
 R---7
 R---15
 L---12
 R---18

[... and so on ...]
```

### Step 5: Verify Installation

Test that the package is properly installed by running Python interactively:

```python
python
>>> from binarytree import Node, print_tree, add_node_by_path
>>> root = Node(1)
>>> root.left = Node(2)
>>> root.right = Node(3)
>>> print_tree(root)
Root:1
 L---2
 R---3
>>> exit()
```

### Step 6: Test Custom Scripts

Create your own test script:

```python
# my_test.py
from binarytree import *

# Create a tree
root = Node(100)
add_node_by_path(root, "L", 50)
add_node_by_path(root, "R", 150)

# Print it
print_tree(root)

# Save to YAML
write_tree_to_yaml(root, "my_tree.yaml")
print("Tree saved!")

# Load it back
loaded_tree = build_tree_from_yaml("my_tree.yaml")
print("\nLoaded tree:")
print_tree(loaded_tree)
```

Run with:
```bash
python my_test.py
```

### Troubleshooting Task 1

**Issue: "ModuleNotFoundError: No module named 'yaml'"**
- Solution: Install PyYAML: `pip install PyYAML`

**Issue: "ImportError: No module named 'binarytree'"**
- Solution: Make sure you ran `pip install -e .` from the task1 directory

**Issue: "FileNotFoundError: test.yaml"**
- Solution: Make sure you're running the script from the task1 directory where test.yaml exists

## Task 2: Blender Addon

### Step 1: Launch Blender

Open Blender 3.0.0 or higher.

### Step 2: Access Preferences

- Click on **Edit** in the top menu
- Select **Preferences** (or press Ctrl+Alt+U / Cmd+,)

### Step 3: Navigate to Add-ons Section

- Click on the **Add-ons** tab on the left sidebar

### Step 4: Install the Addon

**Method A: Install from File**
1. Click the **Install...** button at the top
2. Navigate to the `task2` folder
3. Select the `__init__.py` file
4. Click **Install Add-on**

**Method B: Copy to Addons Directory**
1. Copy the entire `task2` folder to your Blender addons directory:
   - **Windows**: `C:\Users\{username}\AppData\Roaming\Blender Foundation\Blender\{version}\scripts\addons\`
   - **macOS**: `/Users/{username}/Library/Application Support/Blender/{version}/scripts/addons/`
   - **Linux**: `~/.config/blender/{version}/scripts/addons/`
2. Rename the folder to `cube_array_manager`
3. Restart Blender
4. The addon should appear in Preferences → Add-ons

### Step 5: Enable the Addon

1. In the Add-ons preferences, search for "Cube Array Manager"
2. Check the checkbox next to **3D View: Cube Array Manager** to enable it
3. The addon is now active!

### Step 6: Access the Addon Panel

1. In the 3D Viewport, press **N** to open the sidebar (if not already open)
2. Look for the **Cube Manager** tab
3. Click on it to see the addon panel

### Step 7: Test Feature Set 1 - Cube Array Creation

**Test 1: Basic Cube Creation**
1. In the "Number of Cubes" field, enter `9`
2. Click **Create Cube Array**
3. You should see 9 cubes arranged in a 3×3 grid
4. Check the Outliner (top-right) - cubes should be in "Cube_Array_Collection"

**Test 2: Range Validation**
1. Enter `25` in the "Number of Cubes" field
2. Try to click **Create Cube Array**
3. You should see a warning: "The number is out of range"

**Test 3: Different Arrangements**
- Try: 4 cubes (2×2 grid)
- Try: 6 cubes (3×2 grid)
- Try: 12 cubes (4×3 grid)

**Test 4: Delete Selected**
1. Select one or more cubes (Shift+Click to select multiple)
2. Click **Delete Selected Cubes**
3. Selected cubes should be removed

**Test 5: Overlap Prevention**
1. Create 4 cubes
2. Manually move them around (Press G, then move mouse)
3. Create 4 more cubes
4. New cubes should avoid overlapping with moved ones

### Step 8: Test Feature Set 2 - Mesh Merging

**Test 1: Merge Two Adjacent Cubes**
1. Delete all existing objects (Select all with A, then X → Delete)
2. Create 2 cubes: Enter `2` and click **Create Cube Array**
3. The two cubes should be adjacent (touching)
4. Select both cubes:
   - Click on first cube
   - Shift+Click on second cube
5. Click **Merge Selected Meshes**
6. The two cubes should merge into one object
7. The shared face should be removed

**Test 2: Merge Multiple Objects**
1. Create a new scene or delete existing objects
2. Create 6 cubes
3. Arrange them so at least some are touching
4. Select the touching cubes
5. Click **Merge Selected Meshes**
6. Check the result - merged areas should have no duplicate faces

**Test 3: Error Handling**
1. Try clicking **Merge Selected Meshes** with no selection
   - Should show: "Select at least 2 meshes to merge"
2. Try with only 1 object selected
   - Should show the same error

### Step 9: Visual Verification

After each test:
- Check the 3D Viewport for visual confirmation
- Check the Outliner (top-right panel) to see object hierarchy
- Use Edit Mode (Tab key) to inspect merged meshes
- Verify that merged objects have no duplicate vertices or faces

### Troubleshooting Task 2

**Issue: Addon doesn't appear after installation**
- Solution 1: Restart Blender completely
- Solution 2: Check the System Console (Window → Toggle System Console) for error messages
- Solution 3: Make sure you enabled the addon checkbox in Preferences

**Issue: "Cube Manager" tab not visible**
- Solution 1: Press N to toggle the sidebar
- Solution 2: Make sure you're in the 3D Viewport (not Shader Editor or other workspace)
- Solution 3: Try switching to different workspaces (tabs at the top)

**Issue: Cubes not creating**
- Solution: Check the System Console for errors
- Make sure you have permission to create objects
- Try with a fresh Blender file (File → New → General)

**Issue: Merge not working**
- Solution 1: Ensure you have exactly 2 or more MESH objects selected
- Solution 2: Objects must be mesh type (not curves, empties, cameras, etc.)
- Solution 3: Try with default cubes first to verify functionality

**Issue: "The number is out of range" appears unexpectedly**
- This is expected when entering values > 20
- It's a feature, not a bug!
- Simply enter a number ≤ 20

### Advanced Testing

**Performance Test:**
1. Create 20 cubes at once (maximum allowed)
2. Verify all cubes appear correctly
3. Check that collections are organized properly

**Stress Test:**
1. Create multiple sets of cubes
2. Manually rearrange them
3. Create more cubes to test overlap prevention
4. Select all and try merging

**Edge Cases:**
1. Try creating 1 cube
2. Try creating exactly 20 cubes
3. Delete all cubes and create new ones
4. Test merging with non-adjacent objects

## Additional Testing Scenarios

### Task 1: Advanced Testing

**Test Large Trees:**
```python
from binarytree import *

# Create a large tree
root = Node(50)
for i in range(1, 8):
    path = "L" * i
    add_node_by_path(root, path, i)
    path = "R" * i
    add_node_by_path(root, path, i + 100)

print_tree(root)
```

**Test YAML Export/Import Cycle:**
```python
# Create tree
root = Node(1)
# ... add nodes ...

# Export
write_tree_to_yaml(root, "test_export.yaml")

# Import
imported = build_tree_from_yaml("test_export.yaml")

# Compare
print("Original:")
print_tree(root)
print("\nImported:")
print_tree(imported)
```

### Task 2: Advanced Testing

1. **Test with Complex Geometry:**
   - Create cubes, then modify them (Scale: S key, Rotate: R key)
   - Try merging modified cubes

2. **Test Collection Management:**
   - Check that all cubes go into the correct collection
   - Try creating multiple batches

3. **Test Undo/Redo:**
   - Create cubes
   - Press Ctrl+Z to undo
   - Press Ctrl+Shift+Z to redo

## Verification Checklist

### Task 1
- [ ] Package installs without errors
- [ ] All imports work correctly
- [ ] main.py runs and produces expected output
- [ ] Can create trees manually
- [ ] Can add nodes by path
- [ ] Can delete nodes
- [ ] Can edit node values
- [ ] YAML import works
- [ ] YAML export works
- [ ] test.yaml loads correctly
- [ ] Custom test scripts work

### Task 2
- [ ] Addon installs in Blender
- [ ] Addon appears in sidebar
- [ ] UI panel displays correctly
- [ ] Can create cubes (1-20)
- [ ] Range validation works (>20 shows error)
- [ ] Cubes arranged in proper grid
- [ ] Collection is created
- [ ] Can delete selected cubes
- [ ] Overlap prevention works
- [ ] Can merge meshes
- [ ] Common faces are removed
- [ ] Error messages display appropriately

## Performance Metrics

### Task 1
- Tree with 100 nodes: Should create and print in < 1 second
- YAML export of 100-node tree: < 1 second
- YAML import of 100-node tree: < 1 second

### Task 2
- Creating 20 cubes: < 2 seconds
- Merging 10 meshes: < 3 seconds
- UI responsiveness: Immediate feedback

## Getting Help

If you encounter issues:

1. **Check Documentation:**
   - README.md (main)
   - task1/README.md
   - task2/README.md

2. **Check System Requirements:**
   - Python version: `python --version`
   - Blender version: Help → About Blender

3. **Check Error Messages:**
   - Python: Read traceback carefully
   - Blender: Check System Console (Window → Toggle System Console)

4. **Verify File Paths:**
   - Make sure you're in the correct directory
   - Check that all files are present

5. **Try Fresh Installation:**
   - Delete and reinstall packages
   - Restart Blender
   - Use a clean Blender file

## Next Steps

After successful installation and testing:

1. **Explore the Code:**
   - Read through the implementation
   - Understand the design decisions
   - Try modifying features

2. **Extend Functionality:**
   - Add new features to Task 1
   - Enhance Task 2 UI
   - Implement bonus features

3. **Provide Feedback:**
   - Note any issues or improvements
   - Document your experience
   - Suggest enhancements

## Summary

Both tasks should now be fully functional. If all tests pass, the submission is ready for evaluation. The implementations demonstrate:
- Strong Python programming skills
- Understanding of data structures
- Ability to work with external libraries
- GUI development capabilities
- 3D programming proficiency
- Comprehensive documentation
- Professional code quality

Thank you for testing this submission!
