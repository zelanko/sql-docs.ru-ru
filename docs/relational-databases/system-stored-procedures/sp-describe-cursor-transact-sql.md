---
title: "процедура sp_describe_cursor (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_describe_cursor
- sp_describe_cursor_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_describe_cursor
ms.assetid: 0c836c99-1147-441e-998c-f0a30cd05275
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c3bfff92cd52459c72961439bc1e7280e2f0e5b9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spdescribecursor-transact-sql"></a>sp_describe_cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выводит атрибуты серверного курсора.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
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
 [ @cursor_return=] *output_cursor_variable* выходных данных  
 Имя объявленной переменной для получения выходных данных курсора. *output_cursor_variable* — **курсор**, не по умолчанию, и не быть связан с одним курсором при вызове процедуры sp_describe_cursor. Возвращаемый курсор является прокручиваемым, динамическим и доступным только для чтения.  
  
 [ @cursor_source=] {N'local' | N'global' | N'variable'}  
 Указывает, задан ли возвращаемый курсор с помощью имени локального курсора, глобального курсора или курсорной переменной. Параметр — **nvarchar(30)**.  
  
 [ @cursor_identity=] N'*local_cursor_name*"]  
 Имя курсора, созданного инструкцией DECLARE CURSOR с ключевым словом LOCAL или параметром LOCAL по умолчанию. *local_cursor_name* — **nvarchar(128)**.  
  
 [ @cursor_identity=] N'*global_cursor_name*"]  
 Имя курсора, созданного инструкцией DECLARE CURSOR с ключевым словом GLOBAL или параметром GLOBAL по умолчанию. *global_cursor_name* — **nvarchar(128)**.  
  
 *global_cursor_name* также может быть именем серверного курсора API, открытого приложением ODBC, которое затем именованного вызовом SQLSetCursorName.  
  
 [ @cursor_identity=] N'*input_cursor_variable*"]  
 Имя переменной курсора, связанной с открытым курсором. *input_cursor_variable* — **nvarchar(128)**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="cursors-returned"></a>Возвращенные курсоры  
 процедура sp_describe_cursor помещает результирующий набор [!INCLUDE[tsql](../../includes/tsql-md.md)] **курсор** выходной параметр. Это позволяет пакетам [!INCLUDE[tsql](../../includes/tsql-md.md)], хранимым процедурам и триггерам построчно обрабатывать выходные данные. Это также означает, что процедуру нельзя вызывать непосредственно из функций API баз данных. **Курсор** выходной параметр должен быть привязан к программной переменной, но API базы данных не поддерживают привязку **курсор** параметры или переменные.  
  
 В приведенной ниже таблице показан формат курсора, возвращенного процедурой sp_describe_cursor. Формат курсора такой же, что и формат, возвращаемый процедурой sp_cursor_list.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|reference_name|**sysname**|Имя, используемое для ссылки на курсор. Если ссылка на курсор осуществлялась с помощью имени, указанного в инструкции DECLARE CURSOR, имя ссылки совпадает с именем курсора. Если ссылка на курсор осуществлялась через переменную, имя ссылки совпадает с именем переменной.|  
