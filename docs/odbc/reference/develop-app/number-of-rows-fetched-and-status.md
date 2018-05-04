---
title: Число строк, загружаемых и состояние | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- row status array [ODBC]
- number of rows fetched [ODBC]
- result sets [ODBC], row status array
ms.assetid: a069b979-5108-4905-932f-8ae8e7905ff2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e699cc8c0272a1221b0148a8d7b2c65da9e3e6c7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="number-of-rows-fetched-and-status"></a>Число строк, загружаемых и состояние
Если задан атрибут инструкции SQL_ATTR_ROWS_FETCHED_PTR, он указывает буфера, который возвращает число строк, возвращаемых при вызове **SQLFetch** или **SQLFetchScroll**и строк с ошибками. (Это число представляет собой число всех строк, которые не имеют состояния SQL_ROW_NO_ROWS). После вызова **SQLBulkOperations** или **SQLSetPos**, буфер содержит число строк, измененных в ходе массовой операции, выполняемой функцией. Если атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR **SQLFetch** или **SQLFetchScroll** возвращает *массив состояния строк,* предоставляющее состояние каждого Возвращенная строка. Оба буферов, который указывает эти поля выделенных приложением и заполняется драйвером. Приложению необходимо убедиться, что эти указатели останутся действительными до закрытия курсора.  
  
 Записи в состояние строки состояния массива ли каждой строки, которые были выбраны успешно, будет ли он был обновлен, добавлены или удалены с момента последней загрузки, так и произошла ошибка при получении строки. Если **SQLFetch** или **SQLFetchScroll** возникает ошибка при извлечении одной строки многострочные набора строк, или если **SQLBulkOperations** с *операции*  аргумент SQL_FETCH_BY_BOOKMARK возникает ошибка во время выполнения массовой выборки, задает соответствующее значение в массиве строк состояния для SQL_ROW_ERROR, по-прежнему выборки строк и возвращает значение SQL_SUCCESS_WITH_INFO. Дополнительные сведения об обработке ошибок и массив состояния строк см. в разделе [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md) и [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) функции описания.
