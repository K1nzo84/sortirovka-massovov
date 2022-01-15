# sortirovka-massovov
сортировка массивов



#include <iostream>
#include <ctime>

using namespace std;

template<typename T> void show(T m[], int size_m)
{
    cout << "\n__________________________________\n";
    for (int i = 0; i < size_m; i++)
    {
        cout << m[i] << ";";
    }
}

template<typename T> void rand_m(T m[], int size_m,T x, T y)
{
    
    for (int i = 0; i < size_m; i++)
    {
        m[i] = double(rand()) / RAND_MAX * (y - x) + x;
    }
}

template<typename T> void sort_bub(T m[], int size_m)
{
    for (int j = 0; j < size_m; j++)// алгоритм пузырьковый сортировки
    {
        int counter = 0;
        for (int i = 0; i < size_m - 1; i++)
        {
            if (m[i] > m[i + 1])
            {
                T c = m[i];
                m[i] = m[i + 1];
                m[i + 1] = c;
                counter ++ ;
            }
        }
        if (counter == 0)break;
    }
}

template<typename T> void sort_vi(T m[], int size_m)
{
    for (int j = 0; j < size_m-1; j++)// алгоритм сортировки выбором
    {
        T min = m[j];
        int min_p = j;
        for (int i = j; i < size_m; i++)
        {
            
            if (m[i] < min)
            {
                min = m[i];
                min_p = i;
            }
        }
        T c = m[j];
        m[j] = m[min_p];
        m[min_p] = c;
    }
}

template<typename T> int find_b (T fnd, T m[], int size_m)
{
   // алгоритм бинарного поиска
    int x = 0;
    int y = size_m;
    while ((y - x) > 0)
    {
        int mid = x + (y - x) / 2;
        if (m[mid] == fnd)
            return mid;
        if (m[mid] > fnd)
            y = mid - 1;
        else
            x = mid + 1;
    }
    return -1;
}


int main()
{
    srand(time(0));
    const int size_m = 20;
    int ar[size_m]{};
    rand_m(ar, size_m, 1, 9);
    show(ar, size_m);
    sort_vi(ar, size_m);
    show(ar, size_m);
    cout << "\n";
    cout<<find_b(ar[size_m - 1], ar, size_m);// вывод на экран максимального значение в отсортированном массиве
}
