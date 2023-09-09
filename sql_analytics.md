## Creating a new database

```sql

create database hr_data;

```

## Table Structure and records

```sql

select * from hr_data.hr;

```

## Total Records

```sql

select count(1) as total_records from hr_data.hr;

```


## Total males and females in the company

```sql

select sum(case when gender = 'Female' then 1 else 0 end)  as total_females  ,
sum(case when gender = 'Male' then 1 else 0 end ) as total_males from hr_data.hr;

```

## Attrition % and Total Attrition by Gender in the company

```sql

SELECT Gender, 
       COUNT(*) AS TotalEmployees,
       SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) AS AttritionCount,
       Round(SUM(CASE WHEN Attrition = 'Yes' THEN 1 ELSE 0 END) / COUNT(*),2) * 100 AS AttritionRate
FROM hr_data.hr
GROUP BY Gender;

```

## Education Feild with most number of Attrition 

```sql

SELECT `Education Field`, COUNT(*) AS AttritionCount
FROM hr_data.hr
WHERE Attrition = 'Yes'
GROUP BY `Education Field`
order by AttritionCount desc limit 1;

```

## Department Wise Attrition & Most 

```sql

SELECT Department, COUNT(*) AS AttritionCount
FROM hr_data.hr
WHERE Attrition = 'Yes'
GROUP BY Department
order by AttritionCount desc ;


```

## Department with most Attritions 

```sql

SELECT Department, COUNT(*) AS AttritionCount
FROM hr_data.hr
WHERE Attrition = 'Yes'
GROUP BY Department
order by AttritionCount desc limit 1 ;

```


## Average age of an employee working in the company

```sql

select  Round(Avg(Age),0) as average_age_of_employee from hr_data.hr ;

```

## Top 3 Job roles with the most Job Satification 

```sql

select `Job Role` , count(`Job Satisfaction`) as rating from hr_data.hr where `Job Satisfaction` = 4  group by `Job Role` 
order by rating desc limit 3;

```
