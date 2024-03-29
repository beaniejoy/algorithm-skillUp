# BFS, DFS

- BFS
  - 너비 우선 탐색
  - Breath First Search
- DFS
  - 깊이 우선 탐색
  - Depth First Search

## DFS 구현

### Recursive 방법

```java
public class DFS {
  private boolean[] visited;
  // Graph 게시글 참고
  private Graph.Node[] adjList;

  public DFS(Graph graph, int maxVertices) {
    visited = new boolean[maxVertices];
    adjList = graph.getAdjList();
  }

  public void dfsRecursive(int v) {
    
    if(visited[v])
      return;
    // 방문 체크
    visited[v] = true;
    // 방문한 Vertex 출력
    System.out.println(String.valueOf(v));
    // 인접리스트 조회
    Graph.Node next = adjList[v].getNext();
    while(next != null) {
      if(!visited[next.getVertex()])
        dfsRecursive(next.getVertex());
      
      next = next.getNext();
    }
  }
}
```

### Iterative 방법

```java
public void dfsIterative(int v) {
  
  stack.push(v);
  
  while(!stack.isEmpty()) {
    v = stack.pop();
    
    if(visited[v])
      continue;
    
    visited[v] = true;
    
    System.out.println(String.valueOf(v));
    
    Graph.Node next = adjList[v].getNext();
    while(next != null) {
      if(!visited[next.getVertex()])
        stack.push(next.getVertex());
      
      next = next.getNext();
    }
  }
}
```

## BFS 구현

```java
public void bfs(int v) {
  // Queue 사용
  queue.add(v);

  while(!queue.isEmpty()) {
    v = queue.poll();
    
    if(visited[v])
      continue;
    
    visited[v] = true;
    
    System.out.println(v);
    
    Graph.Node next = adjList[v].getNext();
    while(next != null) {
      if(!visited[next.getVertex()])
        queue.add(next.getVertex());
      
      next = next.getNext();
    }
  }
}
```
