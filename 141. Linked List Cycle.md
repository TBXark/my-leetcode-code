# 141. Linked List Cycle

### 2017-03-23

Given a linked list, determine if it has a cycle in it.

Follow up:
Can you solve it without using extra space?



# Solution

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool hasCycle(ListNode *head) {
			if(head == NULL) { return false; } 
			ListNode *a = head;
			ListNode *b = head;
			while (b->next != NULL &&  b->next->next != NULL) {
				a = a->next;
				b = b->next->next;
				if (a == b) { return true;}
			}
			return false;
    }
};
```

