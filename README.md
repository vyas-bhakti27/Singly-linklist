#include<stdio.h>  // Singly linked list program
#include<stdlib.h>

struct node
{
    int data;
    struct node *next;
}*start=NULL,*q,*t;

int main()
{
    int ch;
    void insert_first();
    void insert_last();
    int insert_pos();
    void display();
    void delete_first();
    void delete_last();
    int delete_pos();

    while(1)
    {
        printf("\n enter 1.Insert\n enter 2.Display\n enter 3.Delete\n enter 4.Exit\n\n");
        printf("Enter the number b/w 1-4:");
        scanf("%d",&ch);

        switch(ch)
        {
            case 1:
                    printf("\n1.Insert at beginning\n2.Insert at end\n3.Insert at specified position\n4.Exit");
                    printf("\n\nEnter your choice(1-4):");
                    scanf("%d",&ch);

                    switch(ch)
                    {
                        case 1: insert_first();
                                break;
                        case 2: insert_last();
                                break;
                        case 3: insert_pos();
                                break;
                        case 4: exit(0);
                        default: printf("Wrong Choice!!");
                    }
                    break;

            case 2: display();
                    break;

            case 3: 
                    printf("\n1.Delete from beginning\n2.Delete from end\n3.Delete from specified position\n4.Exit");
                    printf("\n\nEnter your choice(1-4):");
                    scanf("%d",&ch);

                    switch(ch)
                    {
                        case 1: delete_first();
                                break;
                        case 2: delete_last();
                                break;
                        case 3: delete_pos();
                                break;
                        case 4: exit(0);
                        default: printf("Wrong Choice!!");
                    }
                    break;
            case 4: exit(0);
                    default: printf("Wrong Choice!!");
        }
    }
    return 0;
}

void insert_first()
{
    int num;
    t=(struct node*)malloc(sizeof(struct node));
    printf("Enter data:");
    scanf("%d",&num);
    t->data=num;

    if(start==NULL)        
    {
        printf("Availability Stack Underflow"); // linked list is empty
        t->next=NULL;
        start=t;
    }
    else
    {
        t->next=start;
        start=t;
    }
}

void insert_last()
{
    int num;
    t=(struct node*)malloc(sizeof(struct node));
    printf("Enter data:");
    scanf("%d",&num);
    t->data=num;
    t->next=NULL;

    if(start==NULL)        
    {
        printf("Availability Stack Underflow"); // linked list is empty
        start=t;
    }
    else
    {
        q=start;
        while(q->next!=NULL)
        q=q->next;
        q->next=t;
    }
}

int insert_pos()
{
    int pos,i,num;
    if(start==NULL)
    {
        printf("List is empty!!");
        printf("Availability Stack Underflow");
        return 0;
    }

    t=(struct node*)malloc(sizeof(struct node));
    printf("Enter data:");
    scanf("%d",&num);
    printf("Enter position to insert:");
    scanf("%d",&pos);
    t->data=num;

    q=start;
    for(i=1;i<pos-1;i++)
    {
        if(q->next==NULL)
        {
            printf("There are less elements!!");
            return 0;
        }

        q=q->next;
    }

    t->next=q->next;
    q->next=t;
    return 0;
}

void display()
{
    if(start==NULL)
    {
        printf("List is empty!!");
        printf("Availability Stack Underflow");
    }
    else
    {
        q=start;
        printf("The linked list is:\n");
        while(q!=NULL)
        {
            printf("%d->",q->data);
            q=q->next;
        }
    }
}

void delete_first()
{
    if(start==NULL)
    {
        printf("Underflow");
    }
    else
    {
        q=start;
        start=start->next;
        printf("Deleted element is %d",q->data);
        free(q);
    }
}

void delete_last()
{
    if(start==NULL)
    {
        printf("Underflow");
    }
    else
    {
        q=start;
        while(q->next->next!=NULL)
        q=q->next;

        t=q->next;
        q->next=NULL;
        printf("Deleted element is %d",t->data);
        free(t);
    }
}

int delete_pos()
{
    int pos,i;

    if(start==NULL)
    {
        printf("Underflow");
        return 0;
    }

    printf("Enter position to delete:");
    scanf("%d",&pos);

    q=start;
    for(i=1;i<pos-1;i++)
    {
        if(q->next==NULL)
        {
            printf("There are less elements!!");
            return 0;
        }
        q=q->next;
    }

    t=q->next;
    q->next=t->next;
    printf("Deleted element is %d",t->data);
    free(t);

    return 0;
}
