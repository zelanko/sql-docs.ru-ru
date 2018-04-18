---
title: sp_column_privileges_ex (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_column_privileges_ex
- sp_column_privileges_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_column_privileges_ex
ms.assetid: 98cb6e58-4007-40fc-b048-449fb2e7e6be
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0c31ae66112acc5cf1831573e436995c68c5d7ff
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spcolumnprivilegesex-transact-sql"></a>sp_column_privileges_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает права доступа столбца для указанной таблицы на указанном связанном сервере.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_column_privileges_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @column_name = ] 'column_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@table_server =** ] **"***table_server***"**  
 Имя связанного сервера, для которого возвращаются данные. *table_server* — **sysname**, не имеет значения по умолчанию.  
  
 [  **@table_name =** ] **"***table_name***"**  
 Имя таблицы, которая содержит указанный столбец. *имя_таблицы* — **sysname**, значение по умолчанию NULL.  
  
 [  **@table_schema =** ] **"***table_schema***"**  
 Схема таблицы. *table_schema* — **sysname**, значение по умолчанию NULL.  
  
 [  **@table_catalog =** ] **"***значениям table_catalog***"**  
 Имя базы данных, в котором указанный *table_name* находится. *значениям table_catalog* — **sysname**, значение по умолчанию NULL.  
  
 [  **@column_name =** ] **"***column_name***"**  
 Имя столбца, для которого предоставляются сведения о правах доступа. *column_name* — **sysname**, значение по умолчанию NULL (все общие).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Следующая таблица показывает столбцы результирующего набора. Возвращенные результаты сортируются по **TABLE_QUALIFIER**, **TABLE_OWNER**, **TABLE_NAME**, **COLUMN_NAME**, и  **Право доступа**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Имя квалификатора таблицы. Различные продукты СУБД поддерживают трехкомпонентные имена таблиц (*квалификатор***.*** владелец***.*** имя*). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, где находится таблица. Это поле может иметь значение NULL.|  
|**ПО ЗНАЧЕНИЯМ TABLE_SCHEM**|**sysname**|Имя владельца таблицы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя пользователя базы данных, создавшего таблицу. Это поле всегда возвращает значение.|  
|**ИМЯ_ТАБЛИЦЫ**|**sysname**|Имя таблицы. Это поле всегда возвращает значение.|  
|**COLUMN_NAME**|**sysname**|Имя столбца для каждого столбца **TABLE_NAME** возвращается. Это поле всегда возвращает значение.|  
|**ОБЪЕКТ, ПРЕДОСТАВЛЯЮЩИЙ РАЗРЕШЕНИЕ**|**sysname**|Имя пользователя базы данных, предоставившего разрешения на таблицу **COLUMN_NAME** указанному пользователю **УЧАСТНИК**. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], этот столбец всегда имеет то же, что **TABLE_OWNER**. Это поле всегда возвращает значение.<br /><br /> **GRANTOR** столбца может соответствовать или владельцу базы данных (**TABLE_OWNER**) или кто-то, кому владелец базы данных предоставил разрешения с помощью предложения WITH GRANT OPTION инструкции GRANT.|  
|**УЧАСТНИК**|**sysname**|Имя пользователя базы данных, предоставившего разрешения на таблицу **COLUMN_NAME** указанным пользователем **GRANTOR**. Это поле всегда возвращает значение.|  
|**ПРАВО ДОСТУПА**|**varchar (**32**)**|Одно из доступных разрешений на доступ к столбцу. Разрешениями для столбца может быть одно из следующих значений (или другие значения, поддерживаемые источником данных для определенных реализаций):<br /><br /> ВЫБЕРИТЕ = **УЧАСТНИКУ** может получать данные для столбцов.<br /><br /> INSERT = **УЧАСТНИКУ** может предоставлять данные для этого столбца, когда новые строки вставляются (по **УЧАСТНИКУ**) в таблицу.<br /><br /> UPDATE = **УЧАСТНИКУ** может изменять существующие данные в столбце.<br /><br /> REFERENCES = **УЧАСТНИКУ** может ссылаться на столбец во внешней таблице в связи первичного и внешнего ключа. Связи первичного ключа и внешнего ключа определяются с ограничениями таблицы.|  
|**IS_GRANTABLE**|**varchar (**3**)**|Указывает, является ли **УЧАСТНИКУ** предоставлять разрешения другим пользователям (часто обозначается как разрешение «grant with grant»). Может иметь значение YES, NO или NULL. Неизвестные значения или значения NULL относятся к источникам данных, где неприменимо использование разрешения «право передачи».|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает сведения о правах доступа столбца для таблицы `HumanResources.Department` в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] на связанном сервере `Seattle1`.  
  
```  
EXEC sp_column_privileges_ex @table_server = 'Seattle1',   
   @table_name = 'Department',   
   @table_schema = 'HumanResources',  
   @table_catalog ='AdventureWorks2012';  
```  
  
## <a name="see-also"></a>См. также  
 [sp_table_privileges_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-ex-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
