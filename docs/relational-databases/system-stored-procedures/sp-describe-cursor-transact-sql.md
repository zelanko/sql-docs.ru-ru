---
title: sp_describe_cursor (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_describe_cursor
- sp_describe_cursor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_cursor
ms.assetid: 0c836c99-1147-441e-998c-f0a30cd05275
author: stevestein
ms.author: sstein
ms.openlocfilehash: f82fc9006012d55902f1b5b3260dc7012fd6640a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053076"
---
# <a name="sp_describe_cursor-transact-sql"></a>sp_describe_cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выводит атрибуты серверного курсора.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_describe_cursor [ @cursor_return = ] output_cursor_variable OUTPUT   
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
 Имя объявленной переменной для получения выходных данных курсора. *output_cursor_variable* является **курсором**, не имеет значения по умолчанию и не должен быть связан ни с одним курсором во время вызова sp_describe_cursor. Возвращаемый курсор является прокручиваемым, динамическим и доступным только для чтения.  
  
 [ @cursor_source= ] {Н'локал ' | Н'глобал ' | Н'вариабле "}  
 Указывает, задан ли возвращаемый курсор с помощью имени локального курсора, глобального курсора или курсорной переменной. Параметр имеет тип **nvarchar (30)**.  
  
 [ @cursor_identity= ] N "*local_cursor_name*"]  
 Имя курсора, созданного инструкцией DECLARE CURSOR с ключевым словом LOCAL или параметром LOCAL по умолчанию. *local_cursor_name* имеет тип **nvarchar (128)**.  
  
 [ @cursor_identity= ] N "*global_cursor_name*"]  
 Имя курсора, созданного инструкцией DECLARE CURSOR с ключевым словом GLOBAL или параметром GLOBAL по умолчанию. *global_cursor_name* имеет тип **nvarchar (128)**.  
  
 *global_cursor_name* также может быть именем серверного курсора API, открытого приложением ODBC, которое затем называется путем вызова SQLSetCursorName.  
  
 [ @cursor_identity= ] N "*input_cursor_variable*"]  
 Имя переменной курсора, связанной с открытым курсором. *input_cursor_variable* имеет тип **nvarchar (128)**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="cursors-returned"></a>Возвращенные курсоры  
 sp_describe_cursor инкапсулирует свой результирующий набор в [!INCLUDE[tsql](../../includes/tsql-md.md)] параметре вывода **курсора** . Это позволяет пакетам [!INCLUDE[tsql](../../includes/tsql-md.md)], хранимым процедурам и триггерам построчно обрабатывать выходные данные. Это также означает, что процедуру нельзя вызывать непосредственно из функций API баз данных. Параметр вывода **курсора** должен быть привязан к программной переменной, но API-интерфейсы базы данных не поддерживают привязку параметров или переменных **курсора** .  
  
 В приведенной ниже таблице показан формат курсора, возвращенного процедурой sp_describe_cursor. Формат курсора такой же, что и формат, возвращаемый процедурой sp_cursor_list.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|reference_name|**имеет sysname**|Имя, используемое для ссылки на курсор. Если ссылка на курсор осуществлялась с помощью имени, указанного в инструкции DECLARE CURSOR, имя ссылки совпадает с именем курсора. Если ссылка на курсор осуществлялась через переменную, имя ссылки совпадает с именем переменной.|  
