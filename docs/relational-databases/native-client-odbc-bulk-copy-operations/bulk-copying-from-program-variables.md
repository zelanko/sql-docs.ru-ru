---
title: Массовое копирование из переменных программы | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-bulk-copy-operations
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], program variables
- bcp_bind function
- mapping data types [ODBC]
- SQL Server Native Client ODBC driver, bulk copy
- data types [ODBC], bulk copying
- ODBC, bulk copy operations
- program variables [ODBC]
ms.assetid: e4284a1b-7534-4b34-8488-b8d05ed67b8c
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5e0bcb033e4e99bdba8dc7167d3823e103c9cfd9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="bulk-copying-from-program-variables"></a>Массовое копирование из переменных приложения
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Массовое копирование можно производить напрямую из переменных программы. После распределения переменных для хранения данных для строки и вызова функции [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) для запуска массового копирования, вызовите [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) для каждого столбца указать расположение и формат переменной программы, необходимо сопоставить со столбцом. Заполните каждую переменную с данными, затем вызовите [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) для отправки одну строку данных на сервер. Повторяйте процесс заполнения переменных и вызова **bcp_sendrow** до всех строк, отправленных на сервер, затем вызовите [bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md) для указания, что операция завершена.  
  
 **Bcp_bind *** pData* содержит адрес переменной, привязанной к столбцу. Данные каждого столбца можно сохранить двумя способами:  
  
-   выделить одну переменную для хранения данных;  
  
-   выделить переменную признака, сопровождаемую переменной данных.  
  
 Переменная признака определяет длину данных столбцов переменной длины, а также значения типа NULL, если они разрешены столбцом. При использовании переменной данных только затем адрес этой переменной хранится в **bcp_bind *** pData* параметра. При использовании переменной признака адрес этой переменной хранится в **bcp_bind *** pData* параметра. Функции массового копирования вычисляют расположение переменной данных путем добавления **bcp_bind *** cbIndicator* и *pData* параметров.  
  
 **bcp_bind** поддерживает три метода для обработки данных с переменной длиной:  
  
-   Используйте *cbData* с переменной данных. Поместите длину данных в *cbData*. Каждый раз, длина данных для массового копирования, вызовите [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)Сброс *cbData*. Если один из двух других методов используется, укажите значение SQL_VARLEN_DATA для *cbData*. Если все значения, указанное для столбца значение NULL, укажите SQL_NULL_DATA для *cbData*.  
  
-   Используйте переменные признака. При каждом перемещении нового значения в переменную данных следует сохранять длину значения в переменной признака. Если один из двух других методов используется, укажите значение 0 для *cbIndicator*.  
  
-   Используйте указатели признака конца. Загрузка **bcp_bind *** pTerm* с адресом битового шаблона, который прерывает данные. Если один из двух других методов используется, укажите значение NULL для *pTerm*.  
  
 Все три из этих методов можно использовать на том же **bcp_bind** вызова, в этом случае используется спецификация, приводит к минимальный объем копируемых данных.  
  
 **Bcp_bind *** тип* DB-Library использует идентификаторы типа данных, не идентификаторы типа данных ODBC. Идентификаторы типа данных DB-Library определяются в файле sqlncli.h для использования с функцией ODBC **bcp_bind** функции.  
  
 Функции массового копирования данных поддерживают не все типы данных ODBC C. Например, функции массового копирования не поддерживают структуру ODBC SQL_C_TYPE_TIMESTAMP, поэтому следует использовать [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) или [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) для преобразования данных ODBC SQL_TYPE_TIMESTAMP в переменную SQL_C_CHAR. При использовании **bcp_bind** с *тип* параметра равным SQLCHARACTER, для привязки переменной к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime** преобразование столбца, функции массового копирования предложение escape отметки времени внутри символьной переменной в правильный формат datetime.  
  
 В следующей таблице перечислены типы данных, рекомендуемые для использования в сопоставлении с типом данных ODBC SQL для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.  
  
