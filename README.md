1) SELECT * FROM groups WHERE mountain_id IN (SELECT id FROM mountains WHERE name = ?) ORDER BY start_date, end_date

2) INSERT INTO mountains (name, height, country, region) VALUES (?,?,?,?)

3) UPDATE mountains SET name = ?, height = ?, country = ?, region = ? WHERE id = ? AND id NOT IN (SELECT DISTINCT mountain_id FROM groups)

4) SELECT DISTINCT c.* FROM groups g 
JOIN group_climbers gc ON g.id = gc.group_id 
JOIN climbers c ON gc.climber_id = c.id 
WHERE start_date BETWEEN ? AND ? AND BETWEEN ? AND ?

5) INSERT INTO climbers VALUES ( name = ?, address = ?) 
INSERT INTO group_climbers VALUES ( group_id = ?, climber_id = ?)

6) SELECT m.name, c.name, count(*) FROM mountains m
JOIN groups g ON m.id = g.mountain_id
JOIN group_climbers gc ON g.id = gc.group_id
JOIN climbers c ON c.id = gc.climber_id
GROUP BY m.name, c.name

7) SELECT * FROM groups WHERE start_date BETWEEN ? AND ? AND end_date BETWEEN ? AND ?

8) INSERT INTO groups (name, mountain_id, start_date) VALUES (?, (SELECT id FROM mountains WHERE name = ?), ?)

9) SELECT m.name, count(DISTINCT c.id) FROM mountains m
JOIN groups g ON m.id = g.mountain_id
JOIN group_climbers gc ON g.id = gc.group_id
JOIN climbers c ON c.id = gc.climber_id
GROUP BY m.name
