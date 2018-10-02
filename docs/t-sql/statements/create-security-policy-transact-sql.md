---
title: CREATE SECURITY POLICY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SECURITY_POLICY_TSQL
- CREATE SECURITY
- SECURITY
- CREATE_SECURITY_POLICY_TSQL
- CREATE_SECURITY_TSQL
- SECURITY POLICY
- SECURITY_TSQL
- CREATE SECURITY POLICY
dev_langs:
- TSQL
helpviewer_keywords:
- RLS
- CREATE SECURITY POLICY statement
- Row-Level Security
ms.assetid: d6ab70ee-0fa2-469c-96f6-a3c16d673bc8
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 8717dd0d083ad218366ae19531dc74caf5b395fd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47686943"
---
# <a name="create-security-policy-transact-sql"></a>CREATE SECURITY POLICY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Создает политику безопасности для безопасности на уровне строки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```     
CREATE SECURITY POLICY [schema_name. ] security_policy_name    
    { ADD [ FILTER | BLOCK ] } PREDICATE tvf_schema_name.security_predicate_function_name   
      ( { column_name | expression } [ , …n] ) ON table_schema_name. table_name    
      [ <block_dml_operation> ] , [ , …n] 
    [ WITH ( STATE = { ON | OFF }  [,] [ SCHEMABINDING = { ON | OFF } ] ) ]  
    [ NOT FOR REPLICATION ] 
[;]  
  
<block_dml_operation>  
    [ { AFTER { INSERT | UPDATE } }   
    | { BEFORE { UPDATE | DELETE } } ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *security_policy_name*  
 Имя политики безопасности. Имена политик безопасности должны удовлетворять правилам построения идентификаторов и должны быть уникальными в пределах базы данных и схемы.  
  
 *schema_name*  
 Имя схемы, которой принадлежит политика безопасности. Аргумент *schema_name* необходим из-за привязки к схеме.  
  
 [ FILTER | BLOCK ]  
 Тип предиката безопасности для функции, которая привязывается к целевой таблице. Предикаты FILTER автоматически фильтруют строки, доступные для операций чтения. Предикаты BLOCK явным образом блокируют операции записи, нарушающие функции предиката.  
  
 *tvf_schema_name.security_predicate_function_name*  
 Это встроенная функция, возвращающая табличное значение, которое будет использоваться в качестве предиката и применяться при запросах к целевой таблице. Для конкретной операции DML в определенной таблице можно задать не более одного предиката безопасности. Эта встроенная функция табличного значения должна быть создана с помощью параметра SCHEMABINDING.  
  
 { *имя_столбца* | *выражение* }  
 Имя столбца или выражение, используемое в качестве параметров функции предиката безопасности. Можно использовать любой столбец в целевой таблице. [Выражение](../../t-sql/language-elements/expressions-transact-sql.md) может содержать только константы, встроенные в скалярные функции, операторы и столбцы из целевой таблицы. Для каждого параметра функции нужно указать имя столбца или выражения.  
  
 *table_schema_name.table_name*  
 Представляет целевую таблицу, к которой будет применяться предикат безопасности. Для одной таблицы для конкретной операции DML могут быть предназначены несколько отключенных политик безопасности, но только одна может быть включена в любой момент времени.  
  
 *\<block_dml_operation>* Конкретная операция DML, для которой применяется предикат блокировки. AFTER указывает, что предикат вычисляется по значениям строк после выполнения операции DML (INSERT или UPDATE). BEFORE указывает, что предикат вычисляется по значениям строк до выполнения операции DML (UPDATE или DELETE). Если операция не указана, предикат будет применяться ко всем операциям.  
  
 [ STATE = { ON | **OFF** } ]  
 Включает или отключает политику безопасности для обеспечения применения ее предикатов безопасности в отношении целевых таблиц. Если этот аргумент не указан, создаваемая политика безопасности будет отключена.  
  
 [ SCHEMABINDING = { ON | OFF } ]  
 Указывает, должны ли все функции предиката быть созданы с помощью параметра SCHEMABINDING. По умолчанию все функции должны быть созданы с помощью параметра SCHEMABINDING.  
  
 NOT FOR REPLICATION  
 Указывает, что политика безопасности не должна выполняться, когда агент репликации изменяет целевой объект. Дополнительные сведения см. в статье [Управление поведением триггеров и ограничений во время синхронизации (программирование репликации на языке Transact-SQL)](../../relational-databases/replication/control-behavior-of-triggers-and-constraints-in-synchronization.md).  
  
 [*table_schema_name*.] *table_name*  
 Представляет целевую таблицу, к которой будет применяться предикат безопасности. Для одной таблицы могут быть предназначены несколько отключенных политик безопасности, но только одна может быть включена в любой момент времени.  
  
## <a name="remarks"></a>Remarks  
 При использовании функций предикатов с таблицами, оптимизированными для памяти, необходимо включить параметр **SCHEMABINDING** и использовать указание компиляции **WITH NATIVE_COMPILATION**.  
  
 Предикаты блокировки вычисляются после выполнения соответствующей операции DML. Таким образом, запросу READ UNCOMMITTED будут доступны временные значения, для которых будет выполнен откат.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение ALTER ANY SECURITY POLICY и разрешение ALTER в схеме.  
  
 Кроме того, для каждого добавляемого предиката требуются следующие разрешения:  
  
-   разрешения SELECT и REFERENCES для функции, которая должна использоваться в качестве предиката;  
  
-   разрешение REFERENCES для целевой таблицы, которая привязывается к политике;  
  
-   разрешение REFERENCES в каждом столбце из целевой таблицы, используемом в качестве аргумента.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах демонстрируется использование синтаксиса **CREATE SECURITY POLICY** . Пример полного сценария политики безопасности см. в разделе [Безопасность на уровне строк](../../relational-databases/security/row-level-security.md).  
  
### <a name="a-creating-a-security-policy"></a>A. Создание политики безопасности  
 Следующий синтаксис создает политику безопасности с предикатом фильтра для таблицы Customer и оставляет политику безопасности отключенной.  
  
```  
CREATE SECURITY POLICY [FederatedSecurityPolicy]   
ADD FILTER PREDICATE [rls].[fn_securitypredicate]([CustomerId])   
ON [dbo].[Customer];  
```  
  
### <a name="b-creating-a-policy-that-affects-multiple-tables"></a>Б. Создание политики, влияющей на несколько таблиц  
 Следующий синтаксис создает политику безопасности с тремя предикатами фильтров в трех разных таблицах и включает политику безопасности.  
  
```  
CREATE SECURITY POLICY [FederatedSecurityPolicy]   
ADD FILTER PREDICATE [rls].[fn_securitypredicate1]([CustomerId])   
    ON [dbo].[Customer],  
ADD FILTER PREDICATE [rls].[fn_securitypredicate1]([VendorId])   
    ON [dbo].[ Vendor],  
ADD FILTER PREDICATE [rls].[fn_securitypredicate2]([WingId])   
    ON [dbo].[Patient]  
WITH (STATE = ON);  
```  
  
### <a name="c-creating-a-policy-with-multiple-types-of-security-predicates"></a>В. Создание политики с несколькими типами предикатов безопасности  
 Добавление предиката фильтра и предиката блокировки в таблицу Sales.  
  
```  
CREATE SECURITY POLICY rls.SecPol  
    ADD FILTER PREDICATE rls.tenantAccessPredicate(TenantId) ON dbo.Sales,  
    ADD BLOCK PREDICATE rls.tenantAccessPredicate(TenantId) ON dbo.Sales AFTER INSERT;  
```  
  
## <a name="see-also"></a>См. также:  
 [Безопасность на уровне строк](../../relational-databases/security/row-level-security.md)   
 [ALTER SECURITY POLICY (Transact-SQL)](../../t-sql/statements/alter-security-policy-transact-sql.md)   
 [DROP SECURITY POLICY (Transact-SQL)](../../t-sql/statements/drop-security-policy-transact-sql.md)   
 [sys.security_policies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [sys.security_predicates (Transact-SQL)](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)  
  
  

