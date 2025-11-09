# 25125047_W04
#include <math.h>
#include <iostream>
using namespace std;
int n, r, cl, r2, cl2, a[100], b[100];
float tm[100], c[100][100], d[100][100], sum[100][100];




//Sum
float Sum10(int z, int t) {
	float s = 0;
	for (int e = 0; e < r; ++e)
		s += c[z][e] * d[e][t];
	return s;
}
 
//Input 
void In1() {
	cout << "Input n: "; cin >> n;
	for (int i = 0; i < n; i++) 
		cin >> a[i];
}
//Output
void Out() {
	for (int r = 0; r < n; r++) 
		if (a[r] != 0)
		cout << a[r] << " ";
}

//Output 2
void Out2(int n) {
	cout << n << " ";
}

//In 2D
void In2d() {
	cout << "Input numbers of rows and columns:";
	cin >> r >> cl;
	for (int i = 0; i < r; i++)
		for (int j = 0; j < cl; j++)
			cin >> c[i][j];
}

//Out 2d
void Out2d() {

	for (int i = 0; i < r; i++)
	{
		for (int j = 0; j < cl; j++)
		{
			cout << c[i][j] << " ";
		}
		cout << endl;
	}
}




//Prime 1
bool Pr(int n) {
	if (n < 2) return false;
	for (int i = 2; i <= sqrt(n); i++)
		if (n % i == 0) return false;
	return true;
}

//Check
bool Check6(float h) {
	
	for (int cc = 0; cc < cl; cc++)
		if (c[r][cc] > h) return false;
	for (int cc = 0; cc < r; cc++)
		if (c[cc][cl] < h) return false;
	return true;
}


//Bai 1
void Bai1(int size, int* arr) {
	for (int i = 0; i < size; i++)
		if (Pr(a[i])) arr[i] = 0;
}

//Bai 2
void Bai2() {
	int k, i, n;
	cout << "Input n, i, k; "; cin >> n >> i >> k;

	for (int j = 0; j < n; j++)
		cin >> a[j];
	for (int j = i; j < (i + k); j++)
		a[j] = 0;
	for (int r = 0; r < n; r++)
		if (a[r] != 0)
			cout << a[r] << " ";
}

//Bai3
void Bai3() {
	int max =INT_MIN, max2;
	for (int i = 0; i < n; i++)
		if (a[i] >= max) {
			max2 = max;
			max = a[i];
		}
	if (max != max2) cout << max2;
	else cout << "No second largest number!";
}

//Bai4
void Bai4() {
	int x, y;
	cout << "input a, b"; cin >> x >> y;
	for (int i = 0; i < x; i++) cin >> a[i];
	for (int i = 0; i < y; i++) cin >> b[i];
	for (int i = 0; i < x; i++)
		for (int j = 0; j < y; j++)
			if (a[i] == b[j]) Out2(a[i]);
}

//Bai5
void Bai5() {
	for (int i = 0; i < r; i++)
	{
		float sum = 0;
		for (int j = 0; j < cl; j++)
			sum += c[i][j];
		Out2(sum);
		cout << endl;
	}

}

//Bai6
void Bai6() {
	
	int count = 0;
	for (int i =0; i <r; i++)
		for (int j=0; j<cl;j++)
			if (Check6(c[i][j])) count++;
	Out2(count);
}

//Bai7
void Bai7() {
	float temp = c[0][0];
	for (int i = 0; i < r - 1; ++i) {
		c[i][0] = c[i + 1][0];
	}
	for (int j = 0; j < cl - 1; ++j) {
		c[r - 1][j] = c[r - 1][j + 1];
	}
	for (int i = r - 1; i > 0; --i) {
		c[i][cl - 1] = c[i - 1][cl - 1];
	}
	for (int j = cl - 1; j > 1; --j) {
		c[0][j] = c[0][j - 1];
	}
	c[0][1] = temp;
}

//Bai9
void Bai9() {
	int ct = 0;
	if (r != cl) cout << "Invalid input!";
	else
	{
		for (int i = 0; i < r; i++)
			for (int j = 0; j < cl; j++)
				if (c[i][j] != c[j][i])
					ct++;
		if (ct != 0) cout << "No"; else cout << "Yes";
	}
}

//Bai 10
void Bai10() {
	for (int i = 0; i < r; i++)
		for (int j = 0; j < cl; j++)
		{
			for (int k = 0; k < r; k++)
			sum[i][j] = c[i][k] * d[k][j];
		}
}

//Bai 8
void Bai8() {
	int count = 0, i = 0, j = 0, k = r, l = cl;
	while (count < r * cl)
	{
		while (j < l - 1)
		{
			
			c[i][j] = a[count];
			j++;
			count++;
		}
		while (i < k - 1)
		{
			
			c[i][j] = a[count];
			i++;
			count++;
		}
		while (j > cl-l)
		{
			
			c[i][j] = a[count];
			j--;
			count++;
		}
		while (i > r - k)
		{
			
			c[i][j] = a[count];
			i--;
			count++;
		}
		k++; l++;
	}
}

int main()
{
	int num;
	cout << "Input a number";
	cin >> num;
	if (num == 0) return 0;
	else if (num == 1)
	{
		In1();
		for (int f = 0; f < n; f++)
			if (Pr(a[f]))
				Out2(a[f]);
	}
	else if (num == 2)
	{
		Bai2();
	}
	else if (num == 3)
	{
		In1();
		Bai3();
	}
	else if (num == 4)
	{
		Bai4();
	}
	else if (num == 5)
	{
		In2d();
		Bai5();
	}
	else if (num == 6)
	{
		In2d();
		Bai6();
	}
	else if (num == 7)
	{
		In2d();
		Bai7();
		Out2d();
	}
	else if (num == 8)
	{
		cout << "Input numbers of rows and columns: ";
		cin >> r >> cl;
		for (int i = 0; i < r * cl; i++) cin >> a[i];
		Bai8();
		Out2d();
	}
	else if (num == 9)
	{
		In2d();
		Bai9();
	}
	else if (num == 10)
	{
		cout << "Nhap ma tran A" << endl;
		cout << "Input rows and colums"; cin >> r >> cl;
		for (int i = 0; i < r; i++)
			for (int j = 0; j < cl; j++)
				cin >> c[i][j];
		cout << "Nhap ma tran B" << endl;
		cout << "Input rows and colums"; cin >> r2 >> cl2;
		for (int i = 0; i < r2; i++)
			for (int j = 0; j < cl2; j++)
				cin >> d[i][j];
		Bai10();
		cout << "The product: " << endl;
		for (int i = 0; i < r; i++)
		{
			for (int j = 0; j < cl; j++)
				cout << sum[i][j] << " ";
			cout << endl;
		}

	}
	else if (num == 0)
		return 0;
	else cout << "Invalid input!";
}
