---
title: sp_create_plan_guide_from_handle (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_create_plan_guide_from_handle_TSQL
- sp_create_plan_guide_from_handle
dev_langs:
- TSQL
helpviewer_keywords:
- sp_create_plan_guide_from_handle
ms.assetid: 02cfb76f-a0f9-4b42-a880-1c3e7d64fe41
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 29e5bd9f5dc682862d636b49d77e6b338fe937b9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62724499"
---
# <a name="spcreateplanguidefromhandle-transact-sql"></a>sp_create_plan_guide_from_handle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает одну или несколько структур плана из плана запроса в кэше планов. Эту хранимую процедуру можно использовать для обеспечения использования оптимизатором запросов для конкретного запроса конкретного плана запроса. Дополнительные сведения о структурах планов см. в разделе [Руководства планов](../../relational-databases/performance/plan-guides.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_create_plan_guide_from_handle [ @name = ] N'plan_guide_name'  
    , [ @plan_handle = ] plan_handle  
    , [ [ @statement_start_offset = ] { statement_start_offset | NULL } ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @name =] N'*plan_guide_name*"  
 Имя структуры плана. Имена структур планов ограничены областью текущей базы данных. *plan_guide_name* должны соответствовать требованиям, предъявляемым к [идентификаторы](../../relational-databases/databases/database-identifiers.md) и не может начинаться со знака номера (#). Максимальная длина *plan_guide_name* равна 124 символам.  
  
 [ @plan_handle =] *plan_handle*  
 Определяет пакет в кэше планов. *plan_handle* — **varbinary(64)** . *plan_handle* можно получить из [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md) динамическое административное представление.  
  
 [ @statement_start_offset = ] { *statement_start_offset* | NULL } ]  
 Идентифицирует начальную позицию инструкции внутри пакета, указываемого *plan_handle*. *statement_start_offset* — **int**, значение по умолчанию NULL.  
  
 Смещение инструкции соответствует столбцу statement_start_offset в [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md) динамическое административное представление.  
  
 Если указано значение NULL или смещение инструкции не задано, структура плана создается для каждой инструкции в пакете с помощью плана запроса для указанного дескриптора плана. Полученные в результате структуры планов эквивалентны структурам планов, применяющим указание запроса USE PLAN для принудительного использования определенного плана.  
  
## <a name="remarks"></a>Примечания  
 Структура плана не может быть создана для всех типов инструкций. Если структура плана не может быть создана для какой-либо инструкции в пакете, хранимая процедура пропускает эту инструкцию и переходит к следующей инструкции в пакете. Если инструкция повторяется в одном и том же пакете несколько раз, активируется план для последнего вхождения, а предыдущие планы для инструкции отключаются. Если ни одна из инструкций в пакете не может быть использована в структуре плана, выдается сообщение об ошибке 1053, а данная инструкция завершается неудачно. Рекомендуется всегда получать дескриптор плана из динамического административного представления sys.dm_exec_query_stats для снижения вероятности возникновения этой ошибки.  
  
> [!IMPORTANT]  
>  Процедура sp_create_plan_guide_from_handle создает структуры планов на основе планов в том виде, в каком они находятся в кэше планов. Это означает, что текст пакета, инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] и XML Showplan извлекаются посимвольно (включая любые литеральные значения, переданные запросу) из кэша планов в результирующую структуру плана. Эти текстовые строки могут содержать конфиденциальные сведения, которые затем сохраняются в метаданных базы данных. Пользователи с соответствующими разрешениями могут просматривать эту информацию с помощью представления каталога sys.plan_guides и **свойства структуры плана** диалогового окна в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Чтобы не допустить раскрытия конфиденциальных сведений через руководство плана, рекомендуется проверять руководства плана, созданные из кэша планов, на их наличие.  
  
## <a name="creating-plan-guides-for-multiple-statements-within-a-query-plan"></a>Создание руководств планов для нескольких инструкций в рамках плана запроса  
 Как и sp_create_plan_guide, процедура sp_create_plan_guide_from_handle удаляет план запроса для целевого пакета или модуля из кэша планов. Таким образом обеспечивается использование всеми пользователями новой структуры плана. При создании структуры плана для нескольких инструкций в рамках одного плана запроса можно отложить удаление плана из кэша с помощью создания всех структур плана в явной транзакции. Этот метод позволяет сохранить план в кэше до завершения транзакции и создания структуры плана для каждой указанной инструкции. См. пример Б.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW SERVER STATE. Кроме того, требуются отдельные разрешения на каждую структуру плана, создаваемую с помощью хранимой процедуры sp_create_plan_guide_from_handle. Для создания руководства плана типа OBJECT необходимо разрешение ALTER на соответствующий объект. Чтобы создать структуру плана типа SQL или TEMPLATE, необходимо обладать разрешением ALTER на текущую базу данных. Чтобы определить тип создаваемой структуры плана, выполните следующий запрос.  
  
