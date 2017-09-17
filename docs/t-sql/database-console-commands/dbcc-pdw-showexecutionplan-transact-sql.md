---
title: ": DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.service: sql-data-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
caps.latest.revision: 12
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 461ee87f41692172b31125e36553c0eab0b09772
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-pdwshowexecutionplan-transact-sql"></a>: DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

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
  
 *Идентификатор SPID*  
 Идентификатор для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сеанса, на котором выполняется план запроса. Это должно быть целым числом и не может иметь значение NULL.  
  
## <a name="permissions"></a>Permissions  
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
