---
title: sp_tableoption (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_tableoption_TSQL
- sp_tableoption
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tableoption
ms.assetid: 0a57462c-1057-4c7d-bce3-852cc898341d
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 84e6c530b4887502346b69adcf2590bce9d0e8fc
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85718690"
---
# <a name="sp_tableoption-transact-sql"></a>sp_tableoption (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Устанавливает значения параметров для определяемых пользователем таблиц. sp_tableoption можно использовать для управления поведением строк таблиц с типами **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **XML**, **Text**, **ntext**, **Image**или Large определяемого пользователем типа данных.  
  
> [!IMPORTANT]  
>  Параметр text in row будет исключен в следующей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для хранения больших значений рекомендуется использовать типы данных **varchar (max)**, **nvarchar (max)** и **varbinary (max)** .  
  

 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_tableoption [ @TableNamePattern = ] 'table'   
     , [ @OptionName = ] 'option_name'   
     ,[ @OptionValue =] 'value'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @TableNamePattern =] '*Таблица*'  
 Уточненное или неуточненное имя пользовательской таблицы базы данных. Если указано полное имя таблицы, включая имя базы данных, в качестве последнего должно использоваться имя текущей базы данных. Параметры таблицы нельзя установить одновременно для нескольких таблиц. *Table* имеет тип **nvarchar (776)** и не имеет значения по умолчанию.  
  
 [ @OptionName =] "*option_name*"  
 Название параметра таблицы. *option_name* имеет тип **varchar (35)** и не имеет значения по умолчанию NULL. *option_name* может иметь одно из следующих значений.  
  
|Применение|Описание|  
|-----------|-----------------|  
|table lock on bulk load|Если отключено (по умолчанию), то процесс массовой загрузки в пользовательских таблицах получает блокировку строк. Если включено, то процесс массовой загрузки в пользовательских таблицах получает блокировку массовых обновлений.|  
|блокировка вставки строк|Больше не поддерживается.<br /><br /> Этот параметр не влияет на свойства блокировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и включается только для совместимости существующих скриптов и процедур.|  
|text in row|При значении OFF или 0 (отключено по умолчанию) текущее поведение не меняется и в строке отсутствует блок больших двоичных объектов (BLOB).<br /><br /> Если указан параметр и @OptionValue имеет значение On (включено) или целое число от 24 до 7000, новые строки типа **Text**, **ntext**и **Image** хранятся непосредственно в строке данных. Все существующие большие двоичные объекты (большой двоичный объект: данные типа **Text**, **ntext**или **Image** ) будут преобразованы в текст в формате строки при обновлении значения большого двоичного объекта. Дополнительные сведения см. в подразделе "Примечания".|  
|large value types out of row|1 = столбцы **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **XML** и больших определяемых пользователем типов (UDT) в таблице хранятся вне строки с 16-байтовым указателем на корень.<br /><br /> 0 = **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **XML** и крупные значения UDT хранятся непосредственно в строке данных, до ограничения в 8000 байт и до тех пор, пока значение может уместиться в записи. Если значение не умещается в записи, то указатель хранится в строке, а все остальное хранится вне строки в области хранения объектов LOB. Значение по умолчанию — 0.<br /><br /> Большой определяемый пользователем тип (UDT) применяется к: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздним версиям. <br /><br /> Используйте параметр TEXTIMAGE_ON [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) , чтобы указать расположение для хранения больших типов данных. |  
|формат хранения vardecimal|**Область применения**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версий.<br /><br /> Значения TRUE, ON или 1 означают, что для указанной таблицы включен формат хранения vardecimal. Значения FALSE, OFF или 0 означают, что для таблицы не включен формат хранения vardecimal. Формат хранения vardecimal можно включить, только если для базы данных включен формат хранения vardecimal с помощью [sp_db_vardecimal_storage_format](../../relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql.md). В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях формат хранения **vardecimal** устарел. Вместо этого используйте сжатие ROW. Дополнительные сведения см. в разделе [Data Compression](../../relational-databases/data-compression/data-compression.md). Значение по умолчанию — 0.|  
  
 [ @OptionValue =] "*значение*"  
 Указывает, включено ли *option_name* (true, on или 1) или отключено (false, OFF или 0). *значение* имеет тип **varchar (12)** и не имеет значения по умолчанию. *значение* не учитывает регистр.  
  
 Для параметра text in row допустимыми значениями являются 0, ON, OFF или целое число в диапазоне от 24 до 7 000. Если *значение* равно ON, по умолчанию используется ограничение 256 байт.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или номер ошибки (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Процедура sp_tableoption может использоваться только для установки значений параметра для пользовательских таблиц. Чтобы отобразить свойства таблицы, используйте OBJECTPROPERTY или запрос sys. Tables.  
  
 Параметр text in row процедуры sp_tableoption может быть включен или выключен только на таблицах, содержащих текстовые столбцы. Если таблица не содержит текстового столбца, в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] происходит ошибка.  
  
 Если параметр текст в строке включен, @OptionValue параметр позволяет пользователям указать максимальный размер, который будет храниться в строке для большого двоичного объекта. Значение по умолчанию равно 256 байт, но значения могут располагаться в диапазоне с 24 по 7 000 байт.  
  
 строки типа **Text**, **ntext**и **Image** хранятся в строке данных, если выполняются следующие условия.  
  
