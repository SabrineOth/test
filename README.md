# test

#algo 1


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
