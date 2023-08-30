# Confirmation-Rate
## Problem Link :
[Confirmation Rate](https://leetcode.com/problems/confirmation-rate/description/?envType=study-plan-v2&envId=top-sql-50)
## Solution
```sql
SELECT s.user_id,
       ROUND(
           AVG(
               CASE 
                   WHEN c.action = 'confirmed' THEN 1.00
                   WHEN s.time_stamp IS NULL THEN 0.00
                   ELSE 0
               END
           ),
           2
       ) AS confirmation_rate
FROM signups s
LEFT JOIN confirmations c ON c.user_id = s.user_id
GROUP BY s.user_id;

