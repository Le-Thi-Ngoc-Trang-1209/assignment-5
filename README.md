// assignment 5.1
/*  List */
#include<iostream>
using namespace std;
struct Node{
    int data;
    Node* next;
};
Node* createNode(int x){
    Node *temp = new Node;
    temp->data=x;
    temp->next=NULL;
    return temp;
}
/*Stack*/
class Stack{
    Node* head;
    int size;
public:
    Stack(){
        head = NULL;
        size = 0;
    };
    void push_back(int x);
    void pop_back();
    int top();
    bool isEmpty();
};
void Stack::push_back(int x){
    if(size == 0){
        Node* temp = createNode(x);
        temp->next = head;
        head = temp;
        size++;
    }
    else{
        Node* temp=createNode(x);
        Node* p=head;
        while(p->next!=NULL){
            p=p->next;
        }
        p->next=temp;
        size++;
    }
}
void Stack::pop_back(){
    if(!isEmpty()){
        Node* p = head;
        for(int i=0; i<size-2;i++){ 
            p = p->next;
        }
        Node* temp = p->next;
        p->next=NULL;
        delete temp;
        size--;
    }
}
int Stack::top(){
    Node* p=head;
    while(p->next!=NULL){
        p=p->next;
    }
    return p->data;
}
bool Stack::isEmpty(){
    return (size==0);
}
/* Queue */
class Queue{
    Node* head;
    int size;
public:
    Queue(){
        head = NULL;
        size = 0;
    };

    void push_back(int x);
    void pop_front();
    int front();
    bool isEmpty();
};
void Queue::push_back(int x){
    if(size == 0){
        Node* temp = createNode(x);
        temp->next = head;
        head = temp;
        size++;
    }
    else{
        Node* temp=createNode(x);
        Node* p=head;
        while(p->next!=NULL){
            p=p->next;
        }
        p->next=temp;
        size++;
    }
}
void Queue::pop_front(){
    if(!isEmpty()){
        Node* temp = head;
        head = head->next;
        size--;
        delete temp;
    }
}
int Queue::front(){
    return head->data;
}
bool Queue::isEmpty(){
    return (size==0);
}
int main(){
    Stack S;
    Queue Q;
    for(int i=0;i<5;i++){
        S.push_back(i);
        Q.push_back(i);
    }
    cout << "Stack: ";
    while(!S.isEmpty()){
        cout << S.top() << '\t';
        S.pop_back();
    }
    cout << "\nQueue: ";
    while(!Q.isEmpty()){
        cout << Q.front() << '\t';
        Q.pop_front();
  }
    return 0;
}
//                                                           .bai5.2                                
                             /* Double List  */
#include<iostream>
using namespace std;
struct Node{
    int data;
    Node* next;
    Node* pre;
};
Node* createNode(int x){
    Node *temp = new Node;
    temp->data=x;
    temp->next=NULL;
    temp->pre=NULL;
    return temp;
}
/* Stack */
class Stack{
    Node* head;
    Node* tail;
    int size;
public:
    Stack(){
        head = NULL;
        tail = NULL;
        size = 0;
    };
    void push_back(int x);
    void pop_back();
    int top();
    bool isEmpty();
};
void Stack::push_back(int x){
    if(size == 0){
        Node* temp = createNode(x);
        temp->next = head;
        head = temp;
        tail = head;
        size++;
    }
    else{
        Node* temp=createNode(x);
        temp->pre = tail;
        tail->next = temp;
        tail = temp;
        size++;
    }
}
void Stack::pop_back(){
    if(!isEmpty()){
        if(head==tail){
            Node* temp=head;
            head = NULL;
            tail = NULL;
            delete temp;
            size--;
        }
        else{
            Node *temp = tail;
            tail = tail->pre;
            tail->next = NULL;
            size--;
            delete temp;
        }
    }
}
int Stack::top(){
    return tail->data;
}
bool Stack::isEmpty(){
    return (size==0);
    // return (head==NULL && tail == NULL);
}
/* Queue */
class Queue{
    Node* head;
    Node* tail;
    int size;
public:
    Queue(){
        head = NULL;
        tail = NULL;
        size = 0;
    };
    void push_back(int x);
    void pop_front();
    int front();
    bool isEmpty();
};
void Queue::push_back(int x){
    if(size == 0){
        Node* temp = createNode(x);
        temp->next = head;
        head = temp;
        tail = head;
        size++;
    }
    else{
        Node* temp=createNode(x);
        temp->pre = tail;
        tail->next = temp;
        tail = temp;
        size++;
    }
}
void Queue::pop_front(){
    if(!isEmpty()){
        if(head==tail){
            Node* temp=head;
            head = NULL;
            tail = NULL;
            delete temp;
            size--;
        }
        else{
            Node *temp = head;;
            head = head->next;
            head->pre = NULL;
            size--;
            delete temp;
        }
    }
}
int Queue::front(){
    return head->data;
}
bool Queue::isEmpty(){
    return (size==0);
}
int main(){
    Stack S;
    Queue Q;
    for(int i=0;i<5;i++){
        S.push_back(i);
        Q.push_back(i);
    }
    cout << "Stack: ";
    while(!S.isEmpty()){
        cout << S.top() << '\t';
        S.pop_back();
    }
    cout << "\nQueue: ";
    while(!Q.isEmpty()){
        cout << Q.front() << '\t';
        Q.pop_front();
    }
    return 0;
}
