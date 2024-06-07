# wiproT
import java.util.Scanner;

public class LongestConsecutiveSequence {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        int n = scanner.nextInt();
        int[] arr = new int[n];
        
        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }
        
        int maxLength = 0;
        int maxStartIndex = -1;
        int currentLength = 1; // At least one element is part of the sequence
        int currentStartIndex = 0;
        
        for (int i = 1; i < n; i++) {
            if (arr[i] == arr[i - 1]) {
                currentLength++;
            } else {
                if (currentLength > maxLength) {
                    maxLength = currentLength;
                    maxStartIndex = currentStartIndex;
                }
                currentLength = 1;
                currentStartIndex = i;
            }
        }
        
        // Final check in case the longest sequence is at the end of the array
        if (currentLength > maxLength) {
            maxLength = currentLength;
            maxStartIndex = currentStartIndex;
        }
        
        System.out.println(maxLength);
        System.out.println(maxStartIndex);
    }
}
