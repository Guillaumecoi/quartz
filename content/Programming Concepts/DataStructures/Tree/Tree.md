# Tree
---

![[Pasted image 20240122160402.png#50%#center]]
## Abstract Data Type
---
**Position p**: `p.getElement()`: Returns the element stored at this position.

**Accessor methods:**
- `root()`: Returns `p` of the root (null if empty)
- `parent(p)`: Returns parent of `p` (`p` isRoot -> null).
- `children(p)`: Returns an iterable collection of `p`'s children.
- `numChildren(p)`: Number of children of `p`.

**Simplifying Tree Programming**:
- `isInternal(p)`: True if `p` has at least one child.
- `isExternal(p)`: True if `p` has no children.
- `isRoot(p)`: True if `p` is the root.

**General Methods**:
- `size()`
- `isEmpty()
- `iterator()`: Iterates over all elements.
- `positions()`: Returns an iterable collection of all positions.

### Ordered Tree

if there is a meaningful linear order among the children of each node.
![[Pasted image 20240122160705.png#75%#center]]

### Implementation
---
- [[Programming Languages/Java/Data Structures/Tree|Java]]

### Related Topics:
---
- 