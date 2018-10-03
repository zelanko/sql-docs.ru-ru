---
title: SQLColAttribute | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLColAttribute function
ms.assetid: a5387d9e-a243-4cfe-b786-7fad5842b1d6
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 80e78d486ff0b87a2cf187a134beb029774f9171
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773152"
---
# <a name="sqlcolattribute"></a>SQLColAttribute
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Можно использовать **SQLColAttribute** для получения атрибута столбца результирующего набора для подготовленных или выполненных инструкций ODBC. Вызов **SQLColAttribute** в подготовленной инструкции приводит к обращению к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента получает данные столбца результирующего набора в процессе выполнения инструкции, поэтому вызов **SQLColAttribute** после завершения **SQLExecute** или  **SQLExecDirect** происходит без обращения к серверу.  
  
> [!NOTE]  
>  Атрибуты ODBC идентификаторов столбца доступны не во всех результирующих наборах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Идентификатор поля|Описание|  
|----------------------|-----------------|  
|SQL_COLUMN_TABLE_NAME|Можно использовать для результирующих наборов, полученных от инструкций, которые формируют серверные курсоры, или для выполненных инструкций SELECT, содержащих предложение FOR BROWSE.|  
|SQL_DESC_BASE_COLUMN_NAME|Можно использовать для результирующих наборов, полученных от инструкций, которые формируют серверные курсоры, или для выполненных инструкций SELECT, содержащих предложение FOR BROWSE.|  
|SQL_DESC_BASE_TABLE_NAME|Можно использовать для результирующих наборов, полученных от инструкций, которые формируют серверные курсоры, или для выполненных инструкций SELECT, содержащих предложение FOR BROWSE.|  
|SQL_DESC_CATALOG_NAME|Имя базы данных. Можно использовать для результирующих наборов, полученных от инструкций, которые формируют серверные курсоры, или для выполненных инструкций SELECT, содержащих предложение FOR BROWSE.|  
|SQL_DESC_LABEL|Можно использовать для всех результирующих наборов. Значение идентично значению поля SQL_DESC_NAME.<br /><br /> Длина поля равна нулю только в том случае, если столбец является результатом выражения, не содержащего назначения метки.|  
|SQL_DESC_NAME|Можно использовать для всех результирующих наборов. Значение идентично значению поля SQL_DESC_LABEL.<br /><br /> Длина поля равна нулю только в том случае, если столбец является результатом выражения, не содержащего назначения метки.|  
|SQL_DESC_SCHEMA_NAME|Имя владельца. Можно использовать для результирующих наборов, полученных от инструкций, которые формируют серверные курсоры, или для выполненных инструкций SELECT, содержащих предложение FOR BROWSE.<br /><br /> Доступно, только если имя владельца задано для столбца в инструкции SELECT.|  
|SQL_DESC_TABLE_NAME|Можно использовать для результирующих наборов, полученных от инструкций, которые формируют серверные курсоры, или для выполненных инструкций SELECT, содержащих предложение FOR BROWSE.|  
|SQL_DESC_UNNAMED|SQL_NAMED для всех столбцов в результирующем наборе, за исключением случаев, когда столбец является результатом выражения, не содержащего назначения метки в составе выражения. Если SQL_DESC_UNNAMED возвращает SQL_UNNAMED, все атрибуты ODBC идентификаторов столбцов содержат строки нулевой длины для этого столбца.|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер собственного клиента ODBC использует инструкцию SET FMTONLY для снижения нагрузки на сервер при **SQLColAttribute** вызывается для подготовленных но невыполненных инструкций.  
  
 Для типов больших значений **SQLColAttribute** возвратит следующие значения:  
  
