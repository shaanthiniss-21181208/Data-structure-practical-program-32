class Solution {
  public:
    void removeLoop(Node* head) {
        if(head == NULL || head->next == NULL)
            return;

        Node* slow = head;
        Node* fast = head;

        // Detect loop
        while(fast && fast->next){
            slow = slow->next;
            fast = fast->next->next;

            if(slow == fast)
                break;
        }

        // No loop
        if(slow != fast)
            return;

        slow = head;

        // Find node before loop start
        if(slow == fast){
            while(fast->next != slow)
                fast = fast->next;
        }
        else{
            while(slow->next != fast->next){
                slow = slow->next;
                fast = fast->next;
            }
        }

        // Remove loop
        fast->next = NULL;
    }
};# Data-structure-practical-program-32
