# Top-K-Frequent-Elements
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
         Map<Integer, Integer> frequencyMap = new HashMap<>();
        for (int num : nums) {
            frequencyMap.put(num, frequencyMap.getOrDefault(num, 0) + 1);
        }
        PriorityQueue<Map.Entry<Integer, Integer>> minHeap = new PriorityQueue<>(Comparator.comparingInt(Map.Entry::getValue));
        for (Map.Entry<Integer, Integer> entry : frequencyMap.entrySet()){
            minHeap.add(entry);
            if (minHeap.size() > k){
                minHeap.poll();
            }
        }

        List<Integer> result = new ArrayList<>();
        while (!minHeap.isEmpty()) {
            result.add(minHeap.poll().getKey());
        }

        int[] resultArray = new int[result.size()];
        for (int i = 0; i < result.size(); i++){
            resultArray[i] = result.get(i);
        }

        return resultArray;
    }
}
