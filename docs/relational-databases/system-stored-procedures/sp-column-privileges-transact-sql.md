---
title: sp_column_privileges (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_column_privileges_TSQL
- sp_column_privileges
dev_langs:
- TSQL
helpviewer_keywords:
- sp_column_privileges
ms.assetid: a3784301-2517-4b1d-bbd9-47404483fad0
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5071d68cfe594b2b4266a5c83398ebdd5a9bfbea
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33239774"
---
# <a name="spcolumnprivileges-transact-sql"></a>sp_column_privileges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
 [ @table_name=] '*table_name*"  
 Таблица, используемая для возврата сведений о каталоге. *имя_таблицы* — **sysname**, не имеет значения по умолчанию. Сопоставление по шаблону не поддерживается.  
  
 [ @table_owner=] '*table_owner*"  
 Владелец таблицы, используемой для возврата сведений о каталоге. *TABLE_OWNER* — **sysname**, значение по умолчанию NULL. Сопоставление по шаблону не поддерживается. Если *table_owner* не указан, применяются правила видимости таблиц по умолчанию базовой системы управления базы данных (СУБД).  
  
 Если текущему пользователю принадлежит таблица с указанным именем, возвращаются столбцы этой таблицы. Если *table_owner* не указан и текущий пользователь не является владельцем таблицы с указанным *table_name*, sp_column_privileges выполняет поиск таблицы с указанным *table_name* принадлежат владельцу базы данных. Если такая таблица существует, возвращаются ее столбцы.  
  
 [ @table_qualifier=] '*table_qualifier*"  
 Имя квалификатора таблицы. *table_qualifier* — *sysname*, значение по умолчанию NULL. Различные продукты СУБД поддерживают трехкомпонентные имена таблиц (*квалификатор ***.*** владелец ***.*** имя*). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, где находится таблица.  
  
 [ @column_name=] '*столбца*"  
 Единственный столбец, который используется при получении только одного столбца сведений о каталоге. *столбец* — **nvarchar (** 384 **)**, значение по умолчанию NULL. Если *столбца* — не указано, возвращаются все столбцы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], *столбца* представляет имя столбца, как показано в таблице sys.columns. *столбец* может содержать подстановочные знаки, используя шаблоны совпадения базовой СУБД. Для максимальной совместимости клиент шлюза должен использовать только согласование установленного образца ISO (символы-шаблоны % и _).  
  
## <a name="result-sets"></a>Результирующие наборы  
 sp_column_privileges эквивалентна SQLColumnPrivileges в ODBC. Возвращаемые результаты сортируются по столбцам TABLE_QUALIFIER, TABLE_OWNER, TABLE_NAME, COLUMN_NAME и PRIVILEGE.  
  
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
  
## <a name="remarks"></a>Замечания  
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
  
## <a name="see-also"></a>См. также  
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE (Transact-SQL)](../../t-sql/statements/revoke-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
