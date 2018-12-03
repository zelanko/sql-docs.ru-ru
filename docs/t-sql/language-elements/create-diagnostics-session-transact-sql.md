---
title: CREATE DIAGNOSTICS SESSION (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 662d019e-f217-49df-9e2f-b5662fa0342d
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 9eefa5a7120f64f5dc6f621a2a74956a461619d9
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52394034"
---
# <a name="create-diagnostics-session-transact-sql"></a>CREATE DIAGNOSTICS SESSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Сеансы диагностики позволяют сохранять подробные определяемые пользователем диагностические сведения о производительности системы или запросов.  
  
 Сеансы диагностики обычно используются для отладки производительности определенного запроса или для отслеживания поведения определенного компонента устройства во время работы устройства.  
  
> [!NOTE]  
>  Для использования сеансов диагностики необходимо уметь работать с XML.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Creating a new diagnostics session:  
CREATE DIAGNOSTICS SESSION diagnostics_name AS N'{<session_xml>}';  
  
<session_xml>::  
<Session>  
   [ <MaxItemCount>max_item_count_num</MaxItemCount> ]  
   <Filter>  
      { \<Event Name="event_name"/>  
         [ <Where>\<filter_property_name Name="value" ComparisonType="comp_type"/></Where> ] [ ,...n ]  
      } [ ,...n ]  
   </Filter> ]   
   <Capture>  
      \<Property Name="property_name"/> [ ,...n ]  
   </Capture>  
<Session>  
  
Retrieving results for a diagnostics session:  
SELECT * FROM master.sysdiag.diagnostics_name ;  
  
Removing results for a diagnostics session:  
DROP DIAGNOSTICS SESSION diagnostics_name ;  
```  
  
## <a name="arguments"></a>Аргументы  
 *diagnostics_name*  
 Имя сеанса диагностики. Имена сеансов диагностики могут содержать только символы a–z, A–Z и 0–9. Кроме того, имена сеансов диагностики должны начинаться с буквы. Длина имени *diagnostics_name* ограничена 127 символами.  
  
 *max_item_count_num*  
 Число событий, сохраняемых в представлении. Например, если задано значение 100, в сеансе диагностики сохраняются 100 последних событий, соответствующих условию фильтра. Если обнаружено менее 100 соответствующих событий, сеанс диагностики будет содержать менее 100 событий. Значение *max_item_count_num* должно находиться в диапазоне от 100 до 100 000.  
  
 *event_name*  
 Определяет фактические события, которые должны собираться в рамках сеанса диагностики.  Значение *event_name* — это одно из событий, перечисленных в представлении [sys.pdw_diag_events](https://msdn.microsoft.com/d813aac0-cea1-4f53-b8e8-d26824bc2587), где `sys.pdw_diag_events.is_enabled='True'`.  
  
 *filter_property_name*  
 Имя свойства, по которому ограничиваются результаты. Например, чтобы ограничить результаты по идентификатору сеанса, аргументу *filter_property_name* следует присвоить значение *SessionId*. Список возможных значений аргумента *filter_property_name* см. в описании аргумента *property_name* ниже.  
  
 *value*  
 Значение, сравниваемое с *filter_property_name*. Тип значения должен совпадать с типом свойства. Например, если свойство имеет десятичный тип, аргумент *value* также должен иметь десятичный тип.  
  
 *comp_type*  
 Тип сравнения. Возможные значения: Equals, EqualsOrGreaterThan, EqualsOrLessThan, GreaterThan, LessThan, NotEquals, Contains, RegEx  
  
 *property_name*  
 Свойство, связанное с событием.  Имена свойств могут быть частью тега записи или использоваться как часть условия фильтрации.  
  
|Имя свойства|Описание|  
|-------------------|-----------------|  
|UserName|Имя пользователя (имя для входа).|  
|SessionId|Идентификатор сеанса.|  
|QueryId|Идентификатор запроса.|  
|CommandType|Тип команды.|  
|CommandText|Текст внутри обрабатываемой команды.|  
|OperationType|Тип операции для события.|  
|Duration|Длительность события.|  
|SPID|Идентификатор процесса службы.|  
  
## <a name="remarks"></a>Remarks  
 Каждый пользователь может одновременно открывать до 10 сеансов диагностики. Список текущих сеансов можно получить в представлении [sys.pdw_diag_sessions](https://msdn.microsoft.com/ca111ddc-2787-4205-baf0-1a242c0257a9). Ненужные сеансы можно удалить с помощью инструкции `DROP DIAGNOSTICS SESSION`.  
  
 Сеансы диагностики продолжают собирать метаданные, пока не будут удалены.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение **ALTER SERVER STATE**.  
  
## <a name="locking"></a>Блокировка  
 Принимает совмещаемую блокировку для таблицы Diagnostic Sessions.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-diagnostics-session"></a>A. Создание сеанса диагностики  
 В этом примере создается сеанс диагностики для записи метрик производительности ядра СУБД. В примере создается сеанс диагностики, который ожидает получения событий, связанных с выполнением и завершением запросов ядра, и события блокировки DMS. Возвращаются текст команды, имя компьютера, идентификатор запроса и сеанс, в рамках которого было создано событие.  
  
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
  
 Затем просмотрите результаты сеанса диагностики, выбрав его в схеме sysdiag.  
  
```  
SELECT * FROM master.sysdiag.MYDIAGSESSION;  
```  
  
 Обратите внимание на то, что в схеме sysdiag есть представление, имя которого совпадает с именем сеанса диагностики.  
  
 Чтобы просмотреть действия, связанные только с вашим подключением, добавьте свойство `Session.SPID` и добавьте предложение `WHERE [Session.SPID] = @@spid;` в запрос.  
  
 Завершив работу с сеансом диагностики, удалите его с помощью команды **DROP DIAGNOSTICS**.  
  
```  
DROP DIAGNOSTICS SESSION MYDIAGSESSION;  
```  
  
### <a name="b-alternative-diagnostic-session"></a>Б. Альтернативный сеанс диагностики  
 Во втором примере используются немного другие свойства.  
  
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
  
 Завершив работу с сеансом диагностики, удалите его с помощью команды **DROP DIAGNOSTICS**.  
  
```  
DROP DIAGNOSTICS SESSION PdwOptimizationDiagnostics;  
```  
  
  
