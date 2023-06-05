# DSA
https://docs.google.com/document/d/1jwsndTjOGRka_ZOpUz_3rctM5xWxNRj28p58thGlOCM/edit?usp=sharing

CODE NO 10

#include<iostream>
using namespace std;
#define max 20

class stud
{
int mks[max]; //array of marks   max is nothing but the array size which we define.

public:
    stud() //constructor  which is initializing the array over here.
    {
    for(int i=0;i<max;i++)
      mks[i]=0; //in initializing the array we insert 0's from 1st to last position in array.
    }

    void insertheap(int tot); //to insert element into heap. 
    void displayheap(int tot); //to display data from heap.
    void showmax(int tot); //to show max heap.
    void showmin(); // to show min heap.
};

// We declare some function in the class stud,
// And now we are writing the defination of the function outside the class.

void  stud::insertheap(int tot) // the count total from main function we just pass here as int tot.
{
 for(int i=1;i<=tot;i++) //eg. tot=10 so it will as 10 times to enter the marks.
 {
   cout<<"enter marks";
   cin>>mks[i];

    int j=i; //eg. i = 1 so j = 1 here 1 is the position in array not marks.
    int par=j/2;  //eg. par = 1/2 = 0.5 = 0 (integer), par = 2/2 = 1.
    while(mks[j]<=mks[par] && j!=0) // here it will compare the marks of j and marks of partition 
     {
        int tmp = mks[j]; // here we use swapping technique
        mks[j]=mks[par];
        mks[par]=tmp;
        j=par; // again we comparing and swapping the position until first position or 0.
        par=j/2;
     }       
 }
}

void stud::displayheap(int tot)
{
int i=1,space=6;
cout<<endl;
while(i<=tot)
{
    if(i==1 || i==2 || i==4 || i==8 || i==16)
    {
    cout<<endl<<endl;
    for(int j=0;j<space;j++)
         cout<<" ";
    space-=2;   
    }
   cout<<" "<<mks[i];i++;
         
}
}

void stud::showmax(int tot)
{
    int max1=mks[1];
    for(int i=2;i<=tot;i++)
    {
        if(max1<mks[i])
        max1= mks[i];
    }
    cout<<"Max marks:"<<max1;
}

void stud::showmin() //
{
    cout<<"Min marks:"<<mks[1];
}


int main(){
int ch,count,total;
stud s1; //we creat s1 object of class stud so we can access the member functions.

do
{
cout<<endl<<"Menu";
cout<<endl<<"1.Read marks of the student: ";
cout<<endl<<"2.Display Min heap: "; // min heap = root element is less than child element.
cout<<endl<<"3.Find Max Marks: ";
cout<<endl<<"4.Find Min Marks: ";
cout<<endl<<"Enter Your Choice: ";
cin>>ch;
switch(ch)
{
case 1:
    cout<<"how many students";
    cin>>total;
    s1.insertheap(total); // Call insert function to insert elements. 
    break;
case 2:
    s1.displayheap(total); // Call display function.
    break;
case 3:    
    s1.showmax(total); // To find max element.
    break;
case 4:
    s1.showmin(); // To find min element.
    break;
}
cout<<endl<<"do u want to continue?(1 for continue)";
cin>>count;
}while(count==1);
return 0; // it is an intiger main so it returning 0.
}


________________________________________________________

CODE 1

#include <iostream>
using namespace std;

//heapify function to maintain heap property
// n is the size of heap ,i is the every elements in array
void heapify(int arr[], int n, int i) {
    int largest = i;     // initialize largest as a root since we are using 0 based indexig 
    int left = 2 * i + 1; //left = 2*i+1
    int right = 2 * i + 2; // right = 2*i+2

    if (left < n && arr[left] > arr[largest]) //if left child is larger than root 
        largest = left;

    if (right < n && arr[right] > arr[largest]) //if right child is larger than root
        largest = right;

    if (largest != i) {
        swap(arr[i], arr[largest]);   // swap elemntss largest element stored into sorted list
        heapify(arr, n, largest);     //recursively heapify affect the sub tree 
    }
}

void heapSort(int arr[], int n) {
    for (int i = n / 2 - 1; i >= 0; i--)  // divide array into left and right subtree 
        heapify(arr, n, i);                // call function maintain heap property

    for (int i = n - 1; i > 0; i--) {   //one by one extract an element from heap
        swap(arr[0], arr[i]);           //move current root to end
        heapify(arr, i, 0);             // call max heafiy on the reduced heap
    }
}
void printArray(const int arr[], int n) {
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;
}

void getUserInput(int arr[], int n) {
    cout << "Enter the elements: ";
    for (int i = 0; i < n; i++)
        cin >> arr[i];
}

