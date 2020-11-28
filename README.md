# test

//algo 1 :


import java.util.Arrays;

class Solution {
    public int[] solution(int N, int[] A) {

        final int condition = N + 1;
        int currentMax = 0;
        int countersArray[] = new int[N];

        for (int iii = 0; iii < A.length; iii++) {
            int currentValue = A[iii];
            if (currentValue == condition) {
                Arrays.fill(countersArray, currentMax);
            } else {
                int position = currentValue - 1;
                int localValue = countersArray[position] + 1;
                countersArray[position] = localValue;

                if (localValue > currentMax) {
                    currentMax = localValue;
                }
            }

        }

        return countersArray;
    }
}

//Algo 2 :
 
public class Ladder {
	    public int[] solution(int[] a, int[] b) {
	        final int[] cn = new int[a.length < 2 ? 2 : a.length];
	        cn[0] = 1;
	        cn[1] = 2;
	      
	        for (int i = 2; i < a.length; i++) {
	           
	            cn[i] = (cn[i - 1] + cn[i - 2]) & ((1 << 30) - 1);
	        }
	        for (int i = 0; i < a.length; i++) {
	            a[i] = cn[a[i] - 1] & ((1 << b[i]) - 1);
	        }
	        return a;
	    }
	}
    
  //Algo 3 :
  
public class MinAbsSum {
	    public int solution(int[] a) {
	        if (a.length == 0) {
	            return 0;
	        }
	        int sum = 0;
	        int max = Integer.MIN_VALUE;
	        
	        for (int i = 0; i < a.length; i++) {
	            final int value = Math.abs(a[i]);
	            sum += value;
	            if (max < value) {
	                max = value;
	            }
	            a[i] = value;
	        }
	        
	        final int[] counts = new int[max + 1];
	        for (int value: a) {
	            counts[value]++;
	        }
	       
	        final int[] r = new int[sum + 1];
	        for (int i = 1; i < r.length; i++) {
	            r[i] = -1;
	        }
	      
	        for (int i = 1; i < counts.length; i++) {
	           
	            for (int j = 0; j < r.length; j++) {
	                
	                if (r[j] >= 0) {
	                    r[j] = counts[i];
	                } else if (j - i >= 0 && r[j - i] > 0) {
	                    r[j] = r[j - i] - 1;
	                }
	                
	            }
	        }
	        int result = sum;
	       
	        for (int i = 0; i < r.length / 2 + 1; i++) {
	            if (r[i] >= 0 && result > Math.abs(sum - 2 * i)) {
	                result = Math.abs(sum - 2 * i);
	            }
	        }
	        return result;
	    }
	}


