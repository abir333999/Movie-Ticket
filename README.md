#include <stdio.h>

#define ROWS 5
#define COLS 10

int seats[ROWS][COLS];

void initializeSeats() {
    for(int i=0;i<ROWS;i++) {
        for(int j=0;j<COLS;j++) {
            seats[i][j]=0;
        }
    }
}

void displaySeats() {
    printf("\nSeat Layout:\n\n   ");

    for(int i=1;i<=COLS;i++)
        printf("%2d ",i);

    printf("\n");

    for(int i=0;i<ROWS;i++) {
        printf("%2d ",i+1);
        for(int j=0;j<COLS;j++) {
            if(seats[i][j]==0)
                printf(" O ");
            else
                printf(" X ");
        }
        printf("\n");
    }

    printf("\nO = Available | X = Sold\n");
}

void buyTicket() {
    int row,col;

    printf("Enter Row (1-%d): ",ROWS);
    scanf("%d",&row);

    printf("Enter Column (1-%d): ",COLS);
    scanf("%d",&col);

    if(row<1 || row>ROWS || col<1 || col>COLS) {
        printf("Invalid seat number!\n");
        return;
    }

    if(seats[row-1][col-1]==1) {
        printf("Seat already sold!\n");
    }
    else {
        seats[row-1][col-1]=1;
        printf("Ticket booked successfully!\n");
    }
}

void showStatistics() {
    int sold=0;

    for(int i=0;i<ROWS;i++) {
        for(int j=0;j<COLS;j++) {
            if(seats[i][j]==1)
                sold++;
        }
    }

    int total=ROWS*COLS;
    int available=total-sold;

    printf("\nTotal Seats: %d\n",total);
    printf("Sold Seats: %d\n",sold);
    printf("Available Seats: %d\n",available);
}

int main() {

    int choice;

    initializeSeats();

    while(1) {


    printf("\t\t\t\t\tM-O-V-I-E---T-I-C-K-E-T---M-A-N-A-G-E-M-E-N-T\n\t\t\t\t\t---------------------------------------------\n\t\t\t\t\t\t\t\t\t\t\t\t\tABIR\n\n");
        printf("1. Display Seats\n");
        printf("2. Buy Ticket\n");
        printf("3. Show Statistics\n");
        printf("4. Exit\n");
        printf("Enter choice: ");

        scanf("%d",&choice);

        switch(choice) {

            case 1:
                displaySeats();
                break;

            case 2:
                buyTicket();
                break;

            case 3:
                showStatistics();
                break;

            case 4:
                printf("Thank you!\n");
                return 0;

            default:
                printf("Invalid choice!\n");
        }
    }
    return 0;
}