|cursor_name|**имеет sysname**|Имя курсора из инструкции DECLARE CURSOR. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если курсор создан с помощью присваивания переменной курсора, cursor_name возвращает имя переменной курсора. В более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот выходной столбец возвращает имя, формируемое системой.|  
|cursor_scope|**tinyint**|1 = LOCAL<br /><br /> 2 = GLOBAL|  
|status|**int**|Те же значения, которые получены с помощью системной функции CURSOR_STATUS.<br /><br /> 1 = курсор, указанный ссылкой в имени или переменной курсора, открыт. Если курсор нечувствительный, статичный или является набором ключей, он имеет, по крайней мере, одну строку. Если курсор динамический, результирующий набор имеет ноль или более строк.<br /><br /> 0 = курсор, указанный ссылкой в имени или переменной курсора, открыт, но не имеет строк. Динамические курсоры не возвращают это значение.<br /><br /> -1 = курсор, указанный ссылкой в имени или переменной курсора, закрывается.<br /><br /> -2 = применимо только к переменным курсора. Нет курсора, назначенного переменной. Возможно, параметр OUTPUT назначил курсор переменной, но хранимая процедура закрыла курсор перед возвратом.<br /><br /> -3 = курсор или переменная курсора с заданным именем не существует либо переменной не выделен курсор.|  
|model|**tinyint**|1 = нечувствительный (или статичный)<br /><br /> 2 = набор ключей<br /><br /> 3 = динамический<br /><br /> 4 = перемотка вперед|  
|concurrency|**tinyint**|1 = только для чтения<br /><br /> 2 = блокирование прокрутки<br /><br /> 3 = оптимистический|  
|scrollable|**tinyint**|0 = только вперед<br /><br /> 1 = возможна прокрутка|  
|open_status|**tinyint**|0 = закрыт<br /><br /> 1 = открыт|  
|cursor_rows|**десятичное число (10, 0)**|Количество выбранных строк в результирующем наборе. Дополнительные сведения см. в статье [@@CURSOR_ROWS (Transact-SQL)](../../t-sql/functions/cursor-rows-transact-sql.md).|  
|fetch_status|**smallint**|Состояние последней выборки данного курсора. Дополнительные сведения см. в статье [@@FETCH_STATUS (Transact-SQL)](../../t-sql/functions/fetch-status-transact-sql.md).<br /><br /> 0 = выборка завершена успешно.<br /><br /> -1 = выборка завершена с ошибкой или вышла за пределы курсора.<br /><br /> -2 = запрошенная строка отсутствует.<br /><br /> -9 = выборка по курсору не произведена.|  
|column_count|**smallint**|Количество столбцов в результирующем наборе курсора.|  
|row_count|**десятичное число (10, 0)**|Количество строк, затронутых последней операцией курсора. Дополнительные сведения см. в статье [@@ROWCOUNT (Transact-SQL)](../../t-sql/functions/rowcount-transact-sql.md).|  
|last_operation|**tinyint**|Последняя операция, выполненная над курсором.<br /><br /> 0 = операции c курсором не выполнялись.<br /><br /> 1 = OPEN;<br /><br /> 2 = FETCH;<br /><br /> 3 = ВСТАВИТЬ<br /><br /> 4 = UPDATE;<br /><br /> 5 = DELETE;<br /><br /> 6 = CLOSE<br /><br /> 7 = DEALLOCATE|  
|cursor_handle|**int**|Уникальное значение для курсора в пределах сервера.|  
  
## <a name="remarks"></a>Remarks  
 Процедура sp_describe_cursor описывает такие глобальные для серверного курсора атрибуты как возможность прокрутки и обновления. Используйте процедуру sp_describe_cursor_columns для описания атрибутов результирующего набора, возвращаемого курсором. Процедура sp_describe_cursor_tables используется для получения отчета по базовым таблицам, на которые ссылается курсор. Чтобы получить отчет по серверным курсорам [!INCLUDE[tsql](../../includes/tsql-md.md)], видимым в соединении, используется процедура sp_cursor_list.  
  
 Инструкция DECLARE CURSOR может затребовать тип курсора, который не поддерживается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции SELECT, содержащейся в DECLARE CURSOR. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] неявно преобразует курсор в тип, который может поддерживаться с использованием инструкции SELECT. Если в инструкции DECLARE CURSOR указано ключевое слово TYPE_WARNING, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отправляет в приложение информационное сообщение о завершении преобразования. Затем можно вызвать sp_describe_cursor, чтобы определить тип реализованного курсора.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
 В следующем примере открывается глобальный курсор и используется процедура `sp_describe_cursor` для получения отчета об атрибутах курсора.  
  
```  
USE AdventureWorks2012;  
GO  
-- Declare and open a global cursor.  
DECLARE abc CURSOR STATIC FOR  
SELECT LastName  
FROM Person.Person;  
  
OPEN abc;  
  
-- Declare a cursor variable to hold the cursor output variable  
-- from sp_describe_cursor.  
DECLARE @Report CURSOR;  
  
-- Execute sp_describe_cursor into the cursor variable.  
EXEC master.dbo.sp_describe_cursor @cursor_return = @Report OUTPUT,  
        @cursor_source = N'global', @cursor_identity = N'abc';  
  
-- Fetch all the rows from the sp_describe_cursor output cursor.  
FETCH NEXT from @Report;  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN  
    FETCH NEXT from @Report;  
END  
  
-- Close and deallocate the cursor from sp_describe_cursor.  
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
 [sp_describe_cursor_columns &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-columns-transact-sql.md)   
 [sp_describe_cursor_tables &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-tables-transact-sql.md)  
  
  
