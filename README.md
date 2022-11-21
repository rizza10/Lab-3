# Lab-3
Laboratory 3 - DSA
/* Manalo, Rizza Mae S.           3101
20-03800                          11/21/22

                    Lab 3 - Case 1
*/ 

class Main {  
  
int getMax(int[] a, int n) {  
  int max = a[0];  
  for(int i = 1; i<n; i++) {  
      if(a[i] > max)  
         max = a[i];  
  }  
  return max; //maximum element from the array  
}  
  
void countSort(int[] a, int n) // function to perform counting sort  
{  
    Main c = new Main();
    int[] dup_array = new int [n+1];
   int[] output = new int [n+1];  
   int max = getMax(a, n);  
   //int max = 42;  
   int[] count = new int [max+1]; //create count array with size [max+1]  
  
  for (int i = 0; i <= max; ++i)   
  {  
    count[i] = 0; // Initialize count array with all zeros  
  }
  

  for (int i = 0; i < n; i++) // Store the count of each element  
  {  
    count[a[i]]++;
    dup_array[i] = count[a[i]];
  }

  
   for(int i = 1; i<=max; i++)   
      count[i] += count[i-1]; //find cumulative frequency  
      
  /* This loop will find the index of each element of the original array in  
 
count array, and 
   place the elements in output array*/  
  for (int i = n - 1; i >= 0; i--) {  
    output[count[a[i]] - 1] = a[i];  
    count[a[i]]--; // decrease count for same numbers  
}  
  
   for(int i = 0; i<n; i++) {
      a[i] = output[i]; //store the sorted elements into main array  
   }
   
   //For the Checking if there are repeated elements
   Boolean dup = false;
   
   for (int i=0; i<a.length; i++) {
            if(dup_array[i] != 1) {
                dup = true;
            }
       }
        
   if (dup == true) { // If there are repeated elements, print them in columns
       System.out.println("\n\nOutput:");
        int nn = 0;
        for (int i = 0; i < a.length; i++)
  {
    if (a[i] == nn) {
        System.out.print("      " + a[i]);

    } else {
        System.out.print("    \n" + a[i]);
    }
    nn = a[i];
  }

   }
  else {
       System.out.println("\n\nNo repeated elements");
   }
}  


/* Function to print the array elements */  
void printArray(int a[], int n)  
{  
    int i;  
    for (i = 0; i < n; i++)  {
        System.out.print(a[i] + " "); 
}  
}
public static void main(String args[])  
{  
    int a[] = {2,1,3,4,5,5,4,3,2,1};  
    int n = a.length;  
    Main c1 = new Main();  
    System.out.println("Case 1: ");  
    c1.printArray(a, n);  
    c1.countSort(a,n);
    System.out.println("\n\nSorted Array: ");
    c1.printArray(a, n); 
}  
}

// end of program
