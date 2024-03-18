#include <stdio.h>
#include <stdlib.h>

typedef struct card
{
    char ABC;
    int value;
}card;

void sortCard(card Data[], int size)
{
    card temp;
    for(int i = 0; i < size; i++)
    {
        int poin = 0;
        for(int j = 0; j < size - 1; j++)
        {
            if(Data[j].value > Data[j+1].value)
            {
                temp = Data[j];
                Data[j] = Data[j+1];
                Data[j+1] = temp;
            }
            else
            {
                poin++;
            }
        }
        if(poin == (size-1))
        {
            printf("%d", i);
            break;
        }
        printf("PERTUKARAN %d:\n", i+1);
        for(int j = 0; j < size; j++)
        {
            printf("%c ", Data[j].ABC);
        }
        printf("\n");
    }
}

int main()
{
    int n;
    printf("Berapa kartu yang diinginkan: ");
    scanf("%d", &n);
    card deck[n];
    printf("Masukkan baris kartu anda: ");
    for(int i = 0; i < n; i++)
    {
        scanf(" %c", &deck[i].ABC);
    }
    for(int i = 0; i < n; i++)
    {
        deck[i].value = deck[i].ABC - '0';
        if(deck[i].value < 0 || deck[i].value > 9)
        {
            switch(deck[i].ABC)
            {
            case 'J':
                deck[i].value = 11;
                break;
            case 'Q':
                deck[i].value = 12;
                break;
            case 'K':
                deck[i].value = 13;
                break;
            default:
                break;
            }
        }
    }
    sortCard(deck, n);
}

hasil:
Masukkan jumlah kartu: 5
Masukkan nilai kartu: 3 J Q K 7
Swap 1: 3 7 Q K J 
Swap 2: 3 7 J K Q 
Swap 3: 3 7 J Q K 
Jumlah minimal langkah pertukaran: 3




Penjelasan:

Pertama tama progam meminta input jumlah kartu yang di inginkan, lalu di alokasi ke array sesuai dengan jumlah kartu tersebut. Lalu terjadi bubblesort,  Loop terluar berjalan sebanyak elemen dalam array. lalu terjadi pengecekan dan pengurutan.
