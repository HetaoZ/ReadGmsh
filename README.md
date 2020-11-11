# ReadGmsh

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://HetaoZ.github.io/ReadGmsh.jl/stable)
[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://HetaoZ.github.io/ReadGmsh.jl/dev)
[![Build Status](https://github.com/HetaoZ/ReadGmsh.jl/workflows/CI/badge.svg)](https://github.com/HetaoZ/ReadGmsh.jl/actions)
[![Coverage](https://codecov.io/gh/HetaoZ/ReadGmsh.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/HetaoZ/ReadGmsh.jl)

Read `msh` formatted file generated by Gmsh, and return information of nodes and elements of the selected type `elemtype`. The parameter `elemtype` is an integer representing a Gmsh element type, for example,

1

    2-node line. 
2

    3-node triangle. 
3

    4-node quadrangle. 
4

    4-node tetrahedron. 
5

    8-node hexahedron. 

More element types can be found in Gmsh [documentation](https://gmsh.info/doc/texinfo/gmsh.html) (Section 9.1).

# Install
```julia
] add Gmsh
] add ReadGmsh 
```

# Usage

```julia
using ReadGmsh

# get information of nodes
nodeTags, nodeCoords = get_nodes("examples/rect2d.msh")

# get information of elements of Gmsh element type 1 and 2 respectively
elemTags_1, elemNodeTags_1 = get_elems("examples/rect2d.msh", 1) # elemtype = 1
elemTags_2, elemNodeTags_2 = get_elems("examples/rect2d.msh", 2) # elemtype = 2

# get both information of nodes and elements
nodeTags, nodeCoords, elemTags_2, elemNodeTags_2 = get_nodes_elems("examples/rect2d.msh", 2)

# get information of boundary elements
elemtype = 2
boundary_element_dimension = 2
boundElemTags, boundElemNodeTags = get_bounds("examples/rect2d.msh", elemtype, boundary_element_dimension)

# get information of nodes, elements, and boundary elements
nodeTags, nodeCoords, elemTags_2, elemNodeTags_2, boundElemTags, boundElemNodeTags = get_nodes_elems_bounds("examples/rect2d.msh", 2, 2)
```
![image](https://github.com/HetaoZ/ReadGmsh/blob/main/examples/rect2d.png)