---
title: 'ţ����ϰ��34 c�� little w and Segment Coverage'
date: 2018-12-20 16:43:17
tags:
 - Java
 - �������
categories:
 - �������
---
���ӣ�https://ac.nowcoder.com/acm/contest/297/C
��Դ��ţ����


��Ŀ���� 
Сw��m���߶Σ����Ϊ1��m��

����Щ�߶θ��������ϵ�n���㣬���Ϊ1��n��

��i���߶θ��������ϵ�������L[i]��R[i]��

���ǵ�������ܻ����ص������Ҳ���֤m���߶�һ���ܸ�������n���㡣

����Сw��С�Ķ�ʧ��һ���߶Σ����ʶ�ʧ�����߶Σ�ʹ������û�����ǵ��ĵ�ĸ����������٣��������ʧ���߶εı�ź�û�����ǵ��ĵ�ĸ���������ж����߶η���Ҫ��������������߶εı�ţ����Ϊ1��m����

��������:
��һ�а�������������n��m(1��n��m��10^5)��
������m�У�ÿ�а�������������L[i]��R[i](1��L[i]��R[i]��n)��
�������:
���һ�У�������������a b��
a��ʾ��ʧ���߶εı�š�
b��ʾ��ʧ�˵�a���߶κ�û�����ǵ��ĵ�ĸ�����
ʾ��1
����

>5 3
1 3
4 5
3 4

���
>3 0

>˵��
����ʧ��1���߶Σ�1��2û���߶θ��ǵ���
����ʧ��2���߶Σ�5û���߶θ��ǵ���
����ʧ��3���߶Σ����е㶼���߶θ��ǵ��ˡ�

ʾ��2
����
>6 2
1 2
4 5

���
>2 4

>˵��
����ʧ��1���߶Σ�1��2��3��6û���߶θ��ǵ���
����ʧ��2���߶Σ�3��4��5��6û���߶θ��ǵ���

�����ò��������ж��룬�����߶θ��������Ȼ���¼û�б����ǵ��ĵط������ҳ�����ֵΪ1�������Ȼ���Դ˵ó��� 1-x �и���Ϊ 1 �ĸ��������ܵó������
>java AC����

```java
import java.util.Scanner;

public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int m = sc.nextInt();
		int[] data = new int[n+2];
		int[] l = new int[m], r = new int[m];
		for (int i = 0; i < m; i++) {
			l[i] = sc.nextInt();
			r[i] = sc.nextInt();
			data[l[i]]++;
			data[r[i] + 1]--;
		}
		int sum = data[0];
		int oth=0;
		for (int i = 1; i <= n; i++) {
			sum += data[i];
			if (sum == 1) {
				data[i] = 1;
			} else if (sum == 0) {
				oth++;
			} else {
				data[i] = 0;
			}
		}
		for (int i = 1; i <= n; i++) {
			data[i] += data[i - 1];
		}
		int a = 0, b = 1000000;
		for (int i = 0; i < m; i++) {
			int xi = data[r[i]] - data[l[i]-1];
			if (xi <= b) {
				a = i;
				b = xi;
			}
		}
		System.out.println((a + 1) + " " + (b+oth));
	}
}

```

