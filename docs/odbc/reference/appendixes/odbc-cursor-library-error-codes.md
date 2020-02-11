---
title: Коды ошибок библиотеки курсоров ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursor library [ODBC], error codes
- error codes [ODBC], cursor library
- ODBC cursor library [ODBC], error codes
ms.assetid: 9713480e-8744-4f37-a630-20871590d4a1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a3fb86e1332e3b7e4d89003ccf6421151e5d9cec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68100671"
---
# <a name="odbc-cursor-library-error-codes"></a>Коды ошибок для библиотеки курсоров ODBC
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии компонента доступа к данным Microsoft. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Вместо этого используйте курсоры драйвера и сервера.  
  
 Библиотека курсоров ODBC возвращает следующие SQLSTATE в дополнение к тем, которые перечислены в [справочнике по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md).  
  
> [!NOTE]  
>  Библиотека курсоров не упорядочивает записи состояния. Диспетчер драйверов и ODBC 3. драйверы *x* отвечают за упорядочение записей о состоянии.  
  
|SQLSTATE|Description|Можно вернуть из|  
|--------------|-----------------|--------------------------|  
|01000|Невозможно обновить курсор.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|01000|Библиотека курсоров не используется. Сбой загрузки.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Библиотека курсоров не используется. Недостаточная поддержка драйвера.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Библиотека курсоров не используется. Несовпадение версий с диспетчером драйверов.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Драйвер возвратил SQL_SUCCESS_WITH_INFO. Сообщение с предупреждением потеряно.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|S1000|Общая ошибка: не удалось создать файловый буфер.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Общая ошибка: не удается выполнить чтение из буфера файла.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Общая ошибка: не удается выполнить запись в файловый буфер.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Общая ошибка: не удается закрыть или удалить файловый буфер.|**SQLFreeHandle**<br /><br /> **Функция SQLFreeStmt**|  
|SL001|Невозможно выполнить позиционированный запрос, так как нет привязанных столбцов с возможностью поиска.|**SQLExecDirect**<br /><br /> **SQLGetData**<br /><br /> **SQLPrepare**|  
|SL002|Не удалось выполнить позиционированный запрос, так как результирующий набор был создан условием объединения.|**SQLExecute**<br /><br /> **SQLExecDirect**<br /><br /> **SQLGetData**|  
|SL003|Связанный буфер превышает максимальный размер сегмента.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL004|Результирующий набор не был создан инструкцией **SELECT** .|**SQLGetData**|  
|SL005|Инструкция **SELECT** содержит предложение GROUP BY.|**SQLGetData**|  
|SL006|Массивы параметров не поддерживаются в позиционированных запросах.|**SQLPrepare**<br /><br /> **SQLExecDirect**|  
|SL008|**SQLGetData** не разрешено использовать в однонаправленном (небуферизованном) курсоре.|**SQLGetData**|  
|SL009|Ни один столбец не был привязан до вызова **SQLFetch** или **SQLFetchScroll**.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL010|**SQLBindCol** вернул SQL_ERROR во время попытки привязки к внутреннему буферу.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|SL011|Параметр инструкции допустим только после вызова **SQLFetch** или **SQLFetchScroll**.|**SQLGetStmtAttr**|  
|SL012|Привязки инструкций не могут изменяться, пока курсор открыт.|**SQLBindCol**<br /><br /> **SQLFreeHandle**<br /><br /> **Функция SQLFreeStmt**<br /><br /> **SQLSetStmtAttr**|  
|SL014|Был выдан размещенный запрос, и не все столбцы были помещены в буфер.|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|SL015|**SQLFetch** и **SQLFetchScroll** не могут быть смешанными.|**SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**|
