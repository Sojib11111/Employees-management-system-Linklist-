#include <iostream>
#include <string>
using namespace std;

struct emp_data
{
    int empno;
    string empName;
    string designation;
    int age;
    string phone;
    emp_data *next;
};

emp_data *insert(emp_data *front, int id, const string &name, const string &desg, int age, const string &phone)
{
    emp_data *temp = new emp_data;

    if (temp == NULL)
    {
        cout << "\n Allocation failed \n";
        exit(2);
    }

    temp->empno = id;
    temp->empName = name;
    temp->designation = desg;
    temp->age = age;
    temp->phone = phone;
    temp->next = front;
    front = temp;
    return front;
}

void printNode(emp_data *p)
{
    cout << "\n Employee Details:\n";
    cout << "\n Employee No    : " << p->empno;
    cout << "\n Name           : " << p->empName;
    cout << "\n Designation    : " << p->designation;
    cout << "\n Age            : " << p->age;
    cout << "\n Phone          : " << p->phone << "\n";
    cout << "-------------------------------------\n";
}

emp_data* deleteNode(emp_data *front, int id)
{
    emp_data *ptr;
    emp_data *bptr;

    if (front->empno == id)
    {
        ptr = front;
        cout << "\n Node deleted:";
        printNode(front);
        front = front->next;
        delete ptr;
        return front;
    }

    for (ptr = front->next, bptr = front; ptr != NULL; ptr = ptr->next, bptr = bptr->next)
    {
        if (ptr->empno == id)
        {
            cout << "\n Node deleted:";
            printNode(ptr);
            bptr->next = ptr->next;
            delete ptr;
            return front;
        }
    }

    cout << "\n Employee Number " << id << " not found ";
    return front;
}

void search(emp_data *front, int key)
{
    for (emp_data *ptr = front; ptr != NULL; ptr = ptr->next)
    {
        if (ptr->empno == key)
        {
            cout << "\n Key found:";
            printNode(ptr);
            return;
        }
    }

    cout << "\n Employee Number " << key << " not found ";
}

void display(emp_data *front)
{
    for (emp_data *ptr = front; ptr != NULL; ptr = ptr->next)
    {
        printNode(ptr);
    }
}

void menu()
{
    cout << "---------------------------------------------\n";
    cout << "Enter option: \n";
    cout << "1 to INSERT a record into the database       \n";
    cout << "2 to DELETE a record from the database       \n";
    cout << "3 to DISPLAY the records                 \n";
    cout << "4 to SEARCH the records                   \n";
    cout << "5 to EXIT                              \n";
    cout << "---------------------------------------------\n";
}

int main()
{
    emp_data *linkList = NULL;
    string name, desig, phone;
    int choice;
    int eno, age;
    bool flag = false;

    cout << "\n MAIN MENU \n";
    menu();

    while (!flag)
    {
        cout << "\n Enter choice : ";
        cin >> choice;

        switch (choice)
        {
            case 1:
                cout << "\n Enter the Employee Number: ";
                cin >> eno;
                cout << " Enter the Employee name: ";
                cin.ignore();
                getline(cin, name);
                cout << " Enter the Employee Designation: ";
                getline(cin, desig);
                cout << " Enter the Employee Age: ";
                cin >> age;
                cout << " Enter the Employee Phone Number: ";
                cin.ignore();
                getline(cin, phone);
                linkList = insert(linkList, eno, name, desig, age, phone);
                break;

            case 2:
                cout << "\n\n Enter the employee number to be deleted: ";
                cin >> eno;
                linkList = deleteNode(linkList, eno);
                break;

            case 3:
                if (linkList == NULL)
                {
                    cout << "\n List is empty.";
                    break;
                }
                display(linkList);
                break;

            case 4:
                cout << "\n\n Enter the employee number to be searched: ";
                cin >> eno;
                search(linkList, eno);
                break;

            case 5:
                exit(0);

            default:
                cout << "Invalid option. Please try again.\n";
        }
    }

    return 0;
}
