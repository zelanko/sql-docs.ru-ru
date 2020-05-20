---
title: sp_helpstats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpstats
- sp_helpstats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpstats
ms.assetid: 00ab3cfd-2736-4fc0-b1b2-16dd49fb2fe5
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b4f84f187ea3f511b8dddcc79c712dfd7809748d
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824437"
---
# <a name="sp_helpstats-transact-sql"></a>sp_helpstats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает статистические сведения о столбцах и индексах указанной таблицы.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]Чтобы получить сведения о статистике, запросите представления каталога [sys. stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) и [sys. stats_columns](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpstats[ @objname = ] 'object_name'   
     [ , [ @results = ] 'value' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @objname = ] 'object_name'`Указывает таблицу, в которой должны быть представлены статистические данные. *object_name* имеет тип **nvarchar (520)** и не может иметь значение null. Можно указать одно- или двухкомпонентное имя таблицы.  
  
`[ @results = ] 'value'`Задает объем предоставляемых данных. Допустимые значения: **ALL** и **stats**. **Все** списки содержит статистику для всех индексов, а также столбцов, для которых создана статистика. **Статистика содержит только статистику** , не связанную с индексом. *value* имеет тип **nvarchar (5)** и значение по умолчанию stats.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 В следующей таблице отображены столбцы результирующего набора.  
  
|Имя столбца|Описание|  
|-----------------|-----------------|  
|**statistics_name**|Название статистики. Возвращает значение **sysname** и не может быть null.|  
|**statistics_keys**|Ключи, на которых основаны статистические сведения. Возвращает значение типа **nvarchar (2078)** и не может быть null.|  
  
## <a name="remarks"></a>Примечания  
 Для отображения подробных статистических сведений об определенном индексе или статистике воспользуйтесь инструкцией DBCC SHOW_STATISTICS. Дополнительные сведения см. в разделе [DBCC SHOW_STATISTICS &#40;Transact-sql&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md) и [sp_helpindex &#40;transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере с помощью процедуры `sp_createstats` создаются статистики, состоящие из одного столбца, для всех подходящих столбцов всех таблиц пользователя в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Затем, чтобы найти полученные статистики, созданные для таблицы `sp_helpstats`, запускается процедура `Customer`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_createstats;  
GO  
EXEC sp_helpstats   
@objname = 'Sales.Customer',  
@results = 'ALL';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `statistics_name               statistics_keys`  
  
 `----------------------------  ----------------`  
  
 `_WA_Sys_00000003_22AA2996     AccountNumber`  
  
 `AK_Customer_AccountNumber     AccountNumber`  
  
 `AK_Customer_rowguid           rowguid`  
  
 `CustomerType                  CustomerType`  
  
 `IX_Customer_TerritoryID       TerritoryID`  
  
 `ModifiedDate                  ModifiedDate`  
  
 `PK_Customer_CustomerID        CustomerID`  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
