For general info see: [[Programming Concepts/DataStructures/Tree/Tree|Tree]]

---
## Java

### As an Interface
```java
public interface Tree<E> extends Iterable<E> {
	Position<E> root();
	Position<E> parent(Position<E> p) throws IllegalArgumentException;
	Iterable<Position<E>> children(Position<E> p) throws IllegalArgumentException;
	
	int numChildren(Position<E> p) throws IllegalArgumentException;
	
	boolean isInternal(Position<E> p) throws IllegalArgumentException;
	
	boolean isExternal(Position<E> p) throws IllegalArgumentException;
	
	boolean isRoot(Position<E> p) throws IllegalArgumentException;
	
	int size();
	boolean isEmpty();
	Iterator<E> iterator();
	Iterable<Position<E>> positions();
}
```

### As an abstract class

```java
public abstract class AbstractTree<E> implements Tree<E> {

  public boolean isInternal(Position<E> p) { return numChildren(p) > 0; }

  public boolean isExternal(Position<E> p) { return numChildren(p) == 0; }

  public boolean isRoot(Position<E> p) { return p == root(); }

  public int numChildren(Position<E> p) {
    int count=0;
    for (Position child : children(p)) count++;
    return count;
  }

  public int size() {
    int count=0;
    for (Position p : positions()) count++;
    return count;
  }

  public boolean isEmpty() { return size() == 0; }
  ...
}
```

#### Height and debt
```java
  // computing depth of nodes and height of (sub)trees

  public int depth(Position<E> p) throws IllegalArgumentException {
    if (isRoot(p))
      return 0;
    else
      return 1 + depth(parent(p));
  }

  public int height(Position<E> p) throws IllegalArgumentException {
    int h = 0;                          // base case if p is external
    for (Position<E> c : children(p))
      h = Math.max(h, 1 + height(c));
    return h;
  }
  ```

#### Iterations
##### Nested ElementIterator class
```java
private class ElementIterator implements Iterator<E> {
	Iterator<Position<E>> posIterator = positions().iterator();
	public boolean hasNext() { return posIterator.hasNext(); }
	public E next() { return posIterator.next().getElement(); } 
	public void remove() { posIterator.remove(); }
}
```
##### Implementation
```java
  public Iterator<E> iterator() { return new ElementIterator(); }
  public Iterable<Position<E>> positions() { return preorder(); }
  private void preorderSubtree(Position<E> p, List<Position<E>> snapshot) {
    snapshot.add(p);                       
    for (Position<E> c : children(p))
      preorderSubtree(c, snapshot);
  }

  public Iterable<Position<E>> preorder() {
    List<Position<E>> snapshot = new ArrayList<>();
    if (!isEmpty())
      preorderSubtree(root(), snapshot);   // fill the snapshot recursively
    return snapshot;
  }

  private void postorderSubtree(Position<E> p, List<Position<E>> snapshot) {
    for (Position<E> c : children(p))
      postorderSubtree(c, snapshot);
    snapshot.add(p);                       // for postorder, we add position p after exploring subtrees
  }

  public Iterable<Position<E>> postorder() {
    List<Position<E>> snapshot = new ArrayList<>();
    if (!isEmpty())
      postorderSubtree(root(), snapshot);   // fill the snapshot recursively
    return snapshot;
  }

  public Iterable<Position<E>> breadthfirst() {
    List<Position<E>> snapshot = new ArrayList<>();
    if (!isEmpty()) {
      Queue<Position<E>> fringe = new LinkedQueue<>();
      fringe.enqueue(root());                 // start with the root
      while (!fringe.isEmpty()) {
        Position<E> p = fringe.dequeue();     // remove from front of the queue
        snapshot.add(p);                      // report this position
        for (Position<E> c : children(p))
          fringe.enqueue(c);                  // add children to back of queue
      }
    }
    return snapshot;
  }
}
```