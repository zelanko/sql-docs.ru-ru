---
title: Хранимая процедура sp_cursor_list (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cursor_list
- sp_cursor_list_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursor_list
ms.assetid: 7187cfbe-d4d9-4cfa-a3bb-96a544c7c883
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 368c1b64a7c6eea9d338a1698e5a20d90948b696
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33239594"
---
# <a name="spcursorlist-transact-sql"></a>sp_cursor_list (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Представляет атрибуты серверных курсоров, открытых на данный момент для соединения.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_cursor_list [ @cursor_return = ] cursor_variable_name OUTPUT   
     , [ @cursor_scope = ] cursor_scope  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @cursor_return=] *cursor_variable_name*выходных данных  
 Имя объявленной переменной курсора. *cursor_variable_name* — **курсор**, не имеет значения по умолчанию. Этот аргумент является динамическим, прокручиваемым и предназначенным только для чтения.  
  
 [ @cursor_scope=] *cursor_scope*  
 Определяет, какие уровни курсоров включаются в отчет. *cursor_scope* — **int**, без значения по умолчанию и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|1|Представить все локальные курсоры.|  
|2|Представить все глобальные курсоры.|  
|3|Представить как локальные, так и глобальные курсоры.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="cursors-returned"></a>Возвращенные курсоры  
 Хранимая процедура sp_cursor_list возвращает свой отчет в виде выходного параметра-курсора [!INCLUDE[tsql](../../includes/tsql-md.md)], не в виде результирующего набора. Позволяет пакетам, хранимым процедурам и триггерам [!INCLUDE[tsql](../../includes/tsql-md.md)] работать с выходными данными по одной строке за раз. Это также означает, что процедуру нельзя вызвать напрямую из API-функций базы данных. Выходной параметр-курсор должен быть привязан к программной переменной, но API-интерфейсы баз данных не поддерживают привязку параметров-курсоров или переменных.  
  
 Формат курсора, возвращаемого хранимой процедурой sp_cursor_list. Формат курсора такой же, как и формат, возвращаемый хранимой процедурой sp_describe_cursor.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|reference_name|**sysname**|Имя, используемое для ссылки на курсор. Если ссылка на курсор осуществлялась по имени, приведенном в инструкции DECLARE CURSOR, то имя ссылки и имя курсора одинаковы. Если ссылка на курсор осуществлялась при помощи переменной, именем ссылки является имя переменной курсора.|  
