import java.util.Random;
import java.lang.Math;
import java.util.concurrent.TimeUnit;
public class CS435_HW2 {
    public static int compCount= 0;
    
    private static int[] randNumber(int n) {
        Random rand = new Random();
        int arr[] = new int[n];
        for(int i = 0;i<n;i++) {
            arr[i] = rand.nextInt(n)+1;
        }
        return arr;
    }
    private static void line() {
        System.out.println();
    }
    private static boolean compare(int x, int y){
        compCount++;
        if(x>y) {
            return true;
        } 
        return false;
    }
    //********************************* MergeSort **************************************
    private static void merge(int [] arr, int [] l, int [] r, int left, int right) {
        int i =0, j=0, k=0;
        while(i<left && j<right) {
            if(l[i]  <= r[j]) {
                compare(i,j);
                arr[k++] = l[i++];
            }
            else {
                arr[k++] = r[j++];
            }
        }
        while(i<left) {
            compare(i,j);
            arr[k++] = l[i++];
        }
        while(j< right) {
            compare(i,j);
            arr[k++] = r[j++];
        }
    }
    private static void mSort(int [] arr, int n) {
        if(n<2) {
            compare(n,2);
            return;
        }
        int mid = n/2;
        int[] l = new int[mid];
        int[] r = new int[n-mid];
        for(int i = 0; i<mid; i++) {
            l[i] = arr[i];
        }
        for(int i =mid; i<n; i++) {
            r[i-mid] = arr[i];
        }
        mSort(l,mid);
        mSort(r,n-mid);
        
        merge(arr,l,r,mid,n-mid);
    }
    //**************************** HeapSort ********************************************

    private static void heapify(int arr[], int n, int i) {
        int largest = i;
        int l = 2 * i + 1;
        int r = 2 * i + 2;
        if (l < n && arr[l] > arr[largest]) {
            compare(n,l);
            largest = l;
        }
        if (r < n && arr[r] > arr[largest]) {
            compare(n,l);
            largest = r;
        }
        if (largest != i) {
            compare(n,l);
            int swap = arr[i];
            arr[i] = arr[largest];
            arr[largest] = swap;
  
            heapify(arr, n, largest);
        }
    }

    private static void hSort(int arr[], int n) {
        for(int i = n/2 - 1; i>=0; i--) {
            heapify(arr, n, i);
        }
        for(int i = n - 1;i>= 0; i--) {
            int temp = arr[0];
            arr[0] = arr[i];
            arr[i] = temp;

            heapify(arr, i, 0);
        }
    }

    //**************************** QuickSort *******************************************
    private static int partition(int arr[], int low, int high) {
        int pivot = arr[high];
        int i = (low-1);
        for(int j=low; j<high; j++) {
            if(arr[j] <= pivot) {
                compare(j,pivot);
                i++;

                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp; 
            }
        }
        int temp = arr[i+1];
        arr[i+1] = arr[high];
        arr[high] = temp;

        return(i+1);

    }
    private static void qSort(int arr[], int low, int high) {
        if(low < high) {
            compare(high,low);
            int pi = partition(arr,low,high);
            qSort(arr,low,pi-1);
            qSort(arr,pi+1,high);
        }
    }
    private static void printArr(int arr[]) {
        int n = arr.length;
        for(int i = 0; i<n; i++) {
            System.out.print("" + arr[i] + " ");
        }
        line();
    }
    private static void reverse(int arr[], int n) {
        int j = n;
        int[] rev = new int[n];
        for(int i = 0; i< n; i++) {
            rev[j-1] = arr[i];
            j--;
        }
        for(int k = 0; k<n; k++) {
            System.out.print(rev[k] + " ");
        }
        line();
    }

    public static void main(String[] arg) {
        int listofNum = 32;
        long startTime = System.nanoTime();
        //int listofNum = (int)Math.pow(2,10);
        //int listofNum = (int)Math.pow(2,15);
        //int listofNum = (int)Math.pow(2,20);
        //random numbers for array
        int[] A = randNumber(listofNum);
        line();
        System.out.println("List: ");
        for(int i = 0; i< A.length; i++) {
            System.out.print(A[i] + " ");
        }
        line();
        line();
        System.out.print("Sorted List: " );
        line();
        int n = A.length;
        //Quicksort
        //qSort(A, 0, n-1);
        //Mergesort
        //mSort(A, n);
        //Heapsort
        hSort(A, n);
        printArr(A);
        line();
        System.out.print("Reversed List: " );
        line();
        reverse(A,n);
        long endTime = System.nanoTime();
        //Average Case
        int avgCase = (listofNum * listofNum) -listofNum / 4;
        //Worst Case
        int worstCase = (listofNum * listofNum) -listofNum /2;

        long timeElapsed = endTime - startTime;


        System.out.println("Comparisons = " + compCount); 
        System.out.println("Execution time in nanoseconds: " + timeElapsed);
        System.out.println("Execution time in milliseconds: " + timeElapsed / 1000000);
        System.out.println("Average Case = " + avgCase);
        System.out.println("Worst Case = " + worstCase);

    }


}
