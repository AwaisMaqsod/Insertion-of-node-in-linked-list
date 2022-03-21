# Insertion-of-node-in-linked-list
four ways to insert node in linked list, c++
#include<iostream>
using namespace std;
struct Node{
	int data;
	Node*next;
	
};
//in printALL function i give a peremeter (Node*ptr) that means node pointer, and we point ptr to Head.  
void printAll(Node*ptr){//pointes to head of link list
	while(ptr!=NULL){
		cout<<ptr->data<<endl;
		ptr=ptr->next;
	}
}

Node* atfront(Node**ptr){
	//creating new node
	Node*newNode=new Node;
	newNode->data=49;
	newNode->next=*ptr;
	*ptr=newNode;
}

Node* atlast(Node*head,int data){
//	creating node
Node*newNode=new Node;
newNode->data=data;
struct Node*p=head;
//p poits to head
while(p->next!=NULL){
	p=p->next;
}
//head of pointer is equal to newNode
p->next=newNode;
newNode->next=NULL;
return head;	
}
Node* afterNode(Node*head,Node*prevNode,int data){
Node*newNode=new Node;//creating new node newNode
newNode->data=data;// giving data to newNode

newNode->next=prevNode->next;//next of newNode is equal to next of prevNode
prevNode->next=newNode;//next of prevNode is equal to prevNode
}
Node * atIndex(Node*head,int data,int index){

Node*newNode=new Node;
Node*p=head;
int i=0;
while(i!=index-1){
	p=p->next;
	i++;
}	
newNode->data=data;
newNode->next=p->next;
p->next=newNode;
}



int main(){
	//creating nodes
	struct Node*Head=new Node;//node one
	struct Node*second=new Node;//node two
	struct Node*tail=new Node;//node third
	//giving data to nodes  
	Head->data=1;
	second->data=2;
	tail->data=3;
	//giving values to pointer next
    Head->next=second;
	second->next=tail;
	tail->next=NULL;
	//functions
	atIndex(Head,11,1);//insertion by giving index
	afterNode(Head,second,50);//insertion by giving previous node
	atfront(&Head);//insertion on head
	atlast(Head,100);//insertion at last
    printAll(Head);
    
	return 0;
}