|cursor_name|**sysname**|Имя курсора из инструкции DECLARE CURSOR. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], если курсор создан с помощью присваивания переменной курсора, **cursor_name** возвращает имя переменной курсора.  В предыдущих версиях этот выходной столбец возвращает имя, сформированное системой.|  
|cursor_scope|**smallint**|1 = LOCAL<br /><br /> 2 = GLOBAL|  
|status|**smallint**|Те же значения, какие представлены системной функцией CURSOR_STATUS.<br /><br /> 1 = курсор, указанный ссылкой в имени или переменной курсора, открыт. Если курсор нечувствительный, статичный или является набором ключей, он имеет, по крайней мере, одну строку. Если курсор динамический, результирующий набор имеет ноль или более строк.<br /><br /> 0 = курсор, указанный ссылкой в имени или переменной курсора, открыт, но не имеет строк. Динамические курсоры не возвращают это значение.<br /><br /> -1 = курсор, указанный ссылкой в имени или переменной курсора, закрывается.<br /><br /> -2 = применимо только к переменным курсора. Нет курсора, назначенного переменной. Возможно, параметр OUTPUT назначил курсор переменной, но хранимая процедура закрыла курсор перед возвратом.<br /><br /> -3 = курсор или переменная курсора с заданным именем не существует либо переменной не выделен курсор.|  
|model|**smallint**|1 = нечувствительный (или статичный)<br /><br /> 2 = набор ключей<br /><br /> 3 = динамический<br /><br /> 4 = перемотка вперед|  
|параллелизм|**smallint**|1 = только для чтения<br /><br /> 2 = блокирование прокрутки<br /><br /> 3 = оптимистический|  
|scrollable|**smallint**|0 = только вперед<br /><br /> 1 = возможна прокрутка|  
|open_status|**smallint**|0 = закрыт<br /><br /> 1 = открыт|  
|cursor_rows|**int**|Количество уточняющих строк в результирующем наборе. Дополнительные сведения см. в разделе [@@CURSOR_ROWS](../../t-sql/functions/cursor-rows-transact-sql.md).|  
|fetch_status|**smallint**|Состояние последней выборки по данному курсору. Дополнительные сведения см. в разделе [@@FETCH_STATUS](../../t-sql/functions/fetch-status-transact-sql.md):<br /><br /> 0 = выборка завершена успешно.<br /><br /> -1 = выборка завершена с ошибкой или вышла за пределы курсора.<br /><br /> -2 = запрошенная строка отсутствует.<br /><br /> -9 = выборка по курсору не произведена.|  
|column_count|**smallint**|Количество столбцов в результирующем наборе курсора.|  
|row_count|**smallint**|Количество строк, затронутых последней операцией с курсором. Дополнительные сведения см. в разделе [@@ROWCOUNT](../../t-sql/functions/rowcount-transact-sql.md).|  
|last_operation|**smallint**|Последняя операция, выполненная с данным курсором.<br /><br /> 0 = операции c курсором не выполнялись.<br /><br /> 1 = OPEN;<br /><br /> 2 = FETCH;<br /><br /> 3 = ВСТАВКА<br /><br /> 4 = UPDATE;<br /><br /> 5 = DELETE;<br /><br /> 6 = CLOSE<br /><br /> 7 = DEALLOCATE|  
|cursor_handle|**int**|Уникальное значение, определяющее курсор в пределах области сервера.|  
  
## <a name="remarks"></a>Замечания  
 Хранимая процедура sp_cursor_list представляет список текущих серверных курсоров, открытых соединением, и описывает атрибуты, являющиеся глобальными по отношению к каждому курсору, такие как возможность прокрутки и обновления курсора. Курсоры, представленные в хранимой процедуре sp_cursor_list, включают:  
  
-   серверные курсоры [!INCLUDE[tsql](../../includes/tsql-md.md)];  
  
-   Серверные курсоры API, открывающиеся приложением ODBC, которое затем называется SQLSetCursorName для именования курсора.  
  
 Используйте процедуру sp_describe_cursor_columns для описания атрибутов результирующего набора, возвращаемого курсором. Процедура sp_describe_cursor_tables используется для получения отчета по базовым таблицам, на которые ссылается курсор. процедура sp_describe_cursor сообщает те же сведения, как и процедура sp_cursor_list, но только для определенного курсора.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на выполнение по умолчанию принадлежит роли public.  
  
## <a name="examples"></a>Примеры  
 В следующем примере открывается глобальный курсор и используется процедура `sp_cursor_list` для получения отчета об атрибутах курсора.  
  
```  
USE AdventureWorks2012;  
GO  
-- Declare and open a keyset-driven cursor.  
DECLARE abc CURSOR KEYSET FOR  
SELECT LastName  
FROM Person.Person  
WHERE LastName LIKE 'S%';  
OPEN abc;  
  
-- Declare a cursor variable to hold the cursor output variable  
-- from sp_cursor_list.  
DECLARE @Report CURSOR;  
  
-- Execute sp_cursor_list into the cursor variable.  
EXEC master.dbo.sp_cursor_list @cursor_return = @Report OUTPUT,  
      @cursor_scope = 2;  
  
-- Fetch all the rows from the sp_cursor_list output cursor.  
FETCH NEXT from @Report;  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN  
   FETCH NEXT from @Report;  
END  
  
-- Close and deallocate the cursor from sp_cursor_list.  
CLOSE @Report;  
DEALLOCATE @Report;  
GO  
  
-- Close and deallocate the original cursor.  
CLOSE abc;  
DEALLOCATE abc;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
