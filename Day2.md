# Day 2 Notes

## 1. EF Core 2.0

### Context Pooling. 

![context pooling diagram](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/dbcontext_pooling.png)

Before the context was created per request. Now with context polling the context is served by the pool. We still have 
Connection pooling. Context has a lot of dependencies that it has to load and that slows it down when done per request.
Context Pooling is not by default, it's considered more like Advanced state.

To get to pooling functionality we need to change from `AddDbContext<T>` to `AddDbContextPool<T>`.

![change to context pool](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/add_dbcontext_pool.png)

### Explicit compiled query

Explicittly compiled queries are compiled the first time and cached and then any other time they are used, they are much fatser that regular queries.
EF class has some static entry points.
![explicitly compiled query](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/explicit_compiled_query.png)

### Owned types

![owned types example](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/owned_types_1.png)

If we have `Work Address` and `Physical Address` and we make them as pwned type they get added as a prefixed column name at the parent table

![owned types result table](https://github.com/lekova/dotnetconf2017-notes/blob/master/images/prefixed_column_names.png)

We can also mapped them in the same table. Owned types can be nested. Restriction is that only the parent can point to owned type

### Filters

Interpolated string queries. There is a naive interpolation where even if you put the sql query in a local variable there is still a chance of sql ingection. However if the query is inside of the FromSql method it gets parametrized!


### EF Links 
+ Docs https://docs.microsoft.com/ef/core
+ Project https://github.com/aspnet/EntityFrameworkCore
+ Blog https://blogs.msdn.com/dotnet
+ Demos https://github.com/anpete/efdemos
