# -
矩阵运算
#include <iostream>
using namespace std;
class matrix{
	private:
		
	public:
		int A[10][10];
		int cow;
		int column;
	matrix(int r,int c);
    void getA();
    void setA();
 };
matrix::matrix(int r,int c)
{
	cow=r;
	column=c;
}
void matrix::getA()
{
    for(int i=0;i<cow;i++)
    {
    	for(int j=0;j<column;j++)
    	{
    		cout << A[i][j] << " ";
		}
		cout << endl;
	}
}
void matrix::setA()
{
	for(int i=0;i<cow;i++)
    {
    	for(int j=0;j<column;j++)
    	{
    		cin >> A[i][j];
		}
	}
}
void mul(matrix e1,matrix e2)
	{
		if(e1.column==e2.cow)
		{
			matrix ret(e1.cow,e2.column);
			for(int i=0;i<e1.cow;i++)
			{
				for(int j=0;j<e2.column;j++)
				{				
					ret.A[i][j]=0;
				}
			}
			for(int i=0;i<e1.cow;i++)
			{
				for(int j=0;j<e2.column;j++)
				{				
						for(int k=0;k<e1.column;k++)
						{
							ret.A[i][j]+=e1.A[i][k]*e2.A[k][j];
						}
				}
			}
			for(int i=0;i<e1.cow;i++)
			{
				for(int j=0;j<e2.column;j++)
				{				
					cout << ret.A[i][j] << " ";
				}
				cout << endl;
			}
		}
		else
		{
			cout << "行列不相等，无法乘积";		
		}		
	}		
int main()
{
	int n,m;
	cin >> n >> m;
	matrix a1(n,m);
	a1.setA();
	cin >> n >> m;
    matrix a2(n,m);
    a2.setA();
    matrix a3(n,m);
    mul(a1,a2);
	return 0;
}
