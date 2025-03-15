---
layout: post
title: Database Performance and Modernisation Guide
categories: [Application Modernization, Database Performance]
paginate: true
summary: Performance issues in old databases are inevitable. With proper query optimization, indexing, resolving data type mismatches, and modernization strategies, long-term solutions can be achieved. Database improvement is a continuous process.
---

Lately, I've been examining how databases older than even the youngest member of our team encounter performance issues with modern applications, and I'm working on solving these problems. While we carefully ensure that our code and project folder structures are self-explanatory, it's genuinely disappointing that naming conventions for tables and fields in the database remain neglected.

When starting a new application project, I've repeatedly worked hard and shared my experiences to ensure the solution is as close to perfect as possible. Yet, no one seems concerned about the project's state ten years from now. From a realistic perspective, this may seem understandable, but I've also witnessed initial solutions becoming unnecessarily complex (over-engineered) over time. Throughout the years, I've learnt that the best solutions are always the simplest and most practical ones, regardless of when they're implemented.

When the application becomes one of the organisation's most established systems, performance and modernisation discussions about various project stages start taking place in crowded meeting rooms. Usually, the initial improvements are achieved through performance optimisations made at the database level.

At this stage, we need to conduct a thorough review and research to identify critical points. However, nothing can replace the importance of preparing a roadmap before getting started. Having worked on similar projects before, I will share the key checkpoints you should consider along the way.

## Stations

1. Based on the application database users, it is necessary to identify queries with long execution times in the database query log information. At this stage, DMV (Dynamic Management Views) can be used, and tables starting with 'sys.dm_exec_*' can be utilised.

2. The identified queries should undergo structural analysis. In particular, the necessity of using 'UNION' should be reviewed, and it should be examined whether there are built-in or user-defined functions within 'SELECT ...' statements. Such usages may cause unnecessary performance losses.

3. After identifying the queries, we should focus on the 'Query Optimisation' and 'Query Execution Plan Selection' processes. At this stage, query costs should be carefully evaluated, and new decisions should be made for 'JOIN' and 'UNION' operations. Additionally, unnecessary 'WHERE Clause' statements should be removed for better functionality, and it should be ensured that the appropriate indexes are defined.

4. During the query analysis phase, there is a common yet often overlooked issue that the database silently handles for us, which can be defined as 'Type Mismatch.' This issue frequently arises in scenarios such as the following: For example, when examining the records of a field, you see numerical values and assume that it is an 'INTEGER' field while writing a query with a 'WHERE Clause.' However, you may not realise that this field is defined as 'VARCHAR(1).' Similarly, a developer might have chosen to use 'VARCHAR(11)' to store date and time information in a table field. If you attempt to use 'DATETIME' in your query, the database might either save you by performing an automatic conversion or force you to spend hours trying to figure out the source of the error.

5. If data sets are frequently accessed, a 'Materialised View' can provide caching support. However, view objects may not perform more efficiently than a query using the correct indexes. Additionally, the underlying tables will still be accessed every time a query is executed.

6. Although most modern applications use ORM (Object-Relational Mapping) tools for database operations, 'Stored Procedures' are still utilised for complex, long-running tasks that require close interaction with data, depending on the requirements. It is essential to analyse the queries written within these objects with a 'Query Optimisation' and 'Query Execution Plan Selection' perspective.

7. The trigger is the most critical database object in database conversion or performance improvement processes. It is often overlooked and can unexpectedly remind you of its presence through small surprises after your modifications. If you want to feel lucky during this process, you should ensure that Trigger objects do not contain logic that deeply affects business rules.

8. Another important step in database optimisation is analysing the tables based on query peak times. It is essential to ensure that statistics are collected in a planned manner and that operations such as 'Index Rebuild,' 'Index Reorganise,' and 'Update Statistics' are performed regularly.

9. It should be determined whether the database or tables must undergo 'Partitioning.' When working with large data sets, using 'partitioning' can significantly improve query performance and enhance the system's scalability.

10. Various discussions can be held to achieve database-driven performance improvements, but reducing the use of the 'Linked Server' can provide the most significant gains. This is because network latency, performance issues on the remote system that you have no control over, and data type conversions between two systems can lead to highly costly performance losses.

## Conclusion

Database performance and modernisation efforts are not one-time tasks but continuous improvement processes. A solution that initially appears perfect may become inadequate over time due to changing business requirements and increasing data volume. Therefore, making the right design decisions early on can help avoid significant costs in the long run.

Remember, database optimisation requires learning from past mistakes.


