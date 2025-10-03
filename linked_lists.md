# List Manipulation (Манипуляция связными списками) с удалением

## Dummy Head / Sentinel Node

Идея: Создать временный узел (sentinel), который будет предшествовать исходной голове списка. Это гарантирует, что у каждого узла в списке
(включая оригинальную голову) есть "предыдущий" узел, что унифицирует логику удаления.

<details>
  <summary>Пример:</summary>

Задача:
  Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val == val, and return the new head.

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 * int val;
 * ListNode *next;
 * ListNode() : val(0), next(nullptr) {}
 * ListNode(int x) : val(x), next(nullptr) {}
 * ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        // 1. Создаем фиктивный узел (Sentinel Node), который предшествует голове.
        // Это позволяет унифицировать обработку удаления головы, 
        // так как теперь у головы всегда есть "предыдущий" узел.
        ListNode sentinel(0, head); 
        
        // Указатель на предыдущий элемент, начинается с фиктивного узла.
        ListNode* prev = &sentinel;
        
        // Указатель на текущий элемент.
        ListNode* curr = head;

        // 2. Проходим по списку
        while (curr != nullptr) {
            
            if (curr->val == val) {
                // Если нужно удалить:
                // Переназначаем next у prev, перескакивая через curr.
                prev->next = curr->next;
                
                // Освобождаем память удаляемого узла
                delete curr; 
                
                // Перемещаем curr вперед, чтобы проверить следующий узел
                // (prev остается на месте, ожидая, что curr->next тоже может быть удален)
                curr = prev->next;
            } else {
                // Если не нужно удалять:
                // Двигаем оба указателя вперед.
                prev = curr;
                curr = curr->next;
            }
        }

        // 3. Возвращаем голову списка, которая теперь находится после фиктивного узла.
        // SentinelNode.next указывает на первый неудаленный элемент.
        return sentinel.next;
    }
};
```
  
</details>


