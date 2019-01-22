---
title: ALTER SECURITY POLICY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER_SECURITY_POLICY_TSQL
- ALTER SECURITY POLICY
- ALTER_SECURITY_TSQL
- ALTER SECURITY
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER SECURITY POLICY statement
ms.assetid: a8efc37e-113d-489c-babc-b914fea2c316
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 5eb2b34e078d6fa48b3b9bc8e0be6b1b6c367732
ms.sourcegitcommit: 9c99f992abd5f1c174b3d1e978774dffb99ff218
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361514"
---
# <a name="alter-security-policy-transact-sql"></a>ALTER SECURITY POLICY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Изменяет политику безопасности.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
ALTER SECURITY POLICY schema_name.security_policy_name   
    (  
        { ADD { FILTER | BLOCK } PREDICATE tvf_schema_name.security_predicate_function_name   
           ( { column_name | arguments } [ , ...n ] ) ON table_schema_name.table_name   
           [ <block_dml_operation> ]  }   
        | { ALTER { FILTER | BLOCK } PREDICATE tvf_schema_name.new_security_predicate_function_name   
             ( { column_name | arguments } [ , ...n ] ) ON table_schema_name.table_name   
           [ <block_dml_operation> ] }  
        | { DROP { FILTER | BLOCK } PREDICATE ON table_schema_name.table_name }   
        | [ <additional_add_alter_drop_predicate_statements> [ , ...n ] ]  
    )    [ WITH ( STATE = { ON | OFF } ]  
    [ NOT FOR REPLICATION ]  
[;]  
  
<block_dml_operation>  
    [ { AFTER { INSERT | UPDATE } }   
    | { BEFORE { UPDATE | DELETE } } ]  
```  
  
## <a name="arguments"></a>Аргументы  
 security_policy_name  
 Имя политики безопасности. Имена политик безопасности должны удовлетворять правилам построения идентификаторов и должны быть уникальными в пределах базы данных и схемы.  
  
 schema_name  
 Имя схемы, которой принадлежит политика безопасности. Аргумент *schema_name* необходим из-за привязки к схеме.  
  
 [ FILTER | BLOCK ]  
 Тип предиката безопасности для функции, которая привязывается к целевой таблице. Предикаты FILTER автоматически фильтруют строки, доступные для операций чтения. Предикаты BLOCK явным образом блокируют операции записи, нарушающие функции предиката.  
  
 tvf_schema_name.security_predicate_function_name  
 Это встроенная функция, возвращающая табличное значение, которое будет использоваться в качестве предиката и применяться при запросах к целевой таблице. Для конкретной операции DML в определенной таблице можно задать не более одного предиката безопасности. Эта встроенная функция табличного значения должна быть создана с помощью параметра SCHEMABINDING.  
  
 { column_name | arguments }  
 Имя столбца или выражение, используемое в качестве параметров функции предиката безопасности. Любые столбцы в целевой таблице можно использовать как аргументы для функции предиката. Можно использовать выражения, которые включают литералы, встроенные объекты и выражения с арифметическими операторами.  
  
 *table_schema_name.table_name*  
 Представляет целевую таблицу, к которой будет применяться предикат безопасности. Для одной таблицы для конкретной операции DML могут быть предназначены несколько отключенных политик безопасности, но только одна может быть включена в любой момент времени.  
  
 *\<block_dml_operation>*  
 Конкретная операция DML, для которой применяется предикат блокировки. AFTER указывает, что предикат вычисляется по значениям строк после выполнения операции DML (INSERT или UPDATE). BEFORE указывает, что предикат вычисляется по значениям строк до выполнения операции DML (UPDATE или DELETE). Если операция не указана, предикат будет применяться ко всем операциям.  
  
 Изменить операцию, для которой применяется предикат блокирования, с помощью инструкции ALTER невозможно, так как эта операция используется для уникальной идентификации предиката. Вместо этого необходимо удалить предикат и добавить новый для новой операции.  
  
 WITH (STATE = {ON | OFF})  
 Включает или отключает политику безопасности для обеспечения применения ее предикатов безопасности в отношении целевых таблиц. Если этот аргумент не указан, создаваемая политика безопасности будет отключена.  
  
 NOT FOR REPLICATION  
 Указывает, что политика безопасности не должна выполняться, когда агент репликации изменяет целевой объект. Дополнительные сведения см. в статье [Управление поведением триггеров и ограничений во время синхронизации (программирование репликации на языке Transact-SQL)](../../relational-databases/replication/control-behavior-of-triggers-and-constraints-in-synchronization.md).  
  
 table_schema_name.table_name  
 Представляет целевую таблицу, к которой будет применяться предикат безопасности. Для одной таблицы могут быть предназначены несколько отключенных политик безопасности, но только одна может быть включена в любой момент времени.  
  
## <a name="remarks"></a>Remarks  
 Инструкция ALTER SECURITY POLICY относится к области транзакции. Если выполняется откат транзакции, происходит также откат этой инструкции.  
  
 При использовании функций предикатов с таблицами, оптимизированными для памяти, политики безопасности должны включать параметр **SCHEMABINDING** и использовать указание компиляции **WITH NATIVE_COMPILATION**. Аргумент SCHEMABINDING невозможно изменить с помощью инструкции ALTER, так как он применяется ко всем предикатам. Чтобы изменить привязку к схеме, необходимо удалить и заново создать политику безопасности.  
  
 Предикаты блокировки вычисляются после выполнения соответствующей операции DML. Таким образом, запросу READ UNCOMMITTED будут доступны временные значения, для которых будет выполнен откат.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER ANY SECURITY POLICY.  
  
 Кроме того, для каждого добавляемого предиката требуются следующие разрешения:  
  
-   разрешения SELECT и REFERENCES для функции, которая должна использоваться в качестве предиката;  
-   разрешение REFERENCES для целевой таблицы, которая привязывается к политике;  
-   разрешение REFERENCES в каждом столбце из целевой таблицы, используемом в качестве аргумента.  
  
## <a name="examples"></a>Примеры  
 В приведенных ниже примерах демонстрируется использование синтаксиса **ALTER SECURITY POLICY**. Пример полного сценария политики безопасности см. в разделе [Безопасность на уровне строк](../../relational-databases/security/row-level-security.md).  
  
### <a name="a-adding-an-additional-predicate-to-a-policy"></a>A. Добавление в политику дополнительного предиката  
 Следующий синтаксис изменяет политику безопасности, добавляя предикат фильтра в таблице `mytable`.  
  
```  
ALTER SECURITY POLICY pol1   
    ADD FILTER PREDICATE schema_preds.SecPredicate(column1)   
    ON myschema.mytable;  
```  
  
### <a name="b-enabling-an-existing-policy"></a>Б. Включение существующей политики  
 В следующем примере выполняется включение политики безопасности с помощью синтаксиса ALTER.  
  
```  
ALTER SECURITY POLICY pol1 WITH ( STATE = ON );  
```  
  
### <a name="c-adding-and-dropping-multiple-predicates"></a>В. Добавление и удаление нескольких предикатов  
 Следующий синтаксис изменяет политику безопасности, добавляя предикаты фильтров в таблицах `mytable1` и `mytable3`, а также удаляя предикат фильтра в таблице `mytable2`.  
  
```  
ALTER SECURITY POLICY pol1  
ADD FILTER PREDICATE schema_preds.SecPredicate1(column1)   
    ON myschema.mytable1,  
DROP FILTER PREDICATE   
    ON myschema.mytable2,  
ADD FILTER PREDICATE schema_preds.SecPredicate2(column2, 1)   
    ON myschema.mytable3;  
```  
  
### <a name="d-changing-the-predicate-on-a-table"></a>Г. Изменение предиката в таблице  
 Следующий синтаксис изменяет существующий предикат фильтра в таблице mytable на функцию SecPredicate2.  
  
```  
ALTER SECURITY POLICY pol1  
    ALTER FILTER PREDICATE schema_preds.SecPredicate2(column1)  
        ON myschema.mytable;  
```  
  
### <a name="e-changing-a-block-predicate"></a>Д. Изменение предиката блокирования  
 Изменение функции предиката блокирования для операции с таблицей.  
  
```  
ALTER SECURITY POLICY rls.SecPol  
    ALTER BLOCK PREDICATE rls.tenantAccessPredicate_v2(TenantId) 
    ON dbo.Sales AFTER INSERT;  
```  
  
## <a name="see-also"></a>См. также:  
 [Безопасность на уровне строк](../../relational-databases/security/row-level-security.md)   
 [CREATE SECURITY POLICY (Transact-SQL)](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [DROP SECURITY POLICY (Transact-SQL)](../../t-sql/statements/drop-security-policy-transact-sql.md)   
 [sys.security_policies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [sys.security_predicates (Transact-SQL)](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)  
  
  
