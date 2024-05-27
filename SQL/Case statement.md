```sql
select
    case
        when grades.grade >= 8
        then students.name
        else NULL
    end as name,
    grades.grade,
    Students.marks
from Students
join grades on Students.marks >= grades.min_mark and Students.marks <= grades.max_mark
order by grades.grade desc, students.name;
```
