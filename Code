#include <iostream>
#include <algorithm>
#include <string>
#include <cmath>
#include <vector>
#include <iomanip>
#include <cstring>
#define ll long long
using namespace std;

int main() {
    int n, m, i, j, k;
    cout.precision(4);
    cout.setf(ios::fixed);
    cout << "\nEnter the number of rows (n) and columns (m) of the matrix: \n";
    cin >> n >> m;


    float a[n][m + 1], x[n];

    // Enter elements
    cout << "\nEnter the elements of the matrix row by row: \n";
    for (i = 0; i < n; i++)
        for (j = 0; j <= m; j++)
            cin >> a[i][j];

    if(m>n){cout<<"\\nInfinite solutions exist for the given system of equations.\\n";}
    else {

        // Arrange the matrix
        for (i = 0; i < n; i++)
            for (k = i + 1; k < n; k++)
                if (abs(a[i][i]) < abs(a[k][i])) {
                    for (j = 0; j <= m; j++) {
                        swap(a[i][j], a[k][j]);
                    }
                }

        // Gauss elimination
        for (i = 0; i < n; i++)
            for (k = i + 1; k < n; k++) {
                float temp = a[k][i] / a[i][i];
                for (j = 0; j <= m; j++) {
                    a[k][j] = a[k][j] - temp * a[i][j];
                }
            }

        // Check for no solution or infinite solutions
        bool noSolution = false;
        bool infiniteSolutions = false;

        for (i = 0; i < n; i++) {
            bool allZeroes = true;
            for (j = 0; j < m; j++) {
                if (a[i][j] != 0) {
                    allZeroes = false;
                    break;
                }
            }

            if (allZeroes && a[i][m] != 0) {
                noSolution = true;
                break;
            } else if (allZeroes && a[i][m] == 0) {
                infiniteSolutions = true;
                break;
            }
        }

        if (noSolution) {
            cout << "\nNo solution exists for the given system of equations.\n";
        } else if (infiniteSolutions) {
            cout << "\nInfinite solutions exist for the given system of equations.\n";
        } else {
            // Set the values
            for (i = n - 1; i >= 0; i--) {
                x[i] = a[i][m]; // Last element
                for (j = i + 1; j < n; j++) {
                    if (j != i) {
                        x[i] = x[i] - a[i][j] * x[j];
                    }
                }
                x[i] = x[i] / a[i][i];
            }

            // Print the values of the variables
            cout << "\nThe values of the variables are: \n";
            for (i = 0; i < n; i++) {
                cout << "x" << i + 1 << ": " << x[i] << endl;
            }
        }
    }

    return 0;
}
