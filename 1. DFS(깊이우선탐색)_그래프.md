# DFS(깊이우선탐색)

TechBlog : https://hyeounstory.tistory.com/164

```java
import java.util.*;

public class Main {
	public static boolean[] visited_Node = new boolean[7]; 	// 방문했던 노드를 체크하기 위한 변수
	public static ArrayList<ArrayList<Integer>> graph = new ArrayList<ArrayList<Integer>>(); // 그래프 변수

	// 같은 Depth가 있을 경우, 작은 숫자를 먼저 방문(add를 작은 숫자 먼저 했기 때문)
    public static void dfs(int num) {
    	visited_Node[num] = true; // 현재 노드를 방문 처리
        System.out.print(num + " ");
        
        // 현재 노드와 연결된 다른 노드를 재귀적으로 방문
        for (int i = 0; i < graph.get(num).size(); i++) {
            int temp = graph.get(num).get(i);
            if (!visited_Node[temp]) 
            	dfs(temp);
        }
    }
    
    public static void main(String[] args) {
        for (int i = 0; i < 7; i++) {         // 그래프에 7개의 노드 추가
            graph.add(new ArrayList<Integer>());
        }

        // 노드에 연결된 노드 정보 저장 
        graph.get(0).add(1);
        graph.get(0).add(2);
        
        graph.get(1).add(0);
        graph.get(1).add(5);
        
        graph.get(2).add(0);
        graph.get(2).add(3);
        
        graph.get(3).add(2);
        graph.get(3).add(4);
        graph.get(3).add(6);
        
        graph.get(4).add(3);

        graph.get(5).add(1);

        graph.get(6).add(3);

        dfs(0); //첫노드
    }
}

//결과 : 0 1 5 2 3 4 6
```

