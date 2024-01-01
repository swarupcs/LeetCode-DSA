## 445. Add Two Numbers II



https://leetcode.com/problems/add-two-numbers-ii/

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.



#### Example 1:
```
(./addtwonumbersII.jpg)
Input: l1 = [7,2,4,3], l2 = [5,6,4]
Output: [7,8,0,7]
```

#### Example 2:
```
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [8,0,7]
```
#### Example 3:
```
Input: l1 = [0], l2 = [0]
Output: [0]
```

#### Constraints:
```
The number of nodes in each linked list is in the range [1, 100].
0 <= Node.val <= 9
It is guaranteed that the list represents a number that does not have leading zeros.
```

## Solutions

* **Java**

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
         ListNode n1 = reverse(l1), n2 = reverse(l2);
        int carry = 0;
        ListNode temp = n1, pre = n1;
        while((n1 != null) || (n2 != null) || (carry !=0)){
            int v1 = n1 == null? 0 : n1.val;
            int v2 = n2 == null? 0 : n2.val;

            if(n1 == null){
                n1 = new ListNode((v1 + v2 + carry)%10);
                pre.next = n1;
            }
            else {
                n1.val = (v1 + v2 + carry)%10;
            }
            carry = (v1 + v2 + carry) /10;
            pre = n1;
            n1 = n1 == null? null : n1.next;
            n2 = n2 == null? null : n2.next;
        }

        return reverse(temp);

    }
    private ListNode reverse(ListNode l1){
        ListNode cur = l1.next;
        ListNode pre = l1;
        pre.next = null;
        while(cur!= null){
            ListNode next = cur.next;
            cur.next = pre;
            pre = cur;
            cur = next;
        }
        return pre;
    }
    
}
```