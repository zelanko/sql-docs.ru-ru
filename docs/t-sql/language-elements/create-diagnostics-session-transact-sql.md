---
title: "Создание СЕАНСА диагностики (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 662d019e-f217-49df-9e2f-b5662fa0342d
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 71f3463ad4d91bd117c322e9e63c0b331b07ca9f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-diagnostics-session-transact-sql"></a>Создание СЕАНСА диагностики (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Диагностические сеансы позволяют сохранять подробные определяемых пользователем диагностическую информацию о производительности системы или запроса.  
  
 Диагностические сеансы обычно используются для отладки производительности для конкретного запроса или для наблюдения за поведением определенного устройства компонентов во время операции с устройством.  
  
> [!NOTE]  
>  Необходимо ознакомиться с XML для использования сеансов диагностики.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Creating a new diagnostics session:  
CREATE DIAGNOSTICS SESSION diagnostics_name AS N’{<session_xml>}’;  
  
<session_xml>::  
<Session>  
   [ <MaxItemCount>max_item_count_num</MaxItemCount> ]  
   <Filter>  
      { \<Event Name=”event_name”/>  
         [ <Where>\<filter_property_name Name=”value” ComparisonType="comp_type"/></Where> ] [ ,...n ]  
      } [ ,...n ]  
   </Filter> ]   
   <Capture>  
      \<Property Name=”property_name”/> [ ,...n ]  
   </Capture>  
<Session>  
  
Retrieving results for a diagnostics session:  
SELECT * FROM master.sysdiag.diagnostics_name ;  
  
Removing results for a diagnostics session:  
DROP DIAGNOSTICS SESSION diagnostics_name ;  
```  
  
## <a name="arguments"></a>Аргументы  
 *diagnostics_name*  
 Имя сеанса диагностики. Имена сеанса диагностики могут содержать символы a-z, A-Z и 0-9 только. Кроме того имена сеанса диагностики должны начинаться с буквы. *diagnostics_name* не должна превышать 127 символов.  
  
 *max_item_count_num*  
 Число событий, должна быть сохранена в представлении. Например если указано значение 100, 100 последних событий, соответствующих условиям фильтра будут сохраняться в сеанс диагностики. При обнаружении менее 100 сопоставления событий сеанса диагностики будет содержать не более 100 событий. *max_item_count_num* должно быть по крайней мере 100 и меньше или равно 100 000.  
  
 *имя_события*  
 Определяет фактическое сбор событий в сеансе диагностики.  *имя_события* является одним из событий, перечисленных в [sys.pdw_diag_events](http://msdn.microsoft.com/en-us/d813aac0-cea1-4f53-b8e8-d26824bc2587) где `sys.pdw_diag_events.is_enabled='True'`.  
  
 *filter_property_name*  
 Имя свойства, для которого требуется ограничить результаты. Например, если вы хотите ограничить на основе идентификатора сеанса *filter_property_name* должно быть *SessionId*. В разделе *property_name* ниже список возможных значений для *filter_property_name*.  
  
 *value*  
 Значение, сравниваемое с *filter_property_name*. Тип значения должен соответствовать типу свойства. Например, если тип свойства имеет тип decimal тип *значение* должно быть десятичное число.  
  
 *comp_type*  
 Тип сравнения. Возможные значения являются: равно, EqualsOrGreaterThan, EqualsOrLessThan, GreaterThan, LessThan, NotEquals, Contains, регулярное выражение  
  
 *property_name*  
 Свойства, связанные с событием.  Имена свойств могут быть частью тега захвата или используется как один из критериев фильтрации.  
  
|Имя свойства|Description|  
|-------------------|-----------------|  
|UserName|Имя пользователя (имя входа).|  
|SessionId|Идентификатор сеанса.|  
|QueryId|Идентификатор запроса.|  
|CommandType|Тип команды.|  
|CommandText|Текст внутри команды обработки.|  
|OperationType|Тип операции для события.|  
|Длительность|Длительность события.|  
|SPID|Идентификатор процесса службы.|  
  
## <a name="remarks"></a>Замечания  
 Каждый пользователь может более 10 одновременных диагностические сеансы. В разделе [sys.pdw_diag_sessions](http://msdn.microsoft.com/en-us/ca111ddc-2787-4205-baf0-1a242c0257a9) список текущих сеансов и drop все ненужные сеансов с помощью `DROP DIAGNOSTICS SESSION`.  
  
 Диагностические сеансы будут продолжать собирать метаданных до удаления.  
  
## <a name="permissions"></a>Permissions  
 Требуется **ALTER SERVER STATE** разрешение.  
  
## <a name="locking"></a>Блокировка  
 Принимает разделяемую блокировку таблицы диагностических сеансов.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-diagnostics-session"></a>A. Создание сеанса диагностики  
 Этот пример создает сеанс диагностики для записи метрик производительности ядра базы данных. В примере создается сеанса диагностики, ожидающий запрос к ядру СУБД запуска и окончания события и события блокировки DMS. Возвращаемые является текст команды, имя компьютера, идентификатор запроса (идентификатор запроса) и сеанс, который был создан события.  
  
```  
CREATE DIAGNOSTICS SESSION MYDIAGSESSION AS N'  
<Session>  
   <MaxItemCount>100</MaxItemCount>  
   <Filter>  
      <Event Name="EngineInstrumentation:EngineQueryRunningEvent" />  
      <Event Name="DmsCoreInstrumentation:DmsBlockingQueueEnqueueBeginEvent" />  
      <Where>  
         <SessionId Value="381" ComparisonType="NotEquals" />  
      </Where>  
   </Filter>  
   <Capture>  
      <Property Name="Query.CommandText" />  
      <Property Name="MachineName" />  
      <Property Name="Query.QueryId" />  
      <Property Name="Alias" />  
      <Property Name="Duration" />  
      <Property Name="Session.SessionId" />  
   </Capture>  
