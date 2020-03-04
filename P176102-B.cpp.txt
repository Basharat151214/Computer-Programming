#include <iostream>
#include <cstdlib>
#include <iomanip>

using namespace std;

void printmatrix(float A[][3]);
void RowReduce(float A[][3]);

int main()
{
    float A[3][3] = {{-2, 1, 3},
                     {0, 1,  1},
                     {2,  0, 1}}; 
cout<<"Enter the values"<<endl;

    printmatrix(A);
    RowReduce(A);
}

void printmatrix(float A[][3]) 
{
    int p=3;
    int q=3;

    for (int i=0; i<p; i++) {
            for (int j=0; j<q; j++) {
                    cout << setw(5) << setprecision(2) << A[i][j] << " ";
            }
            cout << endl;
    }

    cout << endl;
}

void RowReduce(float A[][3])
{
    const int nrows = 3; 
    const int ncols = 3;

    int lead = 0; 

    while (lead < nrows) {
        float d, m;

        for (int r = 0; r < nrows; r++) { 
            d = A[lead][lead];
            m = A[r][lead] / A[lead][lead];

            for (int c = 0; c < ncols; c++) { 
                if (r == lead)
                    A[r][c] /= d;               
                else
                    A[r][c] -= A[lead][c] * m;  
            }
        }

        lead++;
        printmatrix(A);
    }
}