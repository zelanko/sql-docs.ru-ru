---
title: "Создание ПОЛИТИКИ безопасности (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 53292dc3f9f5cbd36913276496084d4648f13520
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-security-policy-transact-sql"></a>Создание ПОЛИТИКИ безопасности (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Создает политику безопасности для безопасности на уровне строк.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```     
CREATE SECURITY POLICY [schema_name. ] security_policy_name    
    { ADD [ FILTER | BLOCK ] } PREDICATE tvf_schema_name.security_predicate_function_name   
      ( { column_name | arguments } [ , …n] ) ON table_schema_name. table_name    
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
 Имя схемы, которой принадлежит политика безопасности. *schema_name* требуется из-за привязки к схеме.  
  
 [ФИЛЬТР | БЛОК]  
 Тип предиката безопасности для функции, которая привязывается к целевой таблице. Предикаты ФИЛЬТРОВ автоматически фильтруют строки, которые доступны для операций чтения. БЛОК явно предикаты блок операций записи, нарушающие функции предиката.  
  
 *tvf_schema_name.security_predicate_function_name*  
 Это встроенная функция, возвращающая табличное значение, которое будет использоваться в качестве предиката и применяться при запросах к целевой таблице. Для конкретной операции DML в определенной таблице можно задать не более одного предиката безопасности. Эта встроенная функция табличного значения должна быть создана с помощью параметра SCHEMABINDING.  
  
 { *column_name* | *аргументы* }  
 Имя столбца или выражение, используемое в качестве параметров функции предиката безопасности. Любые столбцы в целевой таблице можно использовать как аргументы для функции предиката. Можно использовать выражения, которые включают литералы, встроенные объекты и выражения с арифметическими операторами.  
  
 *table_schema_name.table_name*  
 Представляет целевую таблицу, к которой будет применяться предикат безопасности. Несколько отключенных политик безопасности можно выбрать целевую одной таблицы для конкретной операции DML, но только одна может быть включена в любой момент времени.  
  
 *\<block_dml_operation >* конкретной операции DML, для которой применяется предикат блока. После указывает, что предикат вычисляется по значениям строк после операции DML было выполнено (INSERT или UPDATE). Перед указывает, что предикат будет определяться значения строк, прежде чем операция DML не выполнено (UPDATE или DELETE). Если ни одна из операций не указан, предикат будут применяться ко всем операциям.  
  
 [СОСТОЯНИЕ = {ON | **OFF** }]  
 Включает или отключает политику безопасности для обеспечения применения ее предикатов безопасности в отношении целевых таблиц. Если этот аргумент не указан, создаваемая политика безопасности будет отключена.  
  
 [SCHEMABINDING = {ON | {OFF}]  
 Указывает, является ли все функции предиката, в политике должна быть создана с параметром SCHEMABINDING. По умолчанию все функции должны быть созданы с параметром SCHEMABINDING.  
  
 NOT FOR REPLICATION  
 Указывает, что политика безопасности не должна выполняться, когда агент репликации изменяет целевой объект. Дополнительные сведения см. в статье [Управление поведением триггеров и ограничений во время синхронизации (программирование репликации на языке Transact-SQL)](../../relational-databases/replication/control-behavior-of-triggers-and-constraints-in-synchronization.md).  
  
 [*table_schema_name*.] *имя_таблицы*  
 Представляет целевую таблицу, к которой будет применяться предикат безопасности. Для одной таблицы могут быть предназначены несколько отключенных политик безопасности, но только одна может быть включена в любой момент времени.  
  
## <a name="remarks"></a>Замечания  
 При использовании функции предикатов с таблицами, оптимизированными для памяти, необходимо включить **SCHEMABINDING** и использовать **WITH NATIVE_COMPILATION** указание компиляции.  
  
 Предикаты блокировки вычисляются после выполнения операции DML. Таким образом запрос READ UNCOMMITTED отображаются временные значения, будет выполнен откат.  
  
## <a name="permissions"></a>Permissions  
 Требуется разрешение ALTER ANY SECURITY POLICY и разрешение ALTER в схеме.  
  
 Кроме того, для каждого добавляемого предиката требуются следующие разрешения:  
  
-   разрешения SELECT и REFERENCES для функции, которая должна использоваться в качестве предиката;  
  
-   разрешение REFERENCES для целевой таблицы, которая привязывается к политике;  
  
-   разрешение REFERENCES в каждом столбце из целевой таблицы, используемом в качестве аргумента.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах демонстрируется использование синтаксиса **CREATE SECURITY POLICY** . Пример полного сценария политики безопасности см. в разделе [безопасность на уровне строк](../../relational-databases/security/row-level-security.md).  
  
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
 Добавление предиката фильтра и предиката блокировки для таблицы Sales.  
  
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
 [sys.security_predicates &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)  
  
  