|Идентификатор поля|Описание изменения|  
|----------------------|---------------------------|  
|SQL_DESC_DISPLAY_SIZE|Максимальное число символов, необходимых для отображения данных столбца. Для столбцов типов больших значений возвращается значение SQL_SS_LENGTH_UNLIMITED.|  
|SQL_DESC_LENGTH|Возвращает в результирующем наборе фактическую длину столбца. Для столбцов типов больших значений возвращается значение SQL_SS_LENGTH_UNLIMITED.|  
|SQL_DESC_OCTET_LENGTH|Возвращает максимальную длину столбца с типом больших значений. SQL_SS_LENGTH_UNLIMITED используется для указания неограниченного размера.|  
|SQL_DESC_PRECISION|Возвращает значение SQL_SS_LENGTH_UNLIMITED для столбцов с типом больших значений.|  
|SQL_DESC_TYPE|Возвращает SQL_VARCHAR, SQL_WVARCHAR и SQL_VARBINARY для типов больших значений.|  
|SQL_DESC_TYPE_NAME|Возвращает типы данных varchar, varbinary и nvarchar для типов больших значений.|  
  
 Для всех версий атрибуты столбцов возвращаются только для первого результирующего набора, если несколько результирующих наборов формируются готовым пакетом инструкций SQL.  
  
 Следующие атрибуты столбцов являются расширениями, полученными с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC для собственного клиента возвращает все значения в *NumericAttrPtr* параметра. Возвращаются значения с типом SDWORD (signed long) за исключением SQL_CA_SS_COMPUTE_BYLIST, которое представляет собой указатель на массив WORD.  
  
|Идентификатор поля|Возвращенное значение|  
|----------------------|--------------------|  
|SQL_CA_SS_COLUMN_HIDDEN*|Значение TRUE, если столбец является частью скрытого первичного ключа, созданного для поддержки инструкции Transact-SQL SELECT, содержащей FOR BROWSE.|  
|SQL_CA_SS_COLUMN_ID|Порядковый номер результирующего столбца предложения COMPUTE в текущей инструкции Transact-SQL SELECT.|  
|SQL_CA_SS_COLUMN_KEY*|Значение TRUE, если столбец является частью первичного ключа строки, а инструкция Transact-SQL SELECT содержит FOR BROWSE.|  
|SQL_CA_SS_COLUMN_OP|Целочисленное значение, задающее статистический оператор, ответственный за значение в столбце предложения COMPUTE. Определения целочисленных значений находятся в файле sqlncli.h.|  
|SQL_CA_SS_COLUMN_ORDER|Порядковый номер столбца в предложении ORDER BY инструкции ODBC или Transact-SQL SELECT.|  
|SQL_CA_SS_COLUMN_SIZE|Максимальная длина в байтах, необходимая для привязки значения данных, полученных из столбца, к переменной SQL_C_BINARY.|  
|SQL_CA_SS_COLUMN_SSTYPE|Собственный тип данных, хранящихся в столбце SQL Server. Определения значений типов находятся в файле sqlncli.h.|  
|SQL_CA_SS_COLUMN_UTYPE|Базовый тип данных определяемого пользователем типа данных столбца SQL Server. Определения значений типов находятся в файле sqlncli.h.|  
|SQL_CA_SS_COLUMN_VARYLEN|Значение TRUE, если длина данных столбца может быть разной, в противном случае FALSE.|  
|SQL_CA_SS_COMPUTE_BYLIST|Указатель на массив WORD (unsigned short), задающий столбцы, используемые во фразе BY предложения COMPUTE. Если в предложении COMPUTE не задана фраза BY, возвращается указатель NULL.<br /><br /> Первый элемент массива содержит счетчик столбцов BY. Дополнительные элементы являются порядковыми номерами столбцов.|  
|SQL_CA_SS_COMPUTE_ID|*computeid* строки, которая является результатом предложения COMPUTE в текущей инструкции Transact-SQL SELECT.|  
|SQL_CA_SS_NUM_COMPUTES|Количество предложений COMPUTE, заданных в текущей инструкции Transact-SQL SELECT.|  
|SQL_CA_SS_NUM_ORDERS|Количество столбцов в предложении ORDER BY инструкции ODBC или Transact-SQL SELECT.|  
  
 \*   Доступно, если атрибут инструкции SQL_SOPT_SS_HIDDEN_COLUMNS имеет значение SQL_HC_ON.  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] представлены поля дескриптора для предоставления дополнительных сведений для обозначения имя коллекции схем XML, имя схемы и имени каталога, соответственно. При наличии в этих свойствах неалфавитных символов использование кавычек или escape-символа не требуется. Эти новые поля дескриптора приведены в следующей таблице:  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|SQL_CA_SS_XML_SCHEMACOLLECTION_CATALOG_NAME|CharacterAttributePtr|Имя каталога, в котором определено имя коллекции схем XML. Если обнаружить имя каталога невозможно, то эта переменная содержит пустую строку.<br /><br /> Эти сведения возвращаются из поля записи SQL_DESC_SS_XML_SCHEMACOLLECTION_CATALOG_NAME IRD, предназначенного для чтения и записи.|  
