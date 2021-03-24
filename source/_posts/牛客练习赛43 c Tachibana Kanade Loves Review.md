---
title: 'ţ����ϰ��43 c�� Tachibana Kanade Loves Review'
date: 2019-04-07 21:45:17
tags:
 - Java
 - �������
categories:
 - �������
---
[��Ŀ����](https://ac.nowcoder.com/acm/contest/548/C)


#### ��Ŀ���� 
��������һ���ոտ�ʼѧϰ OI �����¡�
�����ʵ��ǿ��� Qingyu ��ѡ�� IODS 9102 �ĳ����ˡ�������֪�� IODS ��һ�����䶾���ı�����Ϊ������α�����ȡ�úõĳɼ������������ѧϰ���ܿ�����ÿһ��֪ʶ�㡣
�� Qingyu �Ĳ����У��������֪�ⳡ�����ܹ��ῼ��ѡ�� n ��֪ʶ�㡣��ǰ���������Ѿ�������ѧѧϰ������ k ��֪ʶ�㡣����������������Ҫѧϰ������֪ʶ�㣬ÿѧϰһ��������֪ʶ�㣬��Ҫ���ĵ�ʱ��Ϊ Ti �졣ͬʱ��ĳЩ֪ʶ��֮�������ϵ�����Լ���ѧϰ�Ĺ��̡��������㣬������һ������������ m ����ϵ���� i ����ϵ���Ա�ʾΪ(Xi,Yi,Hi)���京��Ϊ���������˵� Xi ��֪ʶ��͵� Yi ��֪ʶ��������һ����ѧϰ Hi �켴��������һ��֪ʶ�㡱��
�����������ʱ����ʣ�޼���ֻ�� t �죬��ˣ�����֪���Լ��ܲ������� t ����ѧϰ������е�֪ʶ�㡣
#### ��������:
�����������ϴ���ע��ʹ��Ч�ʽϸߵĶ��뷽ʽ
����ĵ�һ�а����ĸ����� n, m, k, t���������������
������һ�У����� n �����������α�ʾ T1,T2,?,Tn
������һ�У����� k ����������ʾ�������Ѿ�ѧϰ����֪ʶ�㡣��� k=0����˴�Ϊһ���С�
������ m �У�ÿ�� 3 ������ Xi,Yi,Hi������һ����ϵ��
#### �������:
����������ܹ�ѧϰ�����е�֪ʶ�㣬���һ�� Yes��������� No

#### ʾ��1
#### ����
>4 3 2 5
4 5 6 7
2 3
1 2 3
1 3 2
3 4 2
#### ���
>Yes
##### ˵��
>�������Ѿ�ѧϰ���˵� 2, 3 ��֪ʶ���ɵ� 2 ����ϵ����������Ի� 2 ��ѧ��֪ʶ�� 1�����ɹ�ϵ 3�� ��������� 2 ��ѧ��֪ʶ�� 4������ܹ���Ҫ���� 4 �죬�����������
#### ʾ��2
#### ����
>5 4 0 12
4 5 6 7 1
&nbsp;
1 2 3
1 3 2
3 4 2
1 5 233
#### ���
>Yes
#### ˵��
>������Ƚϲˣ����ʲô��û��ѧ����������ѡ���Ȼ� 4 ���ʱ��ѧ��֪ʶ�� 1��Ȼ����ݹ�ϵ 1, 2���ֱ� 3, 2 ���ʱ��ѧ��֪ʶ�� 2, 3���ٸ��ݹ�ϵ 3���� 2 ���ʱ��ѧ��֪ʶ�� 4��Ȼ�����ٵ���ѧϰ֪ʶ�� 5������1�죬�ܹ������� 12 �� �������������
��ע�⣬��Ȼ��ϵ 4 ������������֪ʶ�� 1 �Ļ�����ѧϰ֪ʶ�� 5������Ҫ��ʱ��ȵ���ѧϰ��Ҫ�࣬��������಻����֪ʶ�� 1 �Ļ�����ѧϰ֪ʶ�� 5.
#### ��ע:
>0?k?n?1e6,m?5e6,t?1e18,Ti,Hi?1e3

����ת��Ϊ��С���������⡣

java��ʱû�ܹ������������Ƕ����е����ɡ�����
Ŀǰ�������ܰѳ���������С���ˡ�����

```java
import java.io.BufferedInputStream;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.StreamTokenizer;
import java.math.BigDecimal;
import java.util.ArrayList;
import java.util.PriorityQueue;
import java.util.Scanner;

public class Main {

	static StreamTokenizer st = new StreamTokenizer(new BufferedInputStream(System.in));

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = nextNum();
		int m = nextNum();
		int k = nextNum();
		long t = nextNum();
		int T[] = new int[n + 1];
		PriorityQueue<Node> pq = new PriorityQueue<>();
		for (int i = 1; i <= n; i++) {
			T[i] = nextNum();
			pq.add(new Node(0, i, T[i], 0));
		}
		boolean has[] = new boolean[n + 1];
		boolean use[] = new boolean[m + 1];
		has[0] = true;
		int K[] = new int[k];
		for (int i = 0; i < k; i++) {
			K[i] = nextNum();
			has[K[i]] = true;
		}

		ArrayList<ArrayList<Node>> al = new ArrayList<>();
		for (int i = 0; i <= n; i++) {
			al.add(new ArrayList<>());
		}
		int flag = k;
		for (int i = 1; i <= m; i++) {
			Node node = new Node(nextNum(), nextNum(), nextNum(), i);
			al.get(node.x).add(node);
			al.get(node.y).add(node);
		}

		for (int i = 0; i < k; i++) {
			for (Node node : al.get(K[i])) {
				if (!use[node.id]) {
					pq.add(node);
					use[node.id] = true;
				}
			}
		}

		long ans = 0;
		while (!pq.isEmpty()) {
			Node te = pq.poll();
			if (has[te.x] && has[te.y]) {
				continue;
			} else if (has[te.x]) {
				flag++;
				ans += te.h;
				has[te.y] = true;
				for (Node node : al.get(te.y)) {
					if ((has[node.x] && has[node.y]) || use[node.id]) {
						continue;
					} else {
						pq.add(node);
						if(node.id!=0) {
							use[node.id] = true;
						}
					}
				}
			} else {
				flag++;
				ans += te.h;
				has[te.x] = true;
				for (Node node : al.get(te.x)) {
					if ((has[node.x] && has[node.y]) || use[node.id]) {
						continue;
					} else {
						pq.add(node);
						if(node.id!=0) {
							use[node.id] = true;
						}
					}
				}
			}
			if (flag >= n) {
				break;
			}
			if (ans > t) {
				System.out.println("No");
				return;
			}
		}
		System.out.println("Yes");
		return;
	}
	private static int nextNum() {
		try {
			st.nextToken();
		} catch (IOException e) {
			e.printStackTrace();
		}
		return (int) st.nval;

	}
}

class Node implements Comparable<Node> {
	int x;
	int y;
	int h;
	int id;

	public Node(int x, int y, int h, int id) {
		super();
		this.x = x;
		this.y = y;
		this.h = h;
		this.id = id;
	}

	@Override
	public String toString() {
		return "Node [x=" + x + ", y=" + y + ", h=" + h + "]";
	}

	@Override
	public int compareTo(Node o) {

		return h - o.h;
	}

}
```

