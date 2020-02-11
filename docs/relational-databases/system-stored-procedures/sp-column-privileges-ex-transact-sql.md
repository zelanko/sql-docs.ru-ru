---
title: sp_column_privileges_ex (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_column_privileges_ex
- sp_column_privileges_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_column_privileges_ex
ms.assetid: 98cb6e58-4007-40fc-b048-449fb2e7e6be
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd4251c4b47f67d348b6978c05c07d0ae64d16c8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070362"
---
# <a name="sp_column_privileges_ex-transact-sql"></a>sp_column_privileges_ex (Transact-SQL)
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
`[ @table_server = ] 'table_server'`Имя связанного сервера, для которого возвращаются сведения. Аргумент *table_server* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @table_name = ] 'table_name'`Имя таблицы, содержащей указанный столбец. Аргумент *table_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @table_schema = ] 'table_schema'`Схема таблицы. Аргумент *table_schema* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @table_catalog = ] 'table_catalog'`Имя базы данных, в которой находится указанный *table_name* . Аргумент *table_catalog* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @column_name = ] 'column_name'`Имя столбца, для которого необходимо предоставить сведения о правах доступа. Аргумент *column_name* имеет тип **sysname**и значение по умолчанию NULL (все общие).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Следующая таблица показывает столбцы результирующего набора. Возвращаемые результаты упорядочиваются по **TABLE_QUALIFIER**, **table_owner**, **table_name**, **column_name**и **привилегии**.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**имеет sysname**|Имя квалификатора таблицы. Различные продукты СУБД поддерживают имена таблиц (_Квалификаторы_**,** состоящие из трех частей). _владелец_**.** _имя_). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, где находится таблица. Это поле может иметь значение NULL.|  
|**TABLE_SCHEM**|**имеет sysname**|Имя владельца таблицы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя пользователя базы данных, создавшего таблицу. Это поле всегда возвращает значение.|  
|**TABLE_NAME**|**имеет sysname**|Имя таблицы. Это поле всегда возвращает значение.|  
|**COLUMN_NAME**|**имеет sysname**|Имя столбца для каждого столбца возвращаемого **table_name** . Это поле всегда возвращает значение.|  
|**GRANTOR**|**имеет sysname**|Имя пользователя базы данных, которому предоставлены разрешения на эту **column_name** в указанный **участник**. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]этот столбец всегда совпадает с **table_owner**. Это поле всегда возвращает значение.<br /><br /> **Столбцом** -исполнителем может быть либо владелец базы данных (**table_owner**), либо пользователь, которому владелец базы данных предоставил разрешения с помощью предложения WITH GRANT OPTION в инструкции GRANT.|  
|**GRANTEE**|**имеет sysname**|Имя пользователя базы данных, которому были предоставлены разрешения на этот **column_name** указанным объектом **Grant**. Это поле всегда возвращает значение.|  
|**PRIVILEGE**|**varchar (** 32 **)**|Одно из доступных разрешений на доступ к столбцу. Разрешениями для столбца может быть одно из следующих значений (или другие значения, поддерживаемые источником данных для определенных реализаций):<br /><br /> SELECT = **получатель** прав может получать данные для столбцов.<br /><br /> INSERT = **GRANTEE** может предоставлять данные для этого столбца при вставке новых строк ( **участником**) в таблицу.<br /><br /> UPDATE = **участник** может изменять существующие данные в столбце.<br /><br /> REFERENCEs = **участник** может ссылаться на столбец во внешней таблице в связи "первичный ключ — внешний ключ". Связи первичного ключа и внешнего ключа определяются с ограничениями таблицы.|  
|**IS_GRANTABLE**|**varchar (** 3 **)**|Указывает, разрешено ли **участнику** предоставлять разрешения другим пользователям (часто это называется разрешением "предоставление с предоставлением"). Может иметь значение YES, NO или NULL. Неизвестные значения или значения NULL относятся к источникам данных, где неприменимо использование разрешения «право передачи».|  
  
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
  
## <a name="see-also"></a>См. также:  
 [sp_table_privileges_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-ex-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
