#include <stdio.h>
#include <stdlib.h>


void merge(int array[], int p, int q, int r){
    int n1 = q-p+1;
    int n2 = r-q;
    int L[n1+1], R[n2+1];//+1 for sentinels.

    for(int i = 0; i < n1; i++){
        L[i] = array[p+i];
    }
    for(int j = 0; j < n2; j++){
        R[j] = array[q+1+j];
    }

    L[n1] = 99999;
    R[n2] = 99999;
    int i = 0;
    int j = 0;
    int k = p;
    for(k; k <= r; k++){
        if(L[i]<=R[j]){
            array[k] = L[i];
            i++;
        }else{
            array[k] = R[j];
            j++;
        }
    }
}

void mergeSort(int array[], int p, int r){
    if(p<r){

        int q = (p+r)/2;

        mergeSort(array, p, q);
        mergeSort(array, q+1, r);
        merge(array, p, q, r);

        for(int i = 0; i<=r;i++){
            printf("%d_", array[i]);
        }
        printf("\n");
    }
}


int main()
{
    ///---------------GETTING INPUT AND PUTTING IT INTO ARRAY-----------------
    FILE *input;
    char fileName[50];
    int data = 0;
    int dataArrayLength = 0;

    printf("Enter the data file (abc.txt): ");
    scanf("%s", fileName);
    input = fopen(fileName,"r");
    int r = 0;

    for(fscanf(input,"%d", &data);!feof(input);fscanf(input,"%d", &data)){
        dataArrayLength++;
    }
    dataArrayLength++;

    fseek(input, 0, SEEK_SET);//Move the cursor (,,x) beginning of the file and move (,x,)0 byte from the file (x,,) input.
    int dataArray[dataArrayLength];
    int length = dataArrayLength;

    for(fscanf(input,"%d", &data);!feof(input);fscanf(input,"%d", &data)){
        dataArray[dataArrayLength-length] = data;
        length--;
    }
    fscanf(input,"%d", &data);
    dataArray[dataArrayLength-length] = data;

    printf("sizeofArray is %d\n ", sizeof(dataArray));
    printf("-----OLD------\n");
    for(int i = 0; i< dataArrayLength; i++){
        printf("%d_", dataArray[i]);
    }
    printf("\n-----NEW------\n");
    ///--------------------------------------------------------------------
    mergeSort(dataArray, 0, dataArrayLength-1);

    for(int i = 0; i< dataArrayLength; i++){
        printf("%d*", dataArray[i]);
    }
    printf("\n----------------\n");

    return 0;
}
