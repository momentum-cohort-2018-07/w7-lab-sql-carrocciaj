## SQL Homework

### Find all time Entries

```sql
SELECT *
FROM time_entries;
```
500 results  

### Find developer who joined most Recently

```sql
SELECT *
FROM developers
ORDER BY joined_on DESC
LIMIT 1;
```

ID 34 Dr. Danielle McLaughlin  

### Find Number of projects for each client

```sql
SELECT clients.id, clients.name, projects.client_id
FROM clients JOIN projects ON clients.id = projects.client_id
GROUP BY clients.name;
```

9 rows returned  

### Find all time entries, and show each one's client name next to it

```sql
SELECT time_entries.*, clients.name
FROM clients JOIN projects ON clients.id = projects.client_id
JOIN time_entries ON projects.id = time_entries.project_id;
```

500 rows returned  

### Find all developers in the "Ohio sheep" group.

```sql
SELECT developers.name, groups.name
FROM developers
JOIN group_assignments ON developers.id = group_assignments.developer_id
JOIN groups ON group_assignments.group_id = groups.id
WHERE groups.name = 'Ohio sheep';
```
3 rows  

### Find the total number of hours worked for each client.

```sql
SELECT clients.name, SUM(time_entries.duration) AS total_work_time
FROM time_entries JOIN projects ON time_entries.project_id = projects.id
JOIN clients ON clients.id = projects.client_id
GROUP BY clients.name;
```

9 rows  

### Find the client for whom Mrs. Lupe Schowalter (the developer) has worked the greatest number of hours.

```sql
SELECT developers.name, MAX(time_entries.duration) AS highest_duration_project
from developers JOIN time_entries ON developers.id = time_entries.developer_id
WHERE developers.name = 'Mrs. Lupe Schowalter';
```

1 row 7 hours client-Kuhic-Bartoletti  

### List all client names with their project names (multiple rows for one client is fine). Make sure that clients still show up even if they have no projects.

```sql
SELECT clients.name, projects.name
FROM clients LEFT JOIN  projects ON clients.id = projects.client_id;
```

33 rows  

### Find all developers who have written no comments.

```sql
SELECT developers.name, comments.comment
FROM developers LEFT JOIN  comments ON developers.id = comments.developer_id
Where comments.comment IS null;
```
13 rows
