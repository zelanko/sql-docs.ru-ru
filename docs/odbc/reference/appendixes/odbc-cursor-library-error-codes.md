---
title: "Коды ошибок библиотеки курсоров ODBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursor library [ODBC], error codes
- error codes [ODBC], cursor library
- ODBC cursor library [ODBC], error codes
ms.assetid: 9713480e-8744-4f37-a630-20871590d4a1
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4a182979a037ec21f7d86d907bb0f0c2a020191a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-cursor-library-error-codes"></a>Коды ошибок библиотеки курсоров ODBC
> [!IMPORTANT]  
>  Этот компонент будет удален в будущей версии компонентов доступа к данным Microsoft. Избегайте использования этой возможности в новых разработках и запланируйте изменение приложений, которые сейчас ее используют. Вместо этого используйте курсоры драйвера и сервера.  
  
 Библиотека курсоров ODBC возвращает следующие атрибуты SQLSTATE, кроме перечисленных в [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md).  
  
> [!NOTE]  
>  Библиотека курсоров не упорядочивает записи состояния; Диспетчер драйверов и ODBC 3. *x* драйверы отвечают за упорядочения записей состояния.  
  
|SQLSTATE|Description|Могут быть возвращены из|  
|--------------|-----------------|--------------------------|  
|01000|Курсор не является обновляемым.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|01000|Библиотека курсоров не используется. Не удалось загрузить.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Библиотека курсоров не используется. Поддержка драйверов недостаточно.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Библиотека курсоров не используется. Несоответствие версий с помощью диспетчера драйверов.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Драйвер возвращается SQL_SUCCESS_WITH_INFO. Предупреждающее сообщение было потеряно.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|S1000|Общая ошибка: не удается создать буфер для файла.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Общая ошибка: не удалось прочитать из буфера файла.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Общая ошибка: не удается записать файл буфера.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Общая ошибка: не удается закрыть или удалить файл буфера.|**SQLFreeHandle**<br /><br /> **SQLFreeStmt**|  
|SL001|Позиционированные запроса невозможно, поскольку для поиска столбцы не были привязаны.|**SQLExecDirect**<br /><br /> **SQLGetData**<br /><br /> **SQLPrepare**|  
|SL002|Не удалось выполнить позиционированные запрос, так как результирующий набор был создан в условии соединения.|**SQLExecute**<br /><br /> **SQLExecDirect**<br /><br /> **SQLGetData**|  
|SL003|Привязанные буфера превышает максимальный размер.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL004|Результирующий набор не была создана **ВЫБЕРИТЕ** инструкции.|**SQLGetData**|  
|SL005|**ВЫБЕРИТЕ** инструкция содержит предложение GROUP BY.|**SQLGetData**|  
|SL006|Массивы параметров не поддерживаются с позиционированием запросов.|**SQLPrepare**<br /><br /> **SQLExecDirect**|  
|SL008|**SQLGetData** недопустимо для однонаправленного курсора (безбуферный).|**SQLGetData**|  
|SL009|Столбцы не были привязаны до вызова метода **SQLFetch** или **SQLFetchScroll**.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL010|**SQLBindCol** возвращает значение SQL_ERROR во время попытки привязки во внутренний буфер.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|SL011|Параметр инструкции действителен только после вызова метода **SQLFetch** или **SQLFetchScroll**.|**SQLGetStmtAttr**|  
|SL012|Инструкции привязки не могут изменяться при открытом курсоре.|**SQLBindCol**<br /><br /> **SQLFreeHandle**<br /><br /> **SQLFreeStmt**<br /><br /> **SQLSetStmtAttr**|  
|SL014|Позиционированные запроса и не все поля число столбцов были помещен в буфер.|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|SL015|**SQLFetch** и **SQLFetchScroll** нельзя смешивать.|**SQLExtendedFetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**|