int main() {
    int choice;
    cout << "1. Heap Sort\n";
    cout << "Enter your choice: ";
    cin >> choice;

    int n;
    cout << "Enter the number of elements: ";
    cin >> n;

    int arr[n];
    getUserInput(arr, n);

    cout << "Original array: ";
    printArray(arr, n);

    switch (choice) {
        case 1:
            heapSort(arr, n);
            cout << "Array after Heap Sort: ";
            printArray(arr, n);
            break;
        default:
            cout << "Invalid choice. Exiting...";
            Break;
 }

    return 0;
}

   ____________________________________________________
 

CODE 7

#include <iostream>
#include <stdlib.h>
using namespace std;
int cost[10][10], i, j, k, n, qu[10], front=0, rear=0, v, visit[10], visited[10];
int stk[10], top=0, visit1[10], visited1[10];
int main()
{
int m;
cout << "Enter number of vertices : ";
cin >> n;
cout << "Enter number of edges : ";
cin >> m;
cout << "\nEDGES :\n";
for (k = 1; k <= m; k++)
{
cin >> i >> j;
cost[i][j] = 1;
//cost[j][i] = 1;
}
//display function
cout << "The adjacency matrix of the graph is : " << endl;
for (i = 1; i <= n; i++)
{
for (j = 1; j <= n; j++)
{
cout << " " << cost[i][j];
}
cout << endl;
}
cout<<"The adjacency list is of the graph is: \n";
for (i=1;i<=n;i++)
{
cout<<i<<"-->";
for(j=1;j<=n;j++)
{
if(cost[i][j]==1)
cout<<j<<" ";
}
cout<<endl;
}
//bfs
cout << "Enter initial vertex : ";
cin >> v;
cout << "The BFS of the Graph is\n";
cout << v<<endl;
visited[v] = 1;
k = 1;
while (k < n)
{
for (j = 1; j <= n; j++)
if (cost[v][j] != 0 && visited[j] != 1 && visit[j] != 1)
{
visit[j] = 1;
qu[rear++] = j;
}
v = qu[front++];
cout << v << " ";
k++;
visit[v] = 0;
visited[v] = 1;
}
//dfs
cout <<endl<<"Enter initial vertex : ";
cin >> v;
cout << "The DFS of the Graph is\n";
cout << v<<endl;
visited[v] = 1;
k = 1;
while (k < n)
{
for (j = n; j >= 1; j--)
if (cost[v][j] != 0 && visited1[j] != 1 && visit1[j] != 1)
{
visit1[j] = 1;
stk[top++] = j;
// top++;
}
v = stk[--top];
cout << v << " ";
k++;
visit1[v] = 0;
visited1[v] = 1;
}
cout<<endl;
}
__________________________________


/*
There are flight paths between cities. If there is a flight between city A and city B 
then there is an edge between the cities. The cost of the edge can be the time that flight 
take to reach city B from A, or the amount of fuel used for the journey. Represent this as a
 graph. The node can be represented by airport name or name of the city. Use adjacency list 
 representation of the graph or use adjacency matrix representation of the graph.
Check whether the graph is connected or not. Justify the storage representation used.
*/
#include <iostream>
#include <string.h>
using namespace std;

class flight
{
public:
	flight();
	int am[10][10];
	char city_index[10][10];
	int create();
	void display(int city_count);
};

flight::flight()
{
	int i, j;
	for (i = 0; i < 10; i++)
	{
		strcpy(city_index[i], "xx");
	}
	for (i = 0; i < 10; i++)
	{
		for (j = 0; j < 10; j++)
		{
			am[i][j] = 0;
		}
	}
}

int flight::create()
{
	int city_count = 0, j, si, di, wt;
	char s[10], d[10], c;
	do
	{
		cout << "\n\tEnter Source City      : ";
		cin >> s;
		cout << "\n\tEnter Destination City : ";
		cin >> d;
		for (j = 0; j < 10; j++)
		{
			if (strcmp(city_index[j], s) == 0)
				break;
		}
		if (j == 10)
		{
			strcpy(city_index[city_count], s);
			city_count++;
		}

		for (j = 0; j < 10; j++)
		{
			if (strcmp(city_index[j], d) == 0)
				break;
		}

		if (j == 10)
		{
			strcpy(city_index[city_count], d);
			city_count++;
		}

		cout << "\n\t Enter Distance From " << s << " And " << d << ": ";
		cin >> wt;

		for (j = 0; j < 10; j++)
		{
			if (strcmp(city_index[j], s) == 0)
				si = j;
			if (strcmp(city_index[j], d) == 0)
				di = j;
		}

		am[si][di] = wt;
		cout << "\n\t Do you want to add more cities.....(y/n) : ";
		cin >> c;
	} while (c == 'y' || c == 'Y'); 
	return (city_count);
}
void flight::display(int city_count)
{
	int i, j;
	cout << "\n\t Displaying Adjacency Matrix :\n\t";
	for (i = 0; i < city_count; i++)
		cout << "\t" << city_index[i];
		cout << "\n";

		for (i = 0; i < city_count; i++)
		{
			cout << "\t" << city_index[i];
				for (j = 0; j < city_count; j++)
					{
						cout << "\t" << am[i][j];
					}
					cout << "\n";
		}
}

