# LeetCode 1857. Largest Color Value in a Directed Graph

## Problem

There is a directed graph of n colored nodes and m edges. The nodes are numbered from 0 to n - 1.

You are given a string colors where colors[i] is a lowercase English letter representing the color of the ith node in this graph (0-indexed). You are also given a 2D array edges where edges[j] = [aj, bj] indicates that there is a directed edge from node aj to node bj.

A valid path in the graph is a sequence of nodes x1 -> x2 -> x3 -> ... -> xk such that there is a directed edge from xi to xi+1 for every 1 <= i < k. The color value of the path is the number of nodes that are colored the most frequently occurring color along that path.

Return the largest color value of any valid path in the given graph, or -1 if the graph contains a cycle.

```java
class Solution {
public:
    bool backspaceCompare(string s, string t) {
        stack<char> st1, st2;

        for (char c : s) {
            if (c == '#' && !st1.empty()) {
                st1.pop();
            } else if (c != '#') {
                st1.push(c);
            }
        }

        for (char c : t) {
            if (c == '#' && !st2.empty()) {
                st2.pop();
            } else if (c != '#') {
                st2.push(c);
            }
        }

        while (!st1.empty() && !st2.empty()) {
            if (st1.top() != st2.top()) {
                return false;
            }
            st1.pop();
            st2.pop();
        }

        return st1.empty() && st2.empty();
    }
};
```

## Link

[LeetCode](https://leetcode.com/ndivyansh29/)
