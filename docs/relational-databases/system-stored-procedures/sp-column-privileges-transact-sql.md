---
description: sp_column_privileges (Transact-SQL)
title: sp_column_privileges (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_column_privileges_TSQL
- sp_column_privileges
dev_langs:
- TSQL
helpviewer_keywords:
- sp_column_privileges
ms.assetid: a3784301-2517-4b1d-bbd9-47404483fad0
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 279789c40dbc79dd3d7b2d421d757a936b0e6126
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97482403"
---
# <a name="sp_column_privileges-transact-sql"></a>sp_column_privileges (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает сведения о правах доступа к столбцам для одной таблицы текущего окружения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_column_privileges [ @table_name = ] 'table_name'   
     [ , [ @table_owner = ] 'table_owner' ]   
     [ , [ @table_qualifier = ] 'table_qualifier' ]   
     [ , [ @column_name = ] 'column' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @table_name =] "*table_name*"  
 Таблица, используемая для возврата сведений о каталоге. Аргумент *table_name* имеет тип **sysname** и не имеет значения по умолчанию. Сопоставление по шаблону не поддерживается.  
  
 [ @table_owner =] "*table_owner*"  
 Владелец таблицы, используемой для возврата сведений о каталоге. Аргумент *table_owner* имеет тип **sysname** и значение по умолчанию NULL. Сопоставление по шаблону не поддерживается. Если параметр *table_owner* не указан, применяются правила видимости таблиц по умолчанию базовой системы управления базами данных (СУБД).  
  
 Если текущему пользователю принадлежит таблица с указанным именем, возвращаются столбцы этой таблицы. Если параметр *table_owner* не указан и текущий пользователь не владеет таблицей с указанным *table_name*, sp_column привилегий ищет таблицу с указанным *table_name* владельцем базы данных. Если такая таблица существует, возвращаются ее столбцы.  
  
 [ @table_qualifier =] "*table_qualifier*"  
 Имя квалификатора таблицы. Аргумент *table_qualifier* имеет тип *sysname* и значение по умолчанию NULL. Различные продукты СУБД поддерживают имена таблиц (_Квалификаторы_**,** состоящие из трех частей). _владелец_**.** _имя_). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, где находится таблица.  
  
 [ @column_name =] "*столбец*"  
 Единственный столбец, который используется при получении только одного столбца сведений о каталоге. *столбец* имеет тип **nvarchar (** 384 **)** и значение по умолчанию NULL. Если *столбец* не указан, возвращаются все столбцы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *столбце столбец* представляет имя столбца, указанное в таблице sys. Columns. *столбец* может содержать подстановочные знаки, используя шаблоны сопоставления с подстановочными знаками базовой СУБД. Для максимальной совместимости клиент шлюза должен использовать только согласование установленного образца ISO (символы-шаблоны % и _).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Хранимая процедура sp_column_privileges эквивалентна функции SQLColumnPrivileges в ODBC. Возвращаемые результаты сортируются по столбцам TABLE_QUALIFIER, TABLE_OWNER, TABLE_NAME, COLUMN_NAME и PRIVILEGE.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|TABLE_QUALIFIER|**sysname**|Имя квалификатора таблицы. Это поле может иметь значение NULL.|  
|TABLE_OWNER|**sysname**|Имя владельца таблицы. Это поле всегда возвращает значение.|  
|TABLE_NAME|**sysname**|Имя таблицы. Это поле всегда возвращает значение.|  
|COLUMN_NAME|**sysname**|Имя столбца для каждого возвращенного столбца из таблицы TABLE_NAME. Это поле всегда возвращает значение.|  
|GRANTOR|**sysname**|Имя пользователя базы данных, который предоставил права доступа к столбцу COLUMN_NAME перечисленным пользователям категории GRANTEE. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец всегда совпадает с владельцем TABLE_OWNER. Это поле всегда возвращает значение.<br /><br /> В столбце GRANTOR может быть указан либо владелец базы данных (TABLE_OWNER), либо пользователь, которому владелец базы данных предоставил разрешения с помощью предложения WITH GRANT OPTION в инструкции GRANT.|  
|GRANTEE|**sysname**|Имя пользователя базы данных, которому предоставил разрешения на доступ к столбцу COLUMN_NAME указанный GRANTOR. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец всегда содержит имя пользователя базы данных из таблицы sysusers. Это поле всегда возвращает значение.|  
|PRIVILEGE|**varchar (** 32 **)**|Одно из доступных разрешений на доступ к столбцу. Разрешениями для столбца может быть одно из следующих значений (или другие значения, поддерживаемые источником данных для определенных реализаций):<br /><br /> SELECT = пользователь GRANTEE может получать данные для столбцов;<br /><br /> INSERT = пользователь GRANTEE может предоставлять данные для этого столбца, когда новые строки вставляются (этим пользователем) в таблицу;<br /><br /> UPDATE = пользователь GRANTEE может изменять существующие данные в столбце;<br /><br /> REFERENCES = GRANTEE — может ссылаться на столбец во внешней таблице в связи «первичный-внешний ключ». Связи «первичный/внешний ключ» определяются с помощью ограничений таблицы.|  
|IS_GRANTABLE|**varchar (** 3 **)**|Указывает, разрешено ли пользователю GRANTEE предоставлять разрешения другим пользователям (часто обозначается как разрешение «право передачи»). Может иметь значение YES, NO или NULL. Неизвестное значение или значение NULL, указывает на источник данных, для которого не применимо разрешение «право передачи».|  
  
## <a name="remarks"></a>Комментарии  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разрешения предоставляются инструкцией GRANT и отзываются инструкцией REVOKE.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="examples"></a>Примеры  
 В следующем примере будут возвращены сведения о правах доступа к столбцу для определенного столбца.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_column_privileges @table_name = 'Employee'   
    ,@table_owner = 'HumanResources'  
    ,@table_qualifier = 'AdventureWorks2012'  
    ,@column_name = 'SalariedFlag';  
```  
  
## <a name="see-also"></a>См. также:  
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE (Transact-SQL)](../../t-sql/statements/revoke-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
