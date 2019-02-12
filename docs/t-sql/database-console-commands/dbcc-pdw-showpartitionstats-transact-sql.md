---
title: DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: uc-msft
ms.author: umajay
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 4417dcd94c3dd24e22805f713901c5ddfbf6b727
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56035025"
---
# <a name="dbcc-pdwshowpartitionstats-transact-sql"></a>DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Отображает размер и число строк для каждой секции таблицы в базе данных [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
Show the partition stats for a table  
DBCC PDW_SHOWPARTITIONSTATS ( " [ database_name . [ schema_name ] . ] | [ schema_name.] table_name  ")  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ *database_name* . [ *schema_name* ] . | *schema_name* . ] *table_name*  
 Имя отображаемой таблицы, состоящее из одной, двух или трех частей.  Если имя таблицы состоит из двух или трех частей, оно должно заключаться в двойные кавычки (""). Заключать однокомпонентное имя таблицы в кавычки необязательно.  
  
## <a name="permissions"></a>Разрешения
Необходимо разрешение **VIEW SERVER STATE**.
  
## <a name="result-sets"></a>Результирующие наборы  
Это результат выполнения команды DBCC PDW_SHOWPARTITIONSTATS.
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|partition_number|ssNoversion|Номер секции.|  
|used_page_count|BIGINT|Число страниц, используемых для данных.|  
|reserved_page_count|BIGINT|Число страниц, выделенных для секции.|  
|row_count|BIGINT|Число строк в секции.|  
|pdw_node_id|ssNoversion|Вычислительный узел для данных.|  
|distribution_id|ssNoversion|Идентификатор распространения для данных.|  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-dbcc-pdwshowpartitionstats-basic-syntax-examples"></a>A. Примеры базового синтаксиса DBCC PDW_SHOWPARTITIONSTATS  
В приведенных ниже примерах отображается занимаемое пространство и число строк для каждой секции таблицы FactInternetSales в базе данных [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].
  
```sql
DBCC PDW_SHOWPARTITIONSTATS ("ssawPDW.dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS ("dbo.FactInternetSales");  
DBCC PDW_SHOWPARTITIONSTATS (FactInternetSales);  
```  
## <a name="see-also"></a>См. также раздел
[DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL)](dbcc-pdw-showexecutionplan-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED (Transact-SQL)](dbcc-pdw-showspaceused-transact-sql.md)  
  