```  
SELECT cp.plan_handle, sql_handle, st.text, objtype   
FROM sys.dm_exec_cached_plans AS cp  
JOIN sys.dm_exec_query_stats AS qs ON cp.plan_handle = qs.plan_handle  
CROSS APPLY sys.dm_exec_sql_text(sql_handle) AS st;  
```  
  
 В строке, содержащей инструкцию, для которой создается структура плана, исследуйте столбец `objtype` в результирующем наборе. Значение `Proc` указывает на то, что структура плана имеет тип OBJECT. Другие значения, например `AdHoc` или `Prepared`, указывают на принадлежность структуры плана к типу SQL.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-plan-guide-from-a-query-plan-in-the-plan-cache"></a>A. Создание руководства плана из плана запроса в кэше планов  
 В следующем примере создается структура плана для отдельной инструкции SELECT путем указания плана запроса из кэша планов. Пример начинается с выполнения простой инструкции `SELECT`, для которой была создана структура плана. План для этого запроса исследуется с помощью динамических административных представлений `sys.dm_exec_sql_text` и `sys.dm_exec_text_query_plan`. Затем структура плана создается для запроса с указанием плана запроса в кэше планов, связанном с данным запросом. Последняя инструкция в примере осуществляет проверку существования структуры плана.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT WorkOrderID, p.Name, OrderQty, DueDate  
FROM Production.WorkOrder AS w   
JOIN Production.Product AS p ON w.ProductID = p.ProductID  
WHERE p.ProductSubcategoryID > 4  
ORDER BY p.Name, DueDate;  
GO  
-- Inspect the query plan by using dynamic management views.  
SELECT * FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_sql_text(sql_handle)  
CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, qs.statement_start_offset, qs.statement_end_offset) AS qp  
WHERE text LIKE N'SELECT WorkOrderID, p.Name, OrderQty, DueDate%';  
GO  
-- Create a plan guide for the query by specifying the query plan in the plan cache.  
DECLARE @plan_handle varbinary(64);  
DECLARE @offset int;  
SELECT @plan_handle = plan_handle, @offset = qs.statement_start_offset  
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_sql_text(sql_handle) AS st  
CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, qs.statement_start_offset, qs.statement_end_offset) AS qp  
WHERE text LIKE N'SELECT WorkOrderID, p.Name, OrderQty, DueDate%';  
  
EXECUTE sp_create_plan_guide_from_handle   
    @name =  N'Guide1',  
    @plan_handle = @plan_handle,  
    @statement_start_offset = @offset;  
GO  
-- Verify that the plan guide is created.  
SELECT * FROM sys.plan_guides  
WHERE scope_batch LIKE N'SELECT WorkOrderID, p.Name, OrderQty, DueDate%';  
GO  
```  
  
### <a name="b-creating-multiple-plan-guides-for-a-multistatement-batch"></a>Б. Создание нескольких руководств планов для пакета из нескольких инструкций  
 В следующем примере создается структура плана для двух инструкций, входящих в пакет из нескольких инструкций. Структуры планов создаются в явной транзакции, поэтому план запроса для пакета не удаляется из кэша планов после создания первой структуры плана. Пример начинается с выполнения пакета из нескольких инструкций. План для пакета исследуется с помощью динамических административных представлений. Обратите внимание, что возвращается строка для каждой инструкции в пакете. Затем создается структура плана для первой и третьей инструкций в пакете путем указания параметра `@statement_start_offset`. Последняя инструкция в примере осуществляет проверку существования структур плана.  
  
 [!code-sql[PlanGuides#Create_From_Handle2](../../relational-databases/system-stored-procedures/codesnippet/tsql/sp-create-plan-guide-fro_1.sql)]  
  
## <a name="see-also"></a>См. также  
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 [Структуры планов](../../relational-databases/performance/plan-guides.md)   
 [sp_create_plan_guide (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_exec_text_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-text-query-plan-transact-sql.md)   
 [sp_control_plan_guide (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql.md)  
  
  
