---
title: DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/16/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: uc-msft
ms.author: umajay
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: d69a9393c990c16357287ac31433780c3b7e27a4
ms.sourcegitcommit: 467b2c708651a3a2be2c45e36d0006a5bbe87b79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53979840"
---
# <a name="dbcc-pdwshowexecutionplan-transact-sql"></a>DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Отображает план выполнения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для запроса, выполняющегося в определенном вычислительном либо управляющем узле [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Позволяет устранять проблемы с производительностью запросов, выполняющихся в вычислительных узлах или управляющем узле.
  
После определения проблем с производительностью запросов SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполняющихся в вычислительных узлах, повысить производительность можно несколькими способами. Возможные способы оптимизации производительности запросов в вычислительных узлах включают в себя создание статистики по нескольким столбцам, создание некластеризованных индексов или использование указаний запросов.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
Синтаксис хранилища данных SQL Azure:

```sql
DBCC PDW_SHOWEXECUTIONPLAN ( distribution_id, spid )  
[;]  
```  
Синтаксис для Azure Parallel Data Warehouse:
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( pdw_node_id, spid )  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *distribution_id*  
 Идентификатор распределения, в котором выполняется план запроса. Это целое число; не может быть равно NULL. Используется при разработке для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
 *pdw_node_id*  
 Идентификатор узла, в котором выполняется план запроса. Это целое число; не может быть равно NULL. Используется для устройства.  
  
 *spid*  
 Идентификатор сеанса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в котором выполняется план запроса. Это целое число; не может быть равно NULL.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение CONTROL для [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
Требуется разрешение VIEW-SERVER-STATE для устройства.
  
## <a name="examples-includesssdwincludessssdw-mdmd"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]  
  
### <a name="a-dbcc-pdwshowexecutionplan-basic-syntax"></a>A. Базовый синтаксис DBCC PDW_SHOWEXECUTIONPLAN  
 При выполнении в экземпляре [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] измените приведенный выше запрос так, чтобы также выбирался идентификатор distribution_id.  
  
```sql
SELECT [sql_spid], [pdw_node_id], [request_id], [dms_step_index], [type], [start_time], [end_time], [status], [distribution_id]  
FROM sys.dm_pdw_dms_workers   
WHERE [status] <> 'StepComplete' and [status] <> 'StepError'  
order by request_id, [dms_step_index];  
```  
  
В результате будет возвращаться идентификатор SPID для каждого активного распределения. Чтобы узнать, что выполнялось в рамках распределения 1 в сеансе 375, следует выполнить приведенную ниже команду.
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( 1, 375 );  
```  

## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="b-dbcc-pdwshowexecutionplan-basic-syntax"></a>Б. Базовый синтаксис DBCC PDW_SHOWEXECUTIONPLAN  
 Если запрос выполняется слишком долго, значит, он производит операцию плана запроса DMS или операцию плана запроса SQL.  
  
Если запрос выполняет операцию плана запроса DMS, с помощью приведенного ниже запроса можно получить список идентификаторов узлов и сеансов для незавершенных этапов.
  
```sql
SELECT [sql_spid], [pdw_node_id], [request_id], [dms_step_index], [type], [start_time], [end_time], [status]   
FROM sys.dm_pdw_dms_workers   
WHERE [status] <> 'StepComplete' and [status] <> 'StepError'  
AND pdw_node_id = 201001   
order by request_id, [dms_step_index], [distribution_id];  
```  
  
Полученные в результате предыдущего запроса значения sql_spid и pdw_node_id можно использовать как параметры инструкции DBCC PDW_SHOWEXEUCTIONPLAN. Например, приведенная ниже команда отображает план выполнения для pdw_node_id 201001 и sql_spid 375.
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( 201001, 375 );  
```  

## <a name="see-also"></a>См. также раздел
[DBCC PDW_SHOWPARTITIONSTATS (Transact-SQL)](dbcc-pdw-showpartitionstats-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED (Transact-SQL)](dbcc-pdw-showspaceused-transact-sql.md)
