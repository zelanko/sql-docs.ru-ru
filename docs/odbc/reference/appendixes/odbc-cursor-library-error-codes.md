---
title: Коды ошибок для библиотеки курсоров ODBC | Документация Майкрософт
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100671"
---
# <a name="odbc-cursor-library-error-codes"></a>Коды ошибок для библиотеки курсоров ODBC
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях компонента доступа к данным Microsoft. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Вместо этого используйте курсоры драйвера и сервера.  
  
 Библиотека курсоров ODBC возвращает следующие SQLSTATE, кроме перечисленных в [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md).  
  
> [!NOTE]  
>  Библиотека курсоров не упорядочивает записи состояния; Диспетчер драйверов и ODBC 3. *x* драйверы несут ответственность за упорядочение записи состояния.  
  
|SQLSTATE|Описание|Могут быть возвращены из|  
|--------------|-----------------|--------------------------|  
|01000|Курсор не является обновляемым.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|01000|Библиотека курсоров не используется. Не удалось загрузить.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Библиотека курсоров не используется. Поддержка драйверов недостаточно.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Библиотека курсоров не используется. Несовпадение версий с помощью диспетчера драйверов.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Драйвер возвращается SQL_SUCCESS_WITH_INFO. Предупреждающее сообщение было потеряно.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|S1000|Общая ошибка: Не удалось создать буфер для файла.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Общая ошибка: Не удается прочитать из файла буфера.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Общая ошибка: Не удалось записать файл буфера.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Общая ошибка: Не удалось закрыть или удалить файловый буфер.|**SQLFreeHandle**<br /><br /> **SQLFreeStmt**|  
|SL001|Невозможно выполнить позиционированные запрос, так как нет доступных для поиска столбцов были привязаны.|**SQLExecDirect**<br /><br /> **SQLGetData**<br /><br /> **SQLPrepare**|  
|SL002|Позиционированные запрос не может быть выполнена, так как результирующий набор был создан в условии соединения.|**SQLExecute**<br /><br /> **SQLExecDirect**<br /><br /> **SQLGetData**|  
|SL003|Привязанные буфера превышает максимальный размер.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL004|Результирующий набор не была создана **ВЫБЕРИТЕ** инструкции.|**SQLGetData**|  
|SL005|**ВЫБЕРИТЕ** инструкция содержит предложение GROUP BY.|**SQLGetData**|  
|SL006|Массивы параметров не поддерживает позиционированные запросов.|**SQLPrepare**<br /><br /> **SQLExecDirect**|  
|SL008|**SQLGetData** не разрешена для курсора последовательного доступа (безбуферный).|**SQLGetData**|  
|SL009|Столбцы не были привязаны перед вызовом метода **SQLFetch** или **SQLFetchScroll**.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL010|**SQLBindCol** возвращает значение SQL_ERROR во время попытки привязки к внутренний буфер.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|SL011|Параметр инструкции является допустимым только после вызова метода **SQLFetch** или **SQLFetchScroll**.|**SQLGetStmtAttr**|  
|SL012|В инструкции привязки не может быть изменен, когда курсор открыт.|**SQLBindCol**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLFreeStmt**<br /><br /> **SQLSetStmtAttr**|  
|SL014|Позиционированные запроса и не все поля число столбцов были помещен в буфер.|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|SL015|**SQLFetch** и **SQLFetchScroll** нельзя комбинировать.|**SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**|