</Session>';  
```  
  
 После создания сеанса диагностики выполните запрос.  
  
```  
SELECT COUNT(EmployeeKey) FROM AdventureWorksPDW2012..FactSalesQuota;  
```  
  
 Затем просмотрите результаты сеанса диагностики, выбрав из схемы sysdiag.  
  
```  
SELECT * FROM master.sysdiag.MYDIAGSESSION;  
```  
  
 Обратите внимание, что схема sysdiag содержит представление, которое называется ваше имя сеанса диагностики.  
  
 Чтобы просмотреть действия, для подключения, добавьте `Session.SPID` свойство и добавьте `WHERE [Session.SPID] = @@spid;` в запрос.  
  
 Когда вы закончите сеанса диагностики, удалите ее при помощи **DROP диагностики** команды.  
  
```  
DROP DIAGNOSTICS SESSION MYDIAGSESSION;  
```  
  
### <a name="b-alternative-diagnostic-session"></a>Б. Альтернативные диагностического сеанса  
 Во втором примере с немного разные свойства.  
  
```  
-- Determine the session_id of your current session  
SELECT TOP 1 session_id();  
-- Replace \<*session_number*> in the code below with the numbers in your session_id  
CREATE DIAGNOSTICS SESSION PdwOptimizationDiagnostics AS N'  
<Session>  
   <MaxItemCount>100</MaxItemCount>  
   <Filter>  
      <Event Name="EngineInstrumentation:MemoGenerationBeginEvent" />  
      <Event Name="EngineInstrumentation:MemoGenerationEndEvent" />  
      <Event Name="DSQLInstrumentation:OptimizationBeginEvent" />  
      <Event Name="DSQLInstrumentation:OptimizationEndEvent" />  
      <Event Name="DSQLInstrumentation:BuildRelOpContextTreeBeginEvent" />  
      <Event Name="DSQLInstrumentation:PostPlanGenModifiersEndEvent" />  
      <Where>  
         <SessionId Value="\<*session_number*>" ComparisonType="Equals" />  
      </Where>  
   </Filter>  
   <Capture>  
      <Property Name="Session.SessionId" />  
      <Property Name="Query.QueryId" />  
      <Property Name="Query.CommandText" />  
      <Property Name="Name" />  
      <Property Name="DateTimePublished" />  
      <Property Name="DateTimePublished.Ticks" />  
  </Capture>  
</Session>';  
```  
  
 Выполните запрос, например:  
  
```  
USE ssawPDW;  
GO  
SELECT * FROM dbo.FactFinance;  
```  
  
 Следующий запрос возвращает время авторизации:  
  
```  
SELECT *   
FROM master.sysdiag.PdwOptimizationDiagnostics   
ORDER BY DateTimePublished;  
```  
  
 Когда вы закончите сеанса диагностики, удалите ее при помощи **DROP диагностики** команды.  
  
```  
DROP DIAGNOSTICS SESSION PdwOptimizationDiagnostics;  
```  
  
  

