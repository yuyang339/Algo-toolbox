```python
def reverse(head)
    prev = None
    while head:
        curr = head
        head = head.next
        curr.next = prev
        prev = curr
    return prev

```

```c++
ListNode * reverse(ListNode * head)
{
    ListNode * prev = nullptr;
    ListNode * curr = head;
    while(curr != nullptr)
    {
        ListNode * tmp = curr->next;
        curr->next = prev;
        prev = curr;
        curr = tmp;
    }
    return prev;
}

```
