# Adjacency List with C

### Representation of Graph with adjacency list in C

**We create linked list and one list of heads to represent adjacency list**


```

//adjacency list -> linked list
typedef struct node{
  int data;
  struct node *next;
}node;

// Storing head address for each list
typedef struct list{
  node *head;
}list;

// head1 -> linkedlist
// head2 -> linkedlist
// head3 -> linkedlist

//headlist for storing the head of
//each linked list
list *headlist[10]={0};


//add Node function
void addNode(int v,int w)
{
  node *src,*des,*tmp;
  if(headlist[v]->head==NULL)
  {
    src=(node*)malloc(sizeof(node));
    src->data=v;
    src->next=NULL;
    headlist[v]->head=src;
  }
  dest=(node*)malloc(sizeof(node));
  dest->data=w;
  dest->next=NULL;
  tmp=headlist[v]->head;
  while(tmp->next!=NULL)
  {
    tmp=tmp->next;
  }
  tmp->next=dest;
}


void main()
{
  //initalize the headlist with null contents
  for(int i=0;i<10;i++)
  {
    headlist[i]=(list*)malloc(sizeof(list));
    headlist[i]->head=NULL;
  }

  //add node to add the nodes in adj list
  addNode(0,1);
  addNode(0,3);
  addNode(1,2);
  printList();
  getch();
}

```
