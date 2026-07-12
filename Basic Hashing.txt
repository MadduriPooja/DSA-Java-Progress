class Solution {
    public List<List<Integer>> countFrequencies(int[] nums) {
        Map<Integer, Integer> map = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            int currentNumber = nums[i];

            if (map.containsKey(currentNumber)) {
                int oldCount = map.get(currentNumber);
                map.put(currentNumber, oldCount + 1);
            } else {
                map.put(currentNumber, 1);
            }
        }

        List<List<Integer>> result = new ArrayList<>();
        
        for (int uniqueNumber : map.keySet()) {
            int itsFrequency = map.get(uniqueNumber);

            List<Integer> pair = new ArrayList<>();
            pair.add(uniqueNumber);
            pair.add(itsFrequency);

            result.add(pair);
        }

        return result;
    }
}


class Solution {
    public int mostFrequentElement(int[] nums) {
        Map<Integer, Integer> freqMap = new HashMap<>();
        int maxCount = 0, result = Integer.MAX_VALUE;

        // 1. One-line Hashing loop
        for (int num : nums) {
            freqMap.put(num, freqMap.getOrDefault(num, 0) + 1);
        }

        // 2. Find the winner efficiently
        for (var entry : freqMap.entrySet()) {
            int element = entry.getKey(), count = entry.getValue();
            
            if (count > maxCount || (count == maxCount && element < result)) {
                maxCount = count;
                result = element;
            }
        }

        return result;
    }
}