|SQL_CA_SS_XML_SCHEMACOLLECTION_SCHEMA_NAM E|CharacterAttributePtr|Имя схемы, в которой определено имя коллекции схем XML. Если обнаружить имя схемы невозможно, то эта переменная содержит пустую строку.<br /><br /> Эти сведения возвращаются из поля записи SQL_DESC_SS_XML_SCHEMACOLLECTION_SCHEMA_NAME IRD, предназначенного для чтения и записи.|  
|SQL_CA_SS_XML_SCHEMACOLLECTION_NAME|CharacterAttributePtr|Имя коллекции схем XML. Если обнаружить имя невозможно, то эта переменная содержит пустую строку.<br /><br /> Эти сведения возвращаются из поля записи SQL_DESC_SS_XML_SCHEMACOLLECTION_NAME IRD, предназначенного для чтения и записи.|  
  
 Кроме того, в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] представлены новые поля дескриптора для получения дополнительных сведений для столбца результирующего набора с определяемым пользователем типом данных (UDT) и для параметра UDT хранимой процедуры или параметризированного запроса. При наличии в этих свойствах неалфавитных символов использование кавычек или escape-символа не требуется. Эти новые поля дескриптора приведены в следующей таблице:  
  
|Имя столбца|Тип|Описание|  
|-----------------|----------|-----------------|  
|SQL_CA_SS_UDT_CATALOG_NAME|CharacterAttributePtr|Имя каталога, содержащего определяемый пользователем тип.|  
|SQL_CA_SS_UDT_SCHEMA_NAME|CharacterAttributePtr|Имя схемы, содержащей определяемый пользователем тип.|  
|SQL_CA_SS_UDT_TYPE_NAME|CharacterAttributePtr|Имя определяемого пользователем типа.|  
|SQL_CA_SS_UDT_ASSEMBLY_TYPE_NAME|CharacterAttributePtr|Полное имя сборки определяемого пользователем типа.|  
  
 Идентификатор существующего дескриптора поля SQL_DESC_TYPE_NAME используется для указания имени определяемого пользователем типа данных. Поле SQL_DESC_TYPE для столбца определяемого пользователем типа содержит значение SQL_SS_UDT.  
  
## <a name="sqlcolattribute-support-for-enhanced-date-and-time-features"></a>Поддержка SQLColAttribute для усовершенствованных функций даты-времени  
 Для значений, возвращаемых для типов даты и времени, см. в разделе «Сведения возвращаются в полях IRD» в [метаданные параметров и результатов](../../relational-databases/native-client-odbc-date-time/metadata-parameter-and-result.md).  
  
 Дополнительные сведения см. в разделе [время улучшения функций даты и &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlcolattribute-support-for-large-clr-udts"></a>Поддержка SQLColAttribute для больших определяемых пользователем типов CLR  
 **SQLColAttribute** поддерживает большие определяемые пользователем типы CLR (UDT). Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlcolattribute-support-for-sparse-columns"></a>Поддержка SQLColAttribute для разреженных столбцов  
 SQLColAttribute запрашивает поле нового дескриптора (IRD) строки реализации, SQL_CA_SS_IS_COLUMN_SET, чтобы определить, является ли столбец **column_set** столбца.  
  
 Дополнительные сведения см. в разделе [Поддержка разреженных столбцов &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLColAttribute](http://go.microsoft.com/fwlink/?LinkId=59334)   
 [Сведения о реализации API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)  
  
  
