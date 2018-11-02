# Range-based for loop


```C++ runnable
#include<iostream>
using namespace std;

template<typename T, int sizeOfArray>
class MyCustomType
{
private:
    T *data;
    int indx;
public:
    MyCustomType(){
        data = new T[sizeOfArray];
        indx = -1;
    }
    ~MyCustomType(){
        delete []data;
    }
    void addData(T newVal){
        data[++indx] = newVal;
    }

    //write definition for begin() and end()
    //these two method will be used for "ranged based loop idiom"
    T* begin(){
        return &data[0];
    }
    T* end(){
        return  &data[sizeOfArray];
    }
};
int main()
{
    MyCustomType<double, 2> numberList;
    numberList.addData(20.25);
    numberList.addData(50.12);
    for(auto val: numberList){
        cout<<val<<endl;
    }
    return 0;
}
