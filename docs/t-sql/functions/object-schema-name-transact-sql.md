---
title: "OBJECT_SCHEMA_NAME (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OBJECT_SCHEMA_NAME
- OBJECT_SCHEMA_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], names
- schemas [SQL Server], names
- displaying schema names
- database objects [SQL Server], names
- OBJECT_SCHEMA_NAME function
ms.assetid: 5ba90bb9-d045-4164-963e-e9e96c0b1e8b
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 621a58fcc00b95626f3e4eb7d34d79af608436fe
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="objectschemaname-transact-sql"></a>OBJECT_SCHEMA_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает имя схемы базы данных в области действия схемы. Список объектов области схемы см. в разделе [sys.objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
OBJECT_SCHEMA_NAME ( object_id [, database_id ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *object_id*  
 Идентификатор объекта, который будет использован. *object_id* — **int** и считается объект области схемы указанной базы данных или в контексте текущей базы данных.  
  
 *database_id*  
 Идентификатор базы данных, где будет выполняться поиск объекта. *database_id* — **int**.  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **sysname**  
  
## <a name="exceptions"></a>Исключения  
 Возвращает значение NULL в случае ошибки или если участник не имеет разрешений для просмотра объекта. Если параметр AUTO_CLOSE целевой базы данных имеет значение ON, то функция откроет базу данных.  
  
 Пользователь может просматривать только метаданные защищаемых объектов, которыми он владеет или на которые пользователю были предоставлены разрешения. Это означает, что встроенные функции, создающие метаданные, такие как OBJECT_SCHEMA_NAME могут вернуть значение NULL в случае, если пользователь не имеет разрешений на объект. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение ANY на данный объект. Чтобы указать идентификатор базы данных, также требуется разрешение CONNECT на базу данных или необходимо включить гостевую учетную запись.  
  
## <a name="remarks"></a>Замечания  
 Системные функции можно использовать в списке выбора, в предложении WHERE и в любом месте, где разрешается использование выражений. Дополнительные сведения см. в разделе [выражений](../../t-sql/language-elements/expressions-transact-sql.md) и [ГДЕ](../../t-sql/queries/where-transact-sql.md).  
  
 Результирующий набор, возвращенный системной функцией, использует порядок сортировки текущей базы данных.  
  
 Если *database_id* не указан, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] предполагается, что *object_id* находится в контексте текущей базы данных. Запрос, который ссылается на *object_id* в другой базе данных возвращает значение NULL или неправильные результаты. Например, в следующем запросе текущий контекст базы данных — база данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] пытается возвратить имя схемы объекта для заданного идентификатора объекта в этой базе данных, а не в базе данных, указанной в предложении FROM запроса. Поэтому возвращаются неверные сведения.  
  
```  
SELECT DISTINCT OBJECT_SCHEMA_NAME(object_id)  
FROM master.sys.objects;  
  
```  
  
 Следующий пример указывает идентификатор базы данных для базы данных `master` в базе данных в функции `OBJECT_SCHEMA_NAME` и приводит к правильным результатам.  
  
```  
SELECT DISTINCT OBJECT_SCHEMA_NAME(object_id, 1) AS schema_name  
FROM master.sys.objects;  
  
```  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-object-schema-name-and-object-name"></a>A. Возвращение имени схемы объекта и имени объекта  
 Следующий пример возвращает имя схемы объекта, имя объекта и SQL-текст для всех кэшированных планов запроса, которые не являются нерегламентированными или подготовленными инструкциями.  
  
```  
SELECT DB_NAME(st.dbid) AS database_name,   
    OBJECT_SCHEMA_NAME(st.objectid, st.dbid) AS schema_name,  
    OBJECT_NAME(st.objectid, st.dbid) AS object_name,   
    st.text AS query_statement  
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
WHERE st.objectid IS NOT NULL;  
GO  
```  
  
### <a name="b-returning-three-part-object-names"></a>Б. Возвращение трехсоставных имен объекта  
 Следующий пример возвращает имя базы данных, схемы и объекта вместе со всеми остальными столбцами в динамическом административном представлении `sys.dm_db_index_operational_stats` для всех объектов во всех базах данных.  
  
```  
SELECT QUOTENAME(DB_NAME(database_id))   
    + N'.'   
    + QUOTENAME(OBJECT_SCHEMA_NAME(object_id, database_id))   
    + N'.'   
    + QUOTENAME(OBJECT_NAME(object_id, database_id))  
    , *   
FROM sys.dm_db_index_operational_stats(null, null, null, null);  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции метаданных &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECT_DEFINITION (Transact-SQL)](../../t-sql/functions/object-definition-transact-sql.md)   
 [Object_id &#40; Transact-SQL &#41;](../../t-sql/functions/object-id-transact-sql.md)   
 [Object_name &#40; Transact-SQL &#41;](../../t-sql/functions/object-name-transact-sql.md)   
 [Защищаемые объекты](../../relational-databases/security/securables.md)  
  
  
