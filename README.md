## EX 5 : TWO DIMENSIONALTRANSFORMATION 

NAME : MOHAMED NIZAMUDDIN A

REG NO : 212224040194

## AIM

To write a c program to implement 2D transformation of image.


## ALGORITHM

Step 1:Start the program.

Step 2:Draw the image with default parameters.

Step 3 : Get the choice from the user.

Step 4: Get the parameters for transformation.

Step 5 : Perform the transformation.

Step 6 : Draw the image.

Step 7 : Stop the program.


## Program :
```
#include<graphics.h>
#include<stdio.h>
#include<conio.h>
#include<math.h>
#include<stdlib.h>

int main() 
{
    int gd = DETECT, gm, i, j, k, ch;
    float tx, ty, x, y, ang, n, temp;
    float a[5][3], si, co, b[5][3], c[5][3];

    initgraph(&gd, &gm,"c:\\turboc3\\bgi");
    
    n = 4;
    a[0][0]=0; a[0][1]=0;
    a[1][0]=100; a[1][1]=0;
    a[2][0]=100; a[2][1]=100;
    a[3][0]=0; a[3][1]=100;
    a[4][0]=0; a[4][1]=0;
    
    while(1)
    {
        cleardevice();
        gotoxy(1,8);
        printf("\n\t******** Program to perform 2-D Transformations ********");
        printf("\n\t\t\t 1. Accept the polygon");
        printf("\n\t\t\t 2. Perform translation");
        printf("\n\t\t\t 3. Perform scaling");
        printf("\n\t\t\t 4. Perform rotation");
        printf("\n\t\t\t 5. Perform reflection");
        printf("\n\t\t\t 6. Perform shearing");
        printf("\n\t\t\t 7. Exit");
        printf("\n\t\t\t Enter your choice::");
        scanf("%d",&ch);
        
        switch(ch)
        {
            case 1: 
                cleardevice();
                gotoxy(1,1);
                printf("\n\tEnter no of points: ");
                scanf("%f",&n);
                
                for(i=0;i<n;i++)
                {
                    printf("\n\t Enter x,y co-ordinates for %d::",i+1);
                    scanf("%f %f",&a[i][0],&a[i][1]);
                }
                a[i][0]=a[0][0];
                a[i][1]=a[0][1];
                cleardevice();
                for(i=0;i<n;i++)
                    line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
                line(0,240,639,240);
                line(320,0,320,479);
                getch();
                break;
            
            case 2:
                cleardevice();
                for(i=0;i<n;i++)
                    line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
                line(0,240,639,240);
                line(320,0,320,479);
                gotoxy(1,1);
                printf("Enter translation vectors tx and ty: ");
                scanf("%f %f",&x,&y);
                cleardevice();
                for(i=0;i<n;i++)
                    line(320+a[i][0]+x,240-(a[i][1]+y),320+a[i+1][0]+x,240-(a[i+1][1]+y));
                line(0,240,639,240);
                line(320,0,320,479);
                getch();
                break;
            
            case 3:
                cleardevice();
                for(i=0;i<n;i++)
                    line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
                line(0,240,639,240);
                line(320,0,320,479);
                gotoxy(1,1);
                printf("Enter scaling factors sx and sy: ");
                scanf("%f %f",&x,&y);
                if(x==0) x=1;
                if(y==0) y=1;
                cleardevice();
                for(i=0;i<n;i++)
                    line(320+(a[i][0]*x),240-(a[i][1]*y),320+(a[i+1][0]*x),240-(a[i+1][1]*y));
                line(0,240,639,240);
                line(320,0,320,479);
                getch();
                break;
            
            case 4:
                cleardevice();
                for(i=0;i<n;i++)
                    line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
                line(0,240,639,240);
                line(320,0,320,479);
                gotoxy(1,1);
                printf("Enter the angle of rotation: ");
                scanf("%f",&ang);
                ang = ang * 0.01745;
                printf("Enter point of rotation (x,y): ");
                scanf("%f %f",&x,&y);
                printf("1. Clockwise  2. Anticlockwise\nEnter choice: ");
                scanf("%d",&k);
                si = sin(ang);
                co = cos(ang);
                for(i=0;i<n+1;i++)
                {
                    c[i][0]=a[i][0];
                    c[i][1]=a[i][1];
                    c[i][2]=1;
                }
                b[0][0]=co;
                b[0][1]=si;
                b[0][2]=0;
                b[1][0]=-si;
                b[1][1]=co;
                b[1][2]=0;
                b[2][0]=(-x*co)+(y*si)+x;
                b[2][1]=(-x*si)-(y*co)+y;
                b[2][2]=1;
                
                if(k==1) // clockwise
                {
                    b[0][1]=-si;
                    b[1][0]=si;
                    b[2][0]=(-x*co)-(y*si)+x;
                    b[2][1]=(-x*si)+(y*co)+y;
                }
                for(i=0;i<n+1;i++)
                    for(j=0;j<3;j++)
                    {
                        a[i][j] = 0;
                        for(k=0;k<3;k++)
                            a[i][j] += c[i][k]*b[k][j];
                    }
                cleardevice();
                for(i=0;i<n;i++)
                    line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
                line(0,240,639,240);
                line(320,0,320,479);
                getch();
                break;
            
            case 5:
                cleardevice();
                for(i=0;i<n;i++)
                    line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
                line(0,240,639,240);
                line(320,0,320,479);
                gotoxy(1,1);
                printf("\n1.Reflection about Y-axis");
                printf("\n2.Reflection about X-axis");
                printf("\n3.Reflection about Origin");
                printf("\n4.Reflection about line y=x");
                printf("\n5.Reflection about line y=-x");
                printf("\nEnter your choice: ");
                scanf("%d",&ch);
                switch(ch)
                {
                    case 1:
                        for(i=0;i<n+1;i++) a[i][0]*=-1;
                        break;
                    case 2:
                        for(i=0;i<n+1;i++) a[i][1]*=-1;
                        break;
                    case 3:
                        for(i=0;i<n+1;i++) { a[i][0]*=-1; a[i][1]*=-1; }
                        break;
                    case 4:
                        for(i=0;i<n+1;i++) { temp=a[i][0]; a[i][0]=a[i][1]; a[i][1]=temp; }
                        break;
                    case 5:
                        for(i=0;i<n+1;i++) { temp=a[i][0]; a[i][0]=a[i][1]; a[i][1]=temp; a[i][0]*=-1; a[i][1]*=-1; }
                        break;
                }
                cleardevice();
                for(i=0;i<n;i++)
                    line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
                line(0,240,639,240);
                line(320,0,320,479);
                getch();
                break;
            
            case 6:
                cleardevice();
                for(i=0;i<n;i++)
                    line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
                line(0,240,639,240);
                line(320,0,320,479);
                gotoxy(1,1);
                printf("\n1. X shear with Y reference");
                printf("\n2. Y shear with X reference");
                printf("\nEnter your choice: ");
                scanf("%d",&ch);
                switch(ch)
                {
                    case 1:
                        printf("\nEnter x-shear parameter: ");
                        scanf("%f",&temp);
                        printf("\nEnter y reference line: ");
                        scanf("%f",&ty);
                        b[0][0]=1; b[0][1]=0; b[0][2]=0;
                        b[1][0]=temp; b[1][1]=1; b[1][2]=0;
                        b[2][0]=-temp*ty; b[2][1]=0; b[2][2]=1;
                        break;
                    case 2:
                        printf("\nEnter y-shear parameter: ");
                        scanf("%f",&temp);
                        printf("\nEnter x reference line: ");
                        scanf("%f",&tx);
                        b[0][0]=1; b[0][1]=temp; b[0][2]=0;
                        b[1][0]=0; b[1][1]=1; b[1][2]=0;
                        b[2][0]=0; b[2][1]=-temp*tx; b[2][2]=1;
                        break;
                    default: break;
                }
                for(i=0;i<n+1;i++) a[i][2]=1;
                for(i=0;i<n+1;i++)
                    for(j=0;j<3;j++)
                    {
                        c[i][j] = 0;
                        for(k=0;k<3;k++)
                            c[i][j] += a[i][k]*b[k][j];
                    }
                cleardevice();
                for(i=0;i<n;i++)
                    line(320+c[i][0],240-c[i][1],320+c[i+1][0],240-c[i+1][1]);
                line(0,240,639,240);
                line(320,0,320,479);
                getch();
                break;
            
            case 7:
                closegraph();
                exit(0);
                break;
                
            default:
                break;
        }
    }
}



```


