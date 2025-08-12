# Data_Structures

## Count number of nodes in Complete Binary tree

```

int maxWidth(Node root) {

    if(root == null) return 0;

    Queue<Pair> queue = new LinkedList<>();

    queue.offer(new Pair(root, 0));

    int maxWidth = 0;

    while(!queue.isEmpty()){

        int size = queue.size();

        int firstIndex = 0, lastIndex = 0;

        int minIndex = queue.peek().index;

        for(int i = 0; i < size; i++){

            Pair pair = queue.poll();

            int currIndex = pair.index - minIndex;

            Node node = pair.node;

            if(i == 0) firstIndex = currIndex;

            if(i == size - 1) lastIndex = currIndex;

            if(node.left != null) queue.offer(new Pair(node.left, 2 * currIndex + 1));

            if(node.right != null) queue.offer(new Pair(node.right, 2 * currIndex + 2));

        }

        maxWidth = Math.max(maxWidth, lastIndex - firstIndex + 1);

    }

    return maxWidth;

}
## Minimum window substring