|Тип данных ODBC SQL|Тип данных ODBC C|bcp_bind *тип* параметр|Тип данных SQL Server|  
|-----------------------|----------------------|--------------------------------|--------------------------|  
|SQL_CHAR|SQL_C_CHAR|SQLCHARACTER|**character**<br /><br /> **char**|  
|SQL_VARCHAR|SQL_C_CHAR|SQLCHARACTER|**varchar**<br /><br /> **Изменение символа**<br /><br /> **char varying**<br /><br /> **sysname**|  
|SQL_LONGVARCHAR|SQL_C_CHAR|SQLCHARACTER|**text**|  
|SQL_WCHAR|SQL_C_WCHAR|SQLNCHAR|**nchar**|  
|SQL_WVARCHAR|SQL_C_WCHAR|SQLNVARCHAR|**nvarchar**|  
|SQL_WLONGVARCHAR|SQL_C_WCHAR|SQLNTEXT|**ntext**|  
|SQL_DECIMAL|SQL_C_CHAR|SQLCHARACTER|**decimal**<br /><br /> **dec**<br /><br /> **money**<br /><br /> **smallmoney**|  
|SQL_NUMERIC|SQL_C_NUMERIC|SQLNUMERICN|**numeric**|  
|SQL_BIT|SQL_C_BIT|SQLBIT|**бит**|  
|SQL_TINYINT (подписанный)|SQL_C_SSHORT|SQLINT2|**smallint**|  
|SQL_TINYINT (неподписанный)|SQL_C_UTINYINT|SQLINT1|**tinyint**|  
|SQL_SMALL_INT (подписанный)|SQL_C_SSHORT|SQLINT2|**smallint**|  
|SQL_SMALL_INT (неподписанный)|SQL_C_SLONG|SQLINT4|**int**<br /><br /> **integer**|  
|SQL_INTEGER (подписанный)|SQL_C_SLONG|SQLINT4|**int**<br /><br /> **integer**|  
|SQL_INTEGER (неподписанный)|SQL_C_CHAR|SQLCHARACTER|**decimal**<br /><br /> **dec**|  
|SQL_BIGINT (подписанный и неподписанный)|SQL_C_CHAR|SQLCHARACTER|**bigint**|  
|SQL_REAL|SQL_C_FLOAT|SQLFLT4|**real**|  
|SQL_FLOAT|SQL_C_DOUBLE|SQLFLT8|**float**|  
|SQL_DOUBLE|SQL_C_DOUBLE|SQLFLT8|**float**|  
|SQL_BINARY|SQL_C_BINARY|SQLBINARY|**binary**<br /><br /> **timestamp**|  
|SQL_VARBINARY|SQL_C_BINARY|SQLBINARY|**varbinary**<br /><br /> **Двоичный переменной**|  
|SQL_LONGVARBINARY|SQL_C_BINARY|SQLBINARY|**image**|  
|SQL_TYPE_DATE|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_TYPE_TIME|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_TYPE_TIMESTAMP|SQL_C_CHAR|SQLCHARACTER|**datetime**<br /><br /> **smalldatetime**|  
|SQL_GUID|SQL_C_GUID|SQLUNIQUEID|**uniqueidentifier**|  
|SQL_INTERVAL_|SQL_C_CHAR|SQLCHARACTER|**char**|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Нет знакового **tinyint**без знака, **smallint**, или без знака **int** типов данных. Для предотвращения потери значений данных при миграции этих типов данных, создайте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицу со следующим наибольшим типом данных integer. Для предотвращения последующего добавления пользователями значений, находящихся за пределами диапазона, разрешенного исходными типом данных, примените к столбцу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] правило ограничения разрешенных значений до диапазона, поддерживаемого типом данных в исходном источнике:  
  
```  
CREATE TABLE Sample_Ints(STinyIntCol   SMALLINT,  
USmallIntCol INT)  
GO  
CREATE RULE STinyInt_Rule  
AS   
@range >= -128 AND @range <= 127  
GO  
CREATE RULE USmallInt_Rule  
AS   
@range >= 0 AND @range <= 65535  
GO  
sp_bindrule STinyInt_Rule, 'Sample_Ints.STinyIntCol'  
GO  
sp_bindrule USmallInt_Rule, 'Sample_Ints.USmallIntCol'  
GO  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] непосредственно не поддерживает типы данных интервала. Приложение тем не менее, может сохранять управляющие последовательности интервала в виде символьных строк в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] символьный столбец. Приложение может считывать их для дальнейшего использования, но они не могут использоваться в инструкциях [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Функции массового копирования могут использоваться для быстрой загрузки данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , был считан из источника данных ODBC. Используйте [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) для привязки столбцов результирующего набора с переменными программы, затем с помощью **bcp_bind** для привязки тех же переменных программы к операции массового копирования. Вызов [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) или **SQLFetch** производит выборку строк данных из источника данных ODBC в переменные программы, а вызов метода [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) выполняет массовое копирование данных из переменных программы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Приложение может использовать [bcp_colptr](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md) функцию для изменения адреса переменной данных, первоначально указанной в **bcp_bind** *pData* параметра. Приложение может использовать [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) функцию для изменения длины данных, первоначально указанной в **bcp_bind *** cbData* параметра.  
  
 Не удается прочитать данные из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в переменные программы с помощью операции массового копирования нет ничего функцию «bcp_readrow». Отправлять данные можно только от приложения на сервер.  
  
## <a name="see-also"></a>См. также  
 [Выполнение операций массового копирования &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