## Output :
![Screenshot (35)](https://github.com/user-attachments/assets/f77a22c1-a6f0-4634-8d92-53c23cc5aae5)

![Screenshot (36)](https://github.com/user-attachments/assets/4e8fa9ac-f0b9-44a4-8ffd-8f06e1af3691)

![Screenshot (37)](https://github.com/user-attachments/assets/1ef583b1-3b90-462a-9ee3-27d8623b4d5a)

![Screenshot (39)](https://github.com/user-attachments/assets/99e41ca1-8e08-45d6-801c-153349fd85ba)

![Screenshot (41)](https://github.com/user-attachments/assets/b5fa5a18-dd64-4136-80e3-75d62a515bed)

![Screenshot (42)](https://github.com/user-attachments/assets/9e92d1de-1572-4d29-aa54-579ffebeb52a)

![Screenshot (43)](https://github.com/user-attachments/assets/b50f3af5-99e5-4125-94a1-0aef44f49a25)

![Screenshot (44)](https://github.com/user-attachments/assets/883a64cc-16a0-4f75-8e65-8171a821aae1)

![Screenshot (45)](https://github.com/user-attachments/assets/606db8c9-dffc-422f-b02a-c87d460cf3b0)

## Result :

Successfully completed a C program to implement 2D transformation of image.