|cursor_name|**sysname**|Имя курсора из инструкции DECLARE CURSOR. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если курсор создан с помощью присваивания переменной курсора, cursor_name возвращает имя переменной курсора. В более ранних версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот выходной столбец возвращает имя, формируемое системой.|  
|cursor_scope|**tinyint**|1 = LOCAL<br /><br /> 2 = GLOBAL|  
|status|**int**|Те же значения, которые получены с помощью системной функции CURSOR_STATUS.<br /><br /> 1 = курсор, указанный ссылкой в имени или переменной курсора, открыт. Если курсор нечувствительный, статичный или является набором ключей, он имеет, по крайней мере, одну строку. Если курсор динамический, результирующий набор имеет ноль или более строк.<br /><br /> 0 = курсор, указанный ссылкой в имени или переменной курсора, открыт, но не имеет строк. Динамические курсоры не возвращают это значение.<br /><br /> -1 = курсор, указанный ссылкой в имени или переменной курсора, закрывается.<br /><br /> -2 = применимо только к переменным курсора. Нет курсора, назначенного переменной. Возможно, параметр OUTPUT назначил курсор переменной, но хранимая процедура закрыла курсор перед возвратом.<br /><br /> -3 = курсор или переменная курсора с заданным именем не существует либо переменной не выделен курсор.|  
|model|**tinyint**|1 = нечувствительный (или статичный)<br /><br /> 2 = набор ключей<br /><br /> 3 = динамический<br /><br /> 4 = перемотка вперед|  
|параллелизм|**tinyint**|1 = только для чтения<br /><br /> 2 = блокирование прокрутки<br /><br /> 3 = оптимистический|  
|scrollable|**tinyint**|0 = только вперед<br /><br /> 1 = возможна прокрутка|  
|open_status|**tinyint**|0 = закрыт<br /><br /> 1 = открыт|  
|cursor_rows|**Decimal(10,0)**|Количество выбранных строк в результирующем наборе. Дополнительные сведения см. в разделе [@@CURSOR_ROWS &#40; Transact-SQL &#41; ](../../t-sql/functions/cursor-rows-transact-sql.md).|  
|fetch_status|**smallint**|Состояние последней выборки данного курсора. Дополнительные сведения см. в разделе [@@FETCH_STATUS &#40; Transact-SQL &#41; ](../../t-sql/functions/fetch-status-transact-sql.md).<br /><br /> 0 = выборка завершена успешно.<br /><br /> -1 = выборка завершена с ошибкой или вышла за пределы курсора.<br /><br /> -2 = запрошенная строка отсутствует.<br /><br /> -9 = выборка по курсору не произведена.|  
|column_count|**smallint**|Количество столбцов в результирующем наборе курсора.|  
|row_count|**Decimal(10,0)**|Количество строк, затронутых последней операцией курсора. Дополнительные сведения см. в разделе [@@ROWCOUNT &#40; Transact-SQL &#41; ](../../t-sql/functions/rowcount-transact-sql.md).|  
|last_operation|**tinyint**|Последняя операция, выполненная над курсором.<br /><br /> 0 = операции c курсором не выполнялись.<br /><br /> 1 = OPEN;<br /><br /> 2 = FETCH;<br /><br /> 3 = ВСТАВКА<br /><br /> 4 = UPDATE;<br /><br /> 5 = DELETE;<br /><br /> 6 = CLOSE<br /><br /> 7 = DEALLOCATE|  
|cursor_handle|**int**|Уникальное значение для курсора в пределах сервера.|  
  
## <a name="remarks"></a>Замечания  
 Процедура sp_describe_cursor описывает такие глобальные для серверного курсора атрибуты как возможность прокрутки и обновления. Используйте процедуру sp_describe_cursor_columns для описания атрибутов результирующего набора, возвращаемого курсором. Процедура sp_describe_cursor_tables используется для получения отчета по базовым таблицам, на которые ссылается курсор. Чтобы получить отчет по серверным курсорам [!INCLUDE[tsql](../../includes/tsql-md.md)], видимым в соединении, используется процедура sp_cursor_list.  
  
 Инструкция DECLARE CURSOR может затребовать тип курсора, который не поддерживается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструкции SELECT, содержащейся в DECLARE CURSOR. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] неявно преобразует курсор в тип, который может поддерживаться с использованием инструкции SELECT. Если в инструкции DECLARE CURSOR указано ключевое слово TYPE_WARNING, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отправляет в приложение информационное сообщение о завершении преобразования. процедура sp_describe_cursor затем может вызываться для определения типа полученного курсора был реализован.  
  
## <a name="permissions"></a>Permissions  
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
 [CURSOR_STATUS &#40; Transact-SQL &#41;](../../t-sql/functions/cursor-status-transact-sql.md)   
 [DECLARE CURSOR (Transact-SQL)](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [Хранимая процедура sp_cursor_list &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-cursor-list-transact-sql.md)   
 [sp_describe_cursor_columns &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-columns-transact-sql.md)   
 [процедура sp_describe_cursor_tables &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-tables-transact-sql.md)  
  
  
