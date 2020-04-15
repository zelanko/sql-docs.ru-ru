---
title: Коды ошибки библиотеки ODBC Cursor (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c263ce53c41546e63dc2a830d3db3b903e2e3515
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301435"
---
# <a name="odbc-cursor-library-error-codes"></a>Коды ошибок для библиотеки курсоров ODBC
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии компонента доступа к данным Майкрософт. Избегайте использования этой функции в новых разработках и планируйте модифицировать приложения, использующие эту функцию в настоящее время. Вместо этого используйте курсоры драйверов и серверов.  
  
 Библиотека курсоров ODBC возвращает следующие S'LSTATEs в дополнение к тем, которые перечислены в [справке ODBC API.](../../../odbc/reference/syntax/odbc-api-reference.md)  
  
> [!NOTE]  
>  Библиотека курсора не заказывает записи статуса; менеджер водителя и ODBC 3. *x* драйверы несут ответственность за заказ записей о состоянии.  
  
|SQLSTATE|Описание|Может быть возвращен из|  
|--------------|-----------------|--------------------------|  
|01000|Курсор не updatable.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|01000|Библиотека Курсора не используется. Нагрузка не удалась.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Библиотека Курсора не используется. Недостаточная поддержка водителя.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Библиотека Курсора не используется. Несоответствие версии с менеджером драйвера.|**SQLBrowseConnect**<br /><br /> **SQLConnect**<br /><br /> **SQLDriverConnect**|  
|01000|Водитель вернулся SQL_SUCCESS_WITH_INFO. Предупреждение было потеряно.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|S1000|Общая ошибка: Невозможно создать буфер файла.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Общая ошибка: Невозможно прочитать из буфера файла.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Общая ошибка: Невозможно написать для буфера файла.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|S1000|Общая ошибка: Невозможно закрыть или удалить буфер файла.|**SQLFreeHandle**<br /><br /> **Функция SQLFreeStmt**|  
|SL001|Позиционированный запрос не может быть выполнен, поскольку не были связаны столбцы поиска.|**SQLExecDirect**<br /><br /> **SQLGetData**<br /><br /> **SQLPrepare**|  
|SL002|Позиционированный запрос не может быть выполнен, поскольку набор результатов был создан условием соединения.|**SQLExecute**<br /><br /> **SQLExecDirect**<br /><br /> **SQLGetData**|  
|SL003|Связанный буфер превышает максимальный размер сегмента.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL004|Набор результатов не был создан выпиской **SELECT.**|**SQLGetData**|  
|SL005|**Заявление SELECT** содержит оговорку GROUP BY.|**SQLGetData**|  
|SL006|Параметры не поддерживаются позиционированными запросами.|**SQLPrepare**<br /><br /> **SQLExecDirect**|  
|SL008|**Не** допускается на курсоре только вперед (не буферный).|**SQLGetData**|  
|SL009|Никакие столбцы не были связаны до вызова **S'LFetch** или **S'LFetchScroll**.|**SQLFetch**<br /><br /> **SQLFetchScroll**|  
|SL010|**S'LBindCol** вернулся SQL_ERROR во время попытки привязать к внутреннему буферу.|**SQLFetch**<br /><br /> **SQLFetchScroll**<br /><br /> **SQLGetData**|  
|SL011|Опция выписки действительна только после вызова **S'LFetch** или **S'LFetchScroll**.|**SQLGetStmtAttr**|  
|SL012|Привязки к выписке не могут быть изменены при открытии курсора.|**SQLBindCol**<br /><br /> **SQLFreeHandle**<br /><br /> **Функция SQLFreeStmt**<br /><br /> **SQLSetStmtAttr**|  
|SL014|Был выдан позиционированный запрос, и не все поля подсчета столбцов были буферизированы.|**SQLExecDirect**<br /><br /> **SQLExecute**<br /><br /> **SQLPrepare**|  
|SL015|Не могут быть смешаны **S'LFetch** и **S'LFetchScroll.**|**Sqlextendedfetch**<br /><br /> **SQLFetch**<br /><br /> **SQLFetchScroll**|