int main()
{
	flight f;
	int n, city_count;
	char c;
	do
	{
		cout << "\n\t** Flight Main Menu **";
		cout << "\n\t1. Create \n\t2. Adjacency Matrix\n\t3. Exit";
		cout << "\n\t.....Enter your choice : ";
		cin >> n;
		switch (n)
		{
		case 1:
			city_count = f.create();
			break;
		case 2:
			f.display(city_count);
			break;
		case 3:
			return 0;
		}
		cout << "\n\t Do you Want to Continue in Main Menu....(y/n) : ";
		cin >> c;
	} while (c == 'y' || c == 'Y');
	return 0;
}

_____________________________________________

CODE 11

/*
Department maintains a student information. The file contains roll number, name, division
and address. Allow user to add, delete information of student. Display information of
particular employee. If record of student does not exist an appropriate message is displayed.
If it is, then the system displays the student details. Use sequential file to main the data.
*/
#include<iostream>
#include<fstream>
#include<string.h>
using namespace std;
class student
  {
    typedef struct stud
    {
        int roll;
        char name[10];
        char div;
        char add[10];
    }stud;
    stud rec;
    public:
      void create();
      void display();
      int search();
      void Delete();
  };
void student::create()
  {
    char ans;
    ofstream fout;
    fout.open("stud.dat",ios::out|ios::binary);
    do
      {
        cout<<"\n\tEnter Roll No of Student    : ";
        cin>>rec.roll;
        cout<<"\n\tEnter a Name of Student     : ";
        cin>>rec.name;
        cout<<"\n\tEnter a Division of Student : ";
        cin>>rec.div;
        cout<<"\n\tEnter a Address of Student  : ";
        cin>>rec.add;
        fout.write((char *)&rec,sizeof(stud))<<flush;
        cout<<"\n\tDo You Want to Add More Records: ";
        cin>>ans;
      }while(ans=='y'||ans=='Y');
    fout.close();
  }
void student::display()
  {
    ifstream fin;
    fin.open("stud.dat",ios::in|ios::binary);
    fin.seekg(0,ios::beg);
    cout<<"\n\tThe Content of File are:\n";
    cout<<"\n\tRoll\tName\tDiv\tAddress";
    while(fin.read((char *)&rec,sizeof(stud)))
      {
        if(rec.roll!=-1)
              cout<<"\n\t"<<rec.roll<<"\t"<<rec.name<<"\t"<<rec.div<<"\t"<<rec.add;
      }
    fin.close();
  }
int student::search()
  {
    int r,i=0;
    ifstream fin;
    fin.open("stud.dat",ios::in|ios::binary);
    fin.seekg(0,ios::beg);
    cout<<"\n\tEnter a Roll No: ";
    cin>>r;
    while(fin.read((char *)&rec,sizeof(stud)))
      {
        if(rec.roll==r)
          {
            cout<<"\n\tRecord Found...\n";
            cout<<"\n\tRoll\tName\tDiv\tAddress";
            cout<<"\n\t"<<rec.roll<<"\t"<<rec.name<<"\t"<<rec.div<<"\t"<<rec.add;
            return i;
          }
        i++;
      }
    fin.close();
    return 0;
  }
void student::Delete()
  {
    int pos;
    pos=search();
    fstream f;
    f.open("stud.dat",ios::in|ios::out|ios::binary);
    f.seekg(0,ios::beg);
    if(pos==0)
      {
        cout<<"\n\tRecord Not Found";
        return;
      }
    int offset=pos*sizeof(stud);
    f.seekp(offset);
    rec.roll=-1;
    strcpy(rec.name,"NULL");
    rec.div='N';
    strcpy(rec.add,"NULL");
    f.write((char *)&rec,sizeof(stud));
    f.seekg(0);
    f.close();
    cout<<"\n\tRecord Deleted";
  }


int main()
  {
    student obj;
    int ch,key;
    char ans;
    do
      {
        cout<<"\n\t***** Student Information *****";
        cout<<"\n\t1. Create\n\t2. Display\n\t3. Delete\n\t4. Search\n\t5. Exit";
        cout<<"\n\t..... Enter Your Choice: ";
        cin>>ch;
        switch(ch)
          {
            case 1: obj.create();
                break;
            case 2: obj.display();
                break;
            case 3: obj.Delete();
                break;
            case 4: key=obj.search();
                if(key==0)
                  cout<<"\n\tRecord Not Found...\n";
                break;
            case 5:
                break;
          }
        cout<<"\n\t..... Do You Want to Continue in Main Menu: ";
        cin>>ans;
      }while(ans=='y'||ans=='Y');
return 1;
  }




