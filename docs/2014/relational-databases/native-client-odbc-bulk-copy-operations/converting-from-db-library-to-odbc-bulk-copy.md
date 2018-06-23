---
title: Преобразование из DB-Library для массового копирования ODBC | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- converting DB-Library to ODBC bulk copy
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], DB-Library bulk copy
- ODBC, bulk copy operations
- DB-Library bulk copy
ms.assetid: 0bc15bdb-f19f-4537-ac6c-f249f42cf07f
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b623bb2e0814ec3b03800af5ef54028b5ef0ac5e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098395"
---
# <a name="converting-from-db-library-to-odbc-bulk-copy"></a>Перевод массового копирования с DB-Library на ODBC
  Преобразование функции массового копирования DB-Library на ODBC прост, так как поддерживаемые функции массового копирования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента похожи на функции массового копирования DB-Library, за исключением следующих случаев:  
  
-   Приложения DB-Library передают указатель на структуру DBPROCESS как первый параметр функций массового копирования. В приложениях ODBC указатель DBPROCESS заменяется дескриптором соединения ODBC.  
  
-   Приложения DB-Library вызывают **BCP_SETL** перед подключением для включения операций массового копирования для DBPROCESS. Приложения ODBC вместо этого вызовите [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) перед соединением, чтобы обеспечить массовые операции для дескриптора соединения:  
  
    ```  
    SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP,  
        (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
    ```  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC для собственного клиента не поддерживает обработчики сообщений и ошибок DB-Library; необходимо вызвать **SQLGetDiagRec** для получения ошибок и сообщений, формируемых функциями массового копирования ODBC. Версии ODBC функций массового копирования возвращают стандартные коды возврата массового копирования SUCCEED или FAILED, а не коды возврата ODBC, такие как SQL_SUCCESS или SQL_ERROR.  
  
-   Значения, указанные для DB-Library [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)*varlen* интерпретируются не так, как ODBC **bcp_bind *** cbData* параметра.  
  
    |Указанное условие|DB-Library *varlen* значение|ODBC *cbData* значение|  
    |-------------------------|--------------------------------|-------------------------|  
    |Предоставлены значения NULL|0|-1 (SQL_NULL_DATA)|  
    |Предоставлены данные переменной длины|-1|-10 (SQL_VARLEN_DATA)|  
    |Символьная или двоичная строка нулевой длины|Н/Д|0|  
  
     В DB-Library *varlen* значение -1 указывает, что предоставлены данные переменной длины, а в ODBC *cbData* означает, что предоставлены только значения NULL. Изменить DB-Library *varlen* -1 в значение SQL_VARLEN_DATA, а также любые *varlen* спецификации от 0 до SQL_NULL_DATA.  
  
-   DB-Library  **bcp_colfmt *** file_collen* и ODBC [bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)* cbUserData * уже же проблема **bcp_bind *** varlen*и *cbData* описанных выше параметров. Изменить DB-Library *file_collen* -1 в значение SQL_VARLEN_DATA, а также любые *file_collen* спецификации от 0 до SQL_NULL_DATA.  
  
-   *IValue* параметр ODBC [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) функция является указателем на void. В DB-Library *iValue* имело тип integer. Приведение значений для ODBC *iValue* на тип void *.  
  
-   **Bcp_control** параметр BCPMAXERRS указывает, сколько отдельных строк могут вызвать ошибки, прежде чем операция массового копирования завершится неудачей. BCPMAXERRS по умолчанию — 0 (отказ при первой ошибке) в версии DB-Library **bcp_control** и 10 версия ODBC. Приложения DB-Library, которые зависят от 0 до завершения операции массового копирования по умолчанию необходимо изменить вызов ODBC **bcp_control** для BCPMAXERRS значение 0.  
  
-   ODBC **bcp_control** функция поддерживает следующие параметры, не поддерживается в версии DB-Library **bcp_control**:  
  
    -   BCPODBC  
  
         Если задано значение TRUE указывает, что **datetime** и **smalldatetime** будут иметь значения, сохраненные в символьном формате, управляющие последовательности ODBC timestamp префикс и суффикс. Это относится только к операциям BCP_OUT.  
  
         Bcpodbc имеет значение FALSE **datetime** вывести значение, преобразованное в строку символов в виде:  
  
        ```  
        1997-01-01 00:00:00.000  
        ```  
  
         Bcpodbc устанавливается значение TRUE, то же **datetime** значение выводится так:  
  
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
  
-   ODBC **bcp_colfmt** функция не поддерживает *file_type* индикатор типа данных SQLCHAR, так как он конфликтует с определением типа ODBC SQLCHAR. Вместо него используйте SQLCHARACTER для **bcp_colfmt**.  
  
-   В ODBC-версиях функций массового копирования, формат для работы с **datetime** и **smalldatetime** значения в символьных строках — формат ODBC гггг мм дд чч:мм:сс.ссс; **smalldatetime** значений используется формат ODBC гггг мм дд чч.  
  
     Версии DB-Library функций массового копирования принимают **datetime** и **smalldatetime** в символьных строках в следующих форматах:  
  
    -   По умолчанию используется формат *ммм дд гггг чч: ммxx* где *xx* AM или PM.  
  
    -   **DateTime** и **smalldatetime** символьные строки в любой формат, поддерживаемый DB-Library **dbconvert** функции.  
  
    -   При **использовать Международные настройки** флажок на DB-Library **параметры** вкладке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Network Utility, функции массового копирования DB-Library также принимают даты в региональном формат даты, определен в качестве параметра языковой стандарт в реестре клиентского компьютера.  
  
     Функции массового копирования DB-Library не принимают ODBC **datetime** и **smalldatetime** форматы.  
  
     Если атрибут инструкции SQL_SOPT_SS_REGIONALIZE установлен в значение SQL_RE_ON, функции массового копирования ODBC принимают даты в региональном формате данных, определенном для локали, установленной в реестре клиентского компьютера.  
  
-   При выводе **money** значения в символьном формате, ODBC массового копирования функции питания четыре цифры точности и без запятых-разделителей; Только версии DB-Library предоставить двух цифр, точности и включают запятые-разделители.  
  
## <a name="see-also"></a>См. также  
 [Выполнение операций массового копирования &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)   
 [Функции массового копирования](../native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  