class NumArray {
    int n;
    int[] segTree = null;
    int[] arr = null;

    private void buildSegmentTree(int i, int left, int right){
        
        if(left == right){
            segTree[i] = arr[left];
            return;
        }

        int mid = left + (right - left)/2;

        //build left subtree
        buildSegmentTree(2 * i + 1, left, mid);
        //build right subtree
        buildSegmentTree(2 * i + 2, mid + 1, right);

        segTree[i] = segTree[2 * i + 1] + segTree[2 * i + 2];

        
    }

    private int rangeSum(int i, int start, int end, int left, int right){

        if(start > right || end < left){ // out of range of currNode
            return 0;
        }

        if(left >= start && right <= end){ // inside range of currNode
            return segTree[i];
        }

        int mid = left + (right - left)/2;
        return rangeSum(2 * i + 1, start, end, left, mid) + 
               rangeSum(2 * i + 2, start, end, mid + 1, right);
    }

    private void updateSegTree(int i, int idx, int val, int left, int right){
        
        if(left == right){
            arr[idx] = val;
            segTree[i] = val;
            return;
        }

        int mid = left + (right - left)/2;
        if(idx <= mid){
            updateSegTree(2 * i + 1, idx, val, left, mid);
        }
        else{
            updateSegTree(2 * i + 2, idx, val, mid + 1, right);
        }

        segTree[i] = segTree[2 * i + 1] + segTree[2 * i + 2];
    }

    public NumArray(int[] nums) {
        n = nums.length;
        arr = nums;
        segTree = new int[4 * n];

        buildSegmentTree(0, 0, n - 1);

    }
    
    public void update(int index, int val) {
        updateSegTree(0, index, val, 0, n - 1);
    }
    
    public int sumRange(int left, int right) {
        return rangeSum(0, left, right, 0, n - 1);
    }
}

/**
 * Your NumArray object will be instantiated and called as such:
 * NumArray obj = new NumArray(nums);
 * obj.update(index,val);
 * int param_2 = obj.sumRange(left,right);
 */
