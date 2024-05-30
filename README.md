import java.util.HashMap;
import java.util.Map;

public class CoinChange {
    
    // Array of denominations in Pakistani currency
    static int[] denominations = {5000, 1000, 500, 100, 50, 20, 10, 5, 2, 1};

    // Method to find the minimum number of denominations
    public static Map<Integer, Integer> findMinDenominations(int amount) {
        Map<Integer, Integer> denominationCount = new HashMap<>();
        
        // Iterate through the denominations
        for (int denom : denominations) {
            // Find the number of each denomination needed
            int count = amount / denom;
            if (count > 0) {
                denominationCount.put(denom, count);
                amount -= count * denom;
            }
        }
        return denominationCount;
    }

    public static void main(String[] args) {
        int amount = 1988;
        Map<Integer, Integer> result = findMinDenominations(amount);

        // Print the result
        System.out.println("Minimum denominations for Rs. " + amount + ":");
        for (Map.Entry<Integer, Integer> entry : result.entrySet()) {
            System.out.println("Rs. " + entry.getKey() + ": " + entry.getValue());
        }
    }
}