-   text in row доступен;  
  
-   Длина строки короче предела, указанного в@OptionValue  
  
-   в строке данных достаточно места.  
  
 Если строки большого двоичного объекта хранятся в строке данных, чтение и запись строк **Text**, **ntext**или **Image** может выполняться так же быстро, как чтение или запись символьных и двоичных строк. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не требуется получать доступ к отдельным страницам для считывания или записи строки BLOB.  
  
 Если строка типа **Text**, **ntext**или **Image** больше указанного предела или доступного пространства в строке, то указатели хранятся в строке. Условия хранения строк большого двоичного объекта в строке, тем не менее, применяются: в строке данных должно быть достаточно места для хранения указателей.  
  
 Строки и указатели BLOB, хранящиеся в строке таблицы, рассматриваются так же, как строки переменной длины. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует только число байтов, необходимое для хранения строки или указателя.  
  
 Существующие строки BLOB преобразуются через некоторое время после первого включения text in row. Строки преобразуются только при обновлении. Аналогично, при увеличении ограничения для текста в параметре строки **текст**, **ntext**или строки **изображений** , уже наданные в строке данных, не будут преобразованы в соответствие с новым ограничением до тех пор, пока они не будут обновлены.  
  
> [!NOTE]  
>  Отключение параметра text in row или уменьшение предела параметра потребует преобразования всех BLOB; поэтому процесс может занять много времени, в зависимости от того, какое число строк BLOB необходимо преобразовать. Во время процесса преобразования таблица блокируется.  
  
 Для табличной переменной, включая функцию, которая возвращает табличную переменную, параметр text in row включен автоматически и имеет значение параметра inline limit, по умолчанию равное 256. Этот параметр нельзя изменить.  
  
 Параметр text in row поддерживает функции TEXTPTR, WRITETEXT, UPDATETEXT и READTEXT. Пользователи могут считывать части BLOB с помощью функции SUBSTRING(), но при этом следует помнить, что внутристрочные текстовые указатели по длине и пределам чисел отличаются от других текстовых указателей.  
  
 Чтобы можно было перевести таблицу из формата хранения vardecimal обратно в формат хранения decimal, база данных должна находиться в режиме восстановления SIMPLE. Изменение режима восстановления разорвет цепочку журналов, используемую для целей резервного копирования, поэтому следует создать полную резервную копию базы данных сразу после отключения формата хранения vardecimal в таблице.  
  
 При преобразовании существующего столбца с типом данных LOB (Text, ntext или image) в типы больших значений типа "Малый/средний" (varchar (max), nvarchar (max) или varbinary (max)) и большинство инструкций не ссылаются на столбцы типа больших значений в вашей среде, попробуйте изменить **large_value_types_out_of_row** на **1** , чтобы получить оптимальную производительность. При изменении значения параметра **large_value_types_out_of_row** существующие значения типа varchar (max), nvarchar (max), varbinary (max) и XML не преобразуются сразу. Хранилище строк изменяется, так как они в последующем обновляются. Любые новые значения, которые добавляются в таблицу, хранятся согласно действующему параметру таблицы. Для немедленного выполнения создайте копию данных, а затем повторно заполните таблицу после изменения параметра **large_value_types_out_of_row** или обновите каждый столбец небольшого числа до среднего размера до самого себя, чтобы хранилище строк было изменено с учетом параметра таблицы. Рассмотрим перестройку индексов в таблице после обновления или повторного заполнения для сжатия таблицы. 
    
  
## <a name="permissions"></a>Разрешения  
 Чтобы выполнить процедуру sp_tableoption, требуется разрешение ALTER на таблицу.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-storing-xml-data-out-of-the-row"></a>A. Хранение XML-данных вне строки  
 В следующем примере указывается, что **XML-** данные в `HumanResources.JobCandidate` таблице должны храниться вне строки.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_tableoption 'HumanResources.JobCandidate', 'large value types out of row', 1;  
```  
  
### <a name="b-enabling-vardecimal-storage-format-on-a-table"></a>Б. Включение формата хранения vardecimal для таблицы  
 В следующем примере изменяется `Production.WorkOrderRouting` Таблица для хранения `decimal` типа данных в `vardecimal` формате хранения.  

```sql  
USE master;  
GO  
-- The database must be enabled for vardecimal storage format  
-- before a table can be enabled for vardecimal storage format  
EXEC sp_db_vardecimal_storage_format 'AdventureWorks2012', 'ON';  
GO  
USE AdventureWorks2012;  
GO  
EXEC sp_tableoption 'Production.WorkOrderRouting',   
   'vardecimal storage format', 'ON';  
```  
  
## <a name="see-also"></a>См. также  
 [sys. Tables &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
