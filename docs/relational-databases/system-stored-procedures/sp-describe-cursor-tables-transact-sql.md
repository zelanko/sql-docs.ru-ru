---
title: sp_describe_cursor_tables (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_describe_cursor_tables_TSQL
- sp_describe_cursor_tables
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_cursor_tables
ms.assetid: 02c0f81a-54ed-4ca4-aa4f-bb7463a9ab9a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5c005ff603f21dca387215cafd9dff572db53960
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053096"
---
# <a name="sp_describe_cursor_tables-transact-sql"></a>sp_describe_cursor_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выводит объекты или базовые таблицы, на которые ссылается серверный курсор.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_describe_cursor_tables   
     [ @cursor_return = ] output_cursor_variable OUTPUT   
     { [ , [ @cursor_source = ] N'local'  
     , [ @cursor_identity = ] N'local_cursor_name' ]   
   | [ , [ @cursor_source = ] N'global'  
     , [ @cursor_identity = ] N'global_cursor_name' ]   
   | [ , [ @cursor_source = ] N'variable'  
     , [ @cursor_identity = ] N'input_cursor_variable' ]   
     }   
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @cursor_return= ] *output_cursor_variable* ПРОВЕРКИ  
 Имя объявленной переменной для получения выходных данных курсора. *output_cursor_variable* является **курсором**, не имеет значения по умолчанию и не должен быть связан ни с одним курсором во время вызова sp_describe_cursor_tables. Возвращаемый курсор является прокручиваемым, динамическим и доступным только для чтения.  
  
 [ @cursor_source= ] {Н'локал ' | Н'глобал ' | Н'вариабле "}  
 Указывает, задан ли возвращаемый курсор с помощью имени локального курсора, глобального курсора или курсорной переменной. Параметр имеет тип **nvarchar (30)**.  
  
 [ @cursor_identity= ] N "*local_cursor_name*"  
 Имя курсора, созданного с помощью инструкции DECLARE CURSOR c ключевым словом LOCAL или параметром LOCAL по умолчанию. *local_cursor_name* имеет тип **nvarchar (128)**.  
  
 [ @cursor_identity= ] N "*global_cursor_name*"  
 Имя курсора, созданного с помощью инструкции DECLARE CURSOR с ключевым словом GLOBAL или параметром GLOBAL по умолчанию. *global_cursor_name* также может быть именем серверного курсора API, открытого приложением ODBC, которое затем наименует курсор путем вызова SQLSetCursorName. *global_cursor_name* имеет тип **nvarchar (128)**.  
  
 [ @cursor_identity= ] N "*input_cursor_variable*"  
 Имя переменной курсора, связанной с открытым курсором. *input_cursor_variable* имеет тип **nvarchar (128)**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="cursors-returned"></a>Возвращенные курсоры  
 sp_describe_cursor_tables инкапсулирует свой отчет в качестве [!INCLUDE[tsql](../../includes/tsql-md.md)] выходного параметра **курсора** . Это позволяет пакетам [!INCLUDE[tsql](../../includes/tsql-md.md)], хранимым процедурам и триггерам построчно обрабатывать выходные данные. Это также означает, что процедуру нельзя вызвать напрямую из функций API-интерфейса. Параметр вывода **курсора** должен быть привязан к программной переменной, но интерфейсы API не поддерживают привязку параметров или переменных **курсора** .  
  
 В следующей таблице показан формат курсора, возвращенного процедурой sp_describe_cursor_tables.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|table owner|**имеет sysname**|Идентификатор пользователя владельца таблицы.|  
|Table_name|**имеет sysname**|Имя объекта или базовой таблицы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] серверные курсоры всегда возвращают объекты, определенные пользователем, а не базовые таблицы.|  
|Optimizer_hints|**smallint**|Битовая карта одного или нескольких следующих значений.<br /><br /> 1 = Блокировка на уровне строк (ROWLOCK).<br /><br /> 4 = Блокировка на уровне страниц (ROWLOCK).<br /><br /> 8 = Блокировка таблицы (TABLOCK).<br /><br /> 16 = Монопольная блокировка таблицы (TABLOCKX).<br /><br /> 32 = Блокировка обновления (UPDLOCK).<br /><br /> 64 = Нет блокировки (NOLOCK).<br /><br /> 128 = Параметр перемотки первой строки (FASTFIRST).<br /><br /> 4096 = Считать повторяемую семантику с помощью DECLARE CURSOR (HOLDLOCK).<br /><br /> При предоставлении нескольких параметров система использует параметр с наибольшими ограничениями. Однако процедура sp_describe_cursor_tables отображает флаги, которые указываются в запросе.|  
|lock_type|**smallint**|Тип блокировки прокрутки, запрашиваемый явно или неявно для каждой базовой таблицы, на которой основан данный курсор. Принимается одно из следующих значений:<br /><br /> 0 = нет<br /><br /> 1 = общее<br /><br /> 3 = обновление|  
|server_name|**sysname, Nullable**|Имя связанного сервера, на котором находится таблица. NULL, если используются предложения OPENQUERY или OPENROWSET.|  
|Objectid|**int**|Идентификатор объекта таблицы. 0, если используются предложения OPENQUERY или OPENROWSET.|  
|dbid|**int**|Идентификатор базы данных, в которой расположена указанная таблица. 0, если используются предложения OPENQUERY или OPENROWSET.|  
|dbname|**sysname**, **Nullable**|Имя базы данных, в которой расположена указанная таблица. NULL, если используются предложения OPENQUERY или OPENROWSET.|  
  
## <a name="remarks"></a>Remarks  
 Процедура sp_describe_cursor_tables описывает базовые таблицы, на которые ссылается серверный курсор. Используйте процедуру sp_describe_cursor_columns для описания атрибутов результирующего набора, возвращаемого курсором. Для описания общих характеристик курсора, таких как прокручивание и возможность обновления, используйте процедуру sp_describe_cursor. Для получения списка серверных курсоров [!INCLUDE[tsql](../../includes/tsql-md.md)], видимых при соединении, используйте процедуру sp_cursor_list.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
 В следующем примере открывается глобальный курсор, а затем с помощью процедуры `sp_describe_cursor_tables` выводится список таблиц, на которые курсор ссылается.  
  
```  
USE AdventureWorks2012;  
GO  
-- Declare and open a global cursor.  
DECLARE abc CURSOR KEYSET FOR  
SELECT LastName  
FROM Person.Person  
WHERE LastName LIKE 'S%';  
  
OPEN abc;  
GO  
-- Declare a cursor variable to hold the cursor output variable  
-- from sp_describe_cursor_tables.  
DECLARE @Report CURSOR;  
  
-- Execute sp_describe_cursor_tables into the cursor variable.  
EXEC master.dbo.sp_describe_cursor_tables  
      @cursor_return = @Report OUTPUT,  
      @cursor_source = N'global', @cursor_identity = N'abc';  
  
-- Fetch all the rows from the sp_describe_cursor_tables output cursor.  
FETCH NEXT from @Report;  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN  
   FETCH NEXT from @Report;  
END  
  
-- Close and deallocate the cursor from sp_describe_cursor_tables.  
CLOSE @Report;  
DEALLOCATE @Report;  
GO  
  
-- Close and deallocate the original cursor.  
CLOSE abc;  
DEALLOCATE abc;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Курсоры](../../relational-databases/cursors.md)   
 [CURSOR_STATUS &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-status-transact-sql.md)   
 [ОБЪЯВИТь курсор &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [sp_cursor_list &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursor-list-transact-sql.md)   
 [sp_describe_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-transact-sql.md)   
 [sp_describe_cursor_columns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-columns-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
