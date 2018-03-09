---
title: "sp_stored_procedures (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_stored_procedures_TSQL
- sp_stored_procedures
dev_langs:
- TSQL
helpviewer_keywords:
- sp_stored_procedures
ms.assetid: fe52dd83-000a-4665-83fb-7a0024193dec
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c71f292c8d6d1b93e73b028ed6d2fc75e944386c
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spstoredprocedures-transact-sql"></a>sp_stored_procedures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает список всех хранимых процедур в текущем окружении.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_stored_procedures [ [ @sp_name = ] 'name' ]   
    [ , [ @sp_owner = ] 'schema']   
    [ , [ @sp_qualifier = ] 'qualifier' ]  
    [ , [@fUsePattern = ] 'fUsePattern' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@sp_name =** ] **"***имя***"**  
 Название процедуры, используемой для возврата сведений о каталоге. *имя* — **nvarchar(390)**, значение по умолчанию NULL. Поиск совпадений по шаблону поддерживается.  
  
 [  **@sp_owner =** ] **"***схемы***"**  
 Имя схемы, которой принадлежит процедура. *схемы* — **nvarchar(384)**, значение по умолчанию NULL. Поиск совпадений по шаблону поддерживается. Если *владельца* не указан, применяются правила видимости процедуры по умолчанию базовой СУБД.  
  
 Если текущая схема содержит процедуру с указанным именем, в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращается эта процедура. Если указано уточненное имя хранимой процедуры, [!INCLUDE[ssDE](../../includes/ssde-md.md)] производит поиск процедуры в следующем порядке:  
  
-   схема **sys** текущей базы данных;  
  
-   схема участника по умолчанию, если она выполняется в пакете или в динамическом SQL; или, если неуточненное имя процедуры появляется внутри определения другой процедуры, далее происходит поиск по схеме, содержащей эту процедуру.  
  
-   Схема **dbo** в текущей базе данных.  
  
 [  **@qualifier =** ] **"***квалификатор***"**  
 Имя квалификатора процедуры. *квалификатор* — **sysname**, значение по умолчанию NULL. Различные продукты СУБД поддерживают трехкомпонентные имена таблиц в форме (*квалификатор***.** *схемы***.** *имя*. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], *квалификатор* представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, в которой находится таблица.  
  
 [  **@fUsePattern =** ] **"***шаблонов***"**  
 Определяет, должны ли символы подчеркивания (_), процента (%) и квадратных скобок ([ ]) рассматриваться как подстановочные. *Шаблонов* — **бит**, значение по умолчанию 1.  
  
 **0** = шаблон сопоставление отключено.  
  
 **1** = шаблон сопоставление включено.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**PROCEDURE_QUALIFIER**|**sysname**|Имя квалификатора процедуры. Этот столбец может принимать значение NULL.|  
|**PROCEDURE_OWNER**|**sysname**|Имя владельца процедуры. Этот столбец всегда возвращает значение.|  
|**PROCEDURE_NAME**|**nvarchar(134)**|Имя процедуры. Этот столбец всегда возвращает значение.|  
|**NUM_INPUT_PARAMS**|**int**|Зарезервировано для последующего использования.|  
|**NUM_OUTPUT_PARAMS**|**int**|Зарезервировано для последующего использования.|  
|**NUM_RESULT_SETS**|**int**|Зарезервировано для последующего использования.|  
|**ПРИМЕЧАНИЯ**|**varchar(254)**|Описание процедуры. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не возвращает значение для этого столбца.|  
|**PROCEDURE_TYPE**|**smallint**|Тип процедуры. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда возвращает 2.0. Значение может быть одним из следующих.<br /><br /> 0 = SQL_PT_UNKNOWN;<br /><br /> 1 = SQL_PT_PROCEDURE;<br /><br /> 2 = SQL_PT_FUNCTION.|  
  
## <a name="remarks"></a>Замечания  
 Для максимальной совместимости клиент шлюза должен принимать только сопоставление шаблонов стандарта SQL (символы-шаблоны «%» и «_»).  
  
 Сведения о разрешении на выполнение определенной хранимой процедуры для текущего пользователя не обязательно проверяются, поэтому доступ не гарантируется. Обратите внимание, что используются только трехкомпонентные имена. Это означает, что возвращаются только локальные хранимые процедуры, а не удаленные хранимые процедуры (которые используют четырехкомпонентные имена), выполняемые на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если серверного атрибута ACCESSIBLE_SPROC равно Y в результирующем наборе для **sp_server_info**, возвращаются только хранимые процедуры, которые могут быть выполнены текущим пользователем.  
  
 **sp_stored_procedures** эквивалентно **SQLProcedures** в ODBC. Возвращенные результаты сортируются по **PROCEDURE_QUALIFIER**, **PROCEDURE_OWNER**, и **имя_процедуры**.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-all-stored-procedures-in-the-current-database"></a>A. Возвращение всех хранимых процедур в текущей базе данных  
 В следующем примере возвращаются все хранимые процедуры в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_stored_procedures;  
```  
  
### <a name="b-returning-a-single-stored-procedure"></a>Б. Возвращение одной хранимой процедуры  
 В следующем примере возвращается результирующий набор для хранимой процедуры `uspLogError`.  
  
```  
USE AdventureWorks2012;  
GO  
sp_stored_procedures N'uspLogError', N'dbo', N'AdventureWorks2012', 1;  
```  
  
## <a name="see-also"></a>См. также:  
 [Каталога хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
