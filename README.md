# Remove-duplicates
Remove duplicate elements from a sorted linked list
//Remove duplicates from sorted linked list
#include<iostream>
using namespace std;

struct Node{
	int data;
	Node *next;
	Node(int d){
		data=d;
		next=NULL;
	}
};

void remDuplicates(Node* head){
	Node* curr=head;
	while(curr!=NULL && curr->next!=NULL){
		if(curr->data==curr->next->data){
			Node* temp=curr->next;
			curr->next=curr->next->next;
			delete(temp);
		}
		else{
			curr=curr->next;
		}
	}
}

Node* insertAtEnd(Node* head,int y){
	Node* temp = new Node(y);
	if(head==NULL){
		return temp;
	}
	Node* curr=head;
	while(curr->next!=NULL){
		curr=curr->next;
	}
	curr->next=temp;
	return head;
}

void printList(Node* head){
	Node* curr=head;
	while(curr!=NULL){
		cout<<curr->data;
		curr=curr->next;
	}
}

int main(){
	Node* head1=NULL;
	int n1;
	cin>>n1;
	for(int i=1;i<=n1;i++){
		int x;
		cin>>x;
		head1=insertAtEnd(head1,x);
	}
	printList(head1);
	cout<<endl;
	remDuplicates(head1);
	printList(head1);
}
