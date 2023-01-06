# BFS(너비우선탐색)

TechBlog : https://hyeounstory.tistory.com/164

```java
import java.util.ArrayList;
import java.util.LinkedList;
import java.util.Queue;

public class Main {
	public static boolean[] visited_Node = new boolean[7]; 	// 방문했던 노드를 체크하기 위한 변수
	public static ArrayList<ArrayList<Integer>> graph = new ArrayList<ArrayList<Integer>>();// 그래프 변수
	public static ArrayList<Integer> result = new ArrayList<Integer>();

	// 가까이 있는 원소부터 탐색
    public static void bfs(int num) {
    	Queue<Integer> q = new LinkedList<>();
    	
        q.offer(num);
    	visited_Node[num] = true; // 1.현재 노드를 방문 처리
        
    	while(!q.isEmpty()) {
            int now = q.poll();  // queue에서 하나의 원소를 뽑음, 선입선출이기에 먼저 들어온 것이 먼저 뽑힘
            
            result.add(now); // 결과저장
            
            // 해당 원소와 연결되어 있는 원소 확인
            for(int i = 0; i < graph.get(now).size(); i++) {
                int temp = graph.get(now).get(i);
                
                if(!visited_Node[temp]) { // 아직 방문처리가 안 된 원소는 queue에 넣고 방문 처리
                	q.offer(temp);
                	visited_Node[temp] = true; // 2.방문 처리
                }
            }
        }
        
        for(int i=0; i< result.size(); i++) {
            System.out.println(result.get(i));
        }
    }
    
	public static void main(String[] args) {
        for (int i = 0; i < 7; i++) { // 그래프에 7개의 노드 추가
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
        
        bfs(0);
	}
}
//결과 : 0 1 2 5 3 4 6
```
