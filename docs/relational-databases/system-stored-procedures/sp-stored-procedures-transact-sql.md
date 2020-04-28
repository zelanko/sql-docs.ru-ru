---
title: sp_stored_procedures (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_stored_procedures_TSQL
- sp_stored_procedures
dev_langs:
- TSQL
helpviewer_keywords:
- sp_stored_procedures
ms.assetid: fe52dd83-000a-4665-83fb-7a0024193dec
author: stevestein
ms.author: sstein
ms.openlocfilehash: 554b9317d6b474b23e9dbbc10dea03156ccc6287
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68702787"
---
# <a name="sp_stored_procedures-transact-sql"></a>sp_stored_procedures (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
`[ @sp_name = ] 'name'`Имя процедуры, используемой для возврата сведений о каталоге. *имя* имеет тип **nvarchar (390)** и значение по умолчанию NULL. Поиск совпадений по шаблону поддерживается.  
  
`[ @sp_owner = ] 'schema'`Имя схемы, которой принадлежит процедура. *Schema* имеет тип **nvarchar (384)** и значение по умолчанию NULL. Поиск совпадений по шаблону поддерживается. Если параметр *owner* не указан, применяются правила видимости процедур по умолчанию базовой СУБД.  
  
 Если текущая схема содержит процедуру с указанным именем, в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращается эта процедура. Если указана неквалифицированная хранимая процедура, [!INCLUDE[ssDE](../../includes/ssde-md.md)] выполняет поиск процедуры в следующем порядке:  
  
-   схема **sys** текущей базы данных;  
  
-   схема участника по умолчанию, если она выполняется в пакете или в динамическом SQL; или, если неуточненное имя процедуры появляется внутри определения другой процедуры, далее происходит поиск по схеме, содержащей эту процедуру.  
  
-   Схема **dbo** в текущей базе данных.  
  
`[ @qualifier = ] 'qualifier'`Имя квалификатора процедуры. *квалификатор* имеет тип **sysname**и значение по умолчанию NULL. Различные продукты СУБД поддерживают имена таблиц в формате, состоящие из трех частей (_квалификатор_**.** _схема_**.** _имя_. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *квалификатор* представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, в которой находится таблица.  
  
`[ @fUsePattern = ] 'fUsePattern'`Определяет, будут ли символы подчеркивания (_), процента (%) или квадратных скобок []) интерпретироваться как подстановочные знаки. *фусепаттерн* имеет **бит**и значение по умолчанию 1.  
  
 **0** = сопоставление шаблонов отключено.  
  
 **1** = сопоставление по шаблону включено.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**PROCEDURE_QUALIFIER**|**sysname**|Имя квалификатора процедуры. Этот столбец может принимать значение NULL.|  
|**PROCEDURE_OWNER**|**sysname**|Имя владельца процедуры. Этот столбец всегда возвращает значение.|  
|**PROCEDURE_NAME**|**nvarchar (134)**|Имя процедуры. Этот столбец всегда возвращает значение.|  
|**NUM_INPUT_PARAMS**|**int**|Зарезервировано для последующего использования.|  
|**NUM_OUTPUT_PARAMS**|**int**|Зарезервировано для последующего использования.|  
|**NUM_RESULT_SETS**|**int**|Зарезервировано для последующего использования.|  
|**ЗАМЕЧАНИЯ**|**varchar (254)**|Описание процедуры. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не возвращает значение для этого столбца.|  
|**PROCEDURE_TYPE**|**smallint**|Тип процедуры. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] всегда возвращает 2.0. Значение может быть одним из следующих.<br /><br /> 0 = SQL_PT_UNKNOWN;<br /><br /> 1 = SQL_PT_PROCEDURE;<br /><br /> 2 = SQL_PT_FUNCTION.|  
  
## <a name="remarks"></a>Remarks  
 Для максимальной совместимости клиент шлюза должен принимать только сопоставление шаблонов стандарта SQL (символы-шаблоны «%» и «_»).  
  
 Сведения о разрешении на выполнение определенной хранимой процедуры для текущего пользователя не обязательно проверяются, поэтому доступ не гарантируется. Обратите внимание, что используются только трехкомпонентные имена. Это означает, что возвращаются только локальные хранимые процедуры, а не удаленные хранимые процедуры (которые используют четырехкомпонентные имена), выполняемые на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если атрибут сервера ACCESSIBLE_SPROC имеет значение Y в результирующем наборе для **sp_server_info**, возвращаются только хранимые процедуры, которые могут быть выполнены текущим пользователем.  
  
 **sp_stored_procedures** эквивалентен **SQLProcedures** в ODBC. Возвращаемые результаты упорядочиваются по **PROCEDURE_QUALIFIER**, **PROCEDURE_OWNER**и **procedure_name**.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-all-stored-procedures-in-the-current-database"></a>A. Возвращение всех хранимых процедур в текущей базе данных  
 В следующем примере возвращаются все хранимые процедуры в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_stored_procedures;  
```  
  
### <a name="b-returning-a-single-stored-procedure"></a>Б) Возвращение одной хранимой процедуры  
 В следующем примере возвращается результирующий набор для хранимой процедуры `uspLogError`.  
  
```  
USE AdventureWorks2012;  
GO  
sp_stored_procedures N'uspLogError', N'dbo', N'AdventureWorks2012', 1;  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры каталога &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
