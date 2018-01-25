---
title: ": DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/16/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|database-console-commands
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
caps.latest.revision: "12"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: af6b466df18df3df0535a2de8f582f57484255aa
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-pdwshowexecutionplan-transact-sql"></a>: DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Отображает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] план выполнения для запросов, выполняемых на определенном [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] вычислительный узел или узел элемента управления. Используется для устранения неполадок проблем производительности запросов при выполнении запросов на вычислительные узлы и узел элемента управления.
  
Если проблемы с производительностью запросов, применимые для SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запросы, выполняемые на вычислительных узлах, существует несколько способов для повышения производительности. Создание статистики по нескольким столбцам, создание некластеризованных индексов или с помощью подсказки в запросе, следующими способами для повышения производительности запросов на вычислительных узлах.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
Синтаксис для SQL Server:

```sql
DBCC PDW_SHOWEXECUTIONPLAN ( distribution_id, spid )  
[;]  
```  
Синтаксис Azure параллельного хранилища данных:
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( pdw_node_id, spid )  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *distribution_id*  
 Идентификатор для распределения, на котором выполняется план запроса. Это должно быть целым числом и не может иметь значение NULL. Использовать при разработке для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
 *pdw_node_id*  
 Идентификатор для узла, на котором выполняется план запроса. Это должно быть целым числом и не может иметь значение NULL. Используется при нацеливании на устройстве.  
  
 *spid*  
 Идентификатор для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сеанса, на котором выполняется план запроса. Это должно быть целым числом и не может иметь значение NULL.  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения CONTROL на [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
Необходимо разрешение VIEW SERVER STATE на устройстве.
  
## <a name="examples-includesssdwincludessssdw-mdmd"></a>Примеры:[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]  
  
### <a name="a-dbcc-pdwshowexecutionplan-basic-syntax"></a>A. Базовый синтаксис: DBCC PDW_SHOWEXECUTIONPLAN  
 При работе на [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] изменить приведенный выше запрос, чтобы выделить и distribution_id, экземпляр.  
  
```sql
SELECT [sql_spid], [pdw_node_id], [request_id], [dms_step_index], [type], [start_time], [end_time], [status], [distribution_id]  
FROM sys.dm_pdw_dms_workers   
WHERE [status] <> 'StepComplete' and [status] <> 'StepError'  
order by request_id, [dms_step_index];  
```  
  
Возвращает идентификатор spid для каждого работающих распространения. Если вам интересно, перешли какие распространения 1 был запущен в рамках сеанса 375, то будет запустить следующую команду.
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( 1, 375 );  
```  

## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="b-dbcc-pdwshowexecutionplan-basic-syntax"></a>Б. Базовый синтаксис: DBCC PDW_SHOWEXECUTIONPLAN  
 Запрос, выполняется слишком много времени, либо запустить DMS запрос операция плана или операции план запроса SQL.  
  
Если запрос выполняется операция DMS план запроса, можно использовать следующий запрос для получения списка идентификаторов узла и идентификаторы сеанса для действия, которые не являются полными.
  
```sql
SELECT [sql_spid], [pdw_node_id], [request_id], [dms_step_index], [type], [start_time], [end_time], [status]   
FROM sys.dm_pdw_dms_workers   
WHERE [status] <> 'StepComplete' and [status] <> 'StepError'  
AND pdw_node_id = 201001   
order by request_id, [dms_step_index], [distribution_id];  
```  
  
На основании результатов предыдущего запроса использования sql_spid и pdw_node_id в качестве параметров DBCC PDW_SHOWEXEUCTIONPLAN. Например следующая команда показывает план выполнения для pdw_node_id 201001 и sql_spid 375.
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( 201001, 375 );  
```  

## <a name="see-also"></a>См. также:
[DBCC PDW_SHOWPARTITIONSTATS &#40; Transact-SQL &#41;](dbcc-pdw-showpartitionstats-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED &#40; Transact-SQL &#41;](dbcc-pdw-showspaceused-transact-sql.md)
