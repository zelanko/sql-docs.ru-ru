---
title: Преобразование из DB-Library в "групповое копирование ODBC" | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- converting DB-Library to ODBC bulk copy
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], DB-Library bulk copy
- ODBC, bulk copy operations
- DB-Library bulk copy
ms.assetid: 0bc15bdb-f19f-4537-ac6c-f249f42cf07f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8f41438f8ecd7a905201b8f912b3fee142716a2c
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71708084"
---
# <a name="converting-from-db-library-to-odbc-bulk-copy"></a>Перевод массового копирования с DB-Library на ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Преобразование программы пакетного копирования DB-Library в ODBC несложно, поскольку функции копирования, поддерживаемые драйвером ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], похожи на функции операций с массовым копированием DB-Library, за исключением следующих.  
  
-   Приложения DB-Library передают указатель на структуру DBPROCESS как первый параметр функций массового копирования. В приложениях ODBC указатель DBPROCESS заменяется дескриптором соединения ODBC.  
  
-   Приложения DB-Library вызывают **BCP_SETL** перед подключением, чтобы включить операции с массовым копированием в дбпроцесс. Приложения ODBC вместо этого вызывают [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) перед подключением, чтобы включить групповые операции для маркера подключения:  
  
    ```  
    SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP,  
        (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
    ```  
  
-   Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает сообщения и обработчики ошибок DB-Library. для получения ошибок и сообщений, вызванных функциями операций с массовым копированием ODBC, необходимо вызвать **SQLGetDiagRec** . Версии ODBC функций массового копирования возвращают стандартные коды возврата массового копирования SUCCEED или FAILED, а не коды возврата ODBC, такие как SQL_SUCCESS или SQL_ERROR.  
  
-   Значения, указанные для параметра DB-Library [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)*Варлен* , обрабатываются иначе, чем параметр ODBC **bcp_bind**_cbData_ .  
  
    |Указанное условие|Значение *ВАРЛЕН* DB-Library|Значение *CBDATA* ODBC|  
    |-------------------------|--------------------------------|-------------------------|  
    |Предоставлены значения NULL|0|-1 (SQL_NULL_DATA)|  
    |Предоставлены данные переменной длины|-1|-10 (SQL_VARLEN_DATA)|  
    |Символьная или двоичная строка нулевой длины|Н/Д|0|  
  
     В DB-Library значение *Варлен* , равное-1, указывает, что данные переменной длины передаются, что в ODBC *cbData* интерпретируется таким же, что предоставляются только значения NULL. Измените все спецификации *ВАРЛЕН* DB-Library с-1 на SQL_VARLEN_DATA и все спецификации *Варлен* от 0 до SQL_NULL_DATA.  
  
-   Библиотеки DB-Library **bcp_colfmt**_file_collen_ и ODBC [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)*cbUserData* имеют те же проблемы, что и **Параметры bcp_bind**_Варлен_ и *cbData* , указанные выше. Измените все спецификации *FILE_COLLEN* DB-Library с-1 на SQL_VARLEN_DATA и все спецификации *file_collen* от 0 до SQL_NULL_DATA.  
  
-   Параметр *iValue* функции ODBC [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) является указателем void. В DB-Library *iValue* был целым числом. Приведите значения для *IVALUE* ODBC к void *.  
  
-   Параметр **BCP_CONTROL** BCPMAXERRS указывает, сколько отдельных строк может содержать ошибки до тех пор, пока операция копирования не завершится ошибкой. По умолчанию для BCPMAXERRS задано значение 0 (ошибка при первой ошибке) в версии **BCP_CONTROL** DB-Library и 10 в версии ODBC. Приложения DB-Library, зависящие от значения по умолчанию 0 для завершения операции копирования, необходимо изменить для вызова **BCP_CONTROL** ODBC, чтобы установить BCPMAXERRS в значение 0.  
  
-   Функция ODBC **bcp_control** поддерживает следующие параметры, не ПОДДЕРЖИВАЕМЫЕ версией DB-Library для **bcp_control**:  
  
    -   BCPODBC  
  
         Если задано значение TRUE, то указывает, что значения **DateTime** и **smalldatetime** , сохраненные в символьном формате, будут иметь префикс escape-последовательности и суффикс последовательного времени ODBC. Это относится только к операциям BCP_OUT.  
  
         Если параметр BCPODBC имеет значение FALSE, то значение **DateTime** , преобразованное в символьную строку, выводится следующим образом:  
  
        ```  
        1997-01-01 00:00:00.000  
        ```  
  
         Если для BCPODBC задано значение TRUE, то то же значение **DateTime** выводится следующим образом:  
  
        ```  
        {ts '1997-01-01 00:00:00.000' }  
        ```  
  
    -   BCPKEEPIDENTITY  
  
         Значение TRUE указывает, что функции массового копирования вставляют значения данных, предоставленные для столбцов с ограничениями идентификаторов. Если эти значения не заданы, то для вставляемых строк создаются новые значения идентификаторов.  
  
    -   BCPHINTS  
  
         Определяет различные оптимизации для массового копирования. Этот параметр не может использоваться в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 и более ранних версиях.  
  
    -   BCPFILECP  
  
         Задает кодовую страницу файла массового копирования.  
  
    -   BCPUNICODEFILE  
  
         Указывает, что файл массового копирования в символьном формате является файлом в Юникоде.  
  
-   Функция ODBC **bcp_colfmt** не поддерживает индикатор *file_type* для SQLCHAR, так как он конфликтует с ОПРЕДЕЛЕНИЕМ типа данных ODBC SQLCHAR. Вместо него используйте SQLCHARACTER для **bcp_colfmt**.  
  
-   В версиях ODBC для функций операций с массовым копированием формат для работы с значениями **DateTime** и **smalldatetime** в символьных строках — это формат ODBC в формате "гггг-мм-дд чч: мм: СС. SSS;" значения **smalldatetime** используют формат ODBC в формате "гггг-мм-дд чч: мм: СС".  
  
     Версии DB-Library функций с массовым копированием принимают значения **DateTime** и **smalldatetime** в символьных строках с использованием нескольких форматов:  
  
    -   Формат по умолчанию — *МММ дд гггг чч: ммxx* , где *XX* — AM или PM.  
  
    -   строки символов **DateTime** и **smalldatetime** в любом формате, поддерживаемом функцией DB-Library **дбконверт** .  
  
    -   Если флажок **использовать международные параметры** установлен на вкладке **Параметры** DB-Library в служебной программе клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], функции операций с массовым копированием DB-Library также принимают даты в региональном формате, определенном для параметра языкового стандарта клиента. реестр компьютера.  
  
     Функции операций с массовым копированием DB-Library не принимают форматы **DateTime** и **smalldatetime** ODBC.  
  
     Если атрибут инструкции SQL_SOPT_SS_REGIONALIZE установлен в значение SQL_RE_ON, функции массового копирования ODBC принимают даты в региональном формате данных, определенном для локали, установленной в реестре клиентского компьютера.  
  
-   При вводе **денежных** значений в символьном формате функции выполнения операций с массовым копированием ODBC предоставляют четыре цифры точности и без разделителей запятой. Версии DB-Library предоставляют только две цифры точности и включают разделители-запятые.  
  
## <a name="see-also"></a>См. также  
 [Выполнение операций &#40;с массовым&#41;копированием ODBC](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)   
 [Функции массового копирования](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
