1.#Get the Second Highest Salary from the Record.

Approach 1:

SELECT MAX (SALARY) AS Second_Highest_Salary from EmployeeSal WHERE SALARY NOT IN
(SELECT MAX (SALARY)from EmployeeSal );

Approach 2:
WITH CTE AS
(SELECT TOP 2 * from  EmployeeSal order BY SALARY DESC)
SELECT TOP 1 SALARY FROM CTE ORDER BY SALARY ASC;

Approach 3:
WITH CTE AS
(SELECT ROW_NUMBER() OVER (order BY SALARY DESC) as NEW_EMP_ID,EMP_ID,SALARY from EmployeeSal)
SELECT SALARY FROM CTE WHERE  NEW_EMP_ID=2 ;

