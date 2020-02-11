---
title: Количество выбранных строк и состояние | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- row status array [ODBC]
- number of rows fetched [ODBC]
- result sets [ODBC], row status array
ms.assetid: a069b979-5108-4905-932f-8ae8e7905ff2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bc1f556873221faa3f86c5272120a786f6f25025
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086334"
---
# <a name="number-of-rows-fetched-and-status"></a>Число строк в выборке и состояние
Если задан атрибут инструкции SQL_ATTR_ROWS_FETCHED_PTR, он задает буфер, который возвращает количество строк, полученных вызовом **SQLFetch** или **SQLFetchScroll**, и строками ошибок. (Это число представляет собой количество всех строк, в которых отсутствует состояние SQL_ROW_NO_ROWS.) После вызова **SQLBulkOperations** или **SQLSetPos**буфер содержит количество строк, затронутых массовыми операциями, выполненными функцией. Если задан атрибут инструкции SQL_ATTR_ROW_STATUS_PTR, **SQLFetch** или **SQLFetchScroll** возвращает *массив состояний строк,* который обеспечивает состояние каждой возвращаемой строки. Оба буфера, на которые указывают эти поля, выделяются приложением и заполняются драйвером. Приложение должно убедиться, что эти указатели остаются действительными до закрытия курсора.  
  
 Записи в массиве состояния строк изменяют, была ли каждая строка успешно получена, была ли она обновлена, добавлена или удалена с момента последней выборки и произошла ли ошибка при выборке строки. Если в **SQLFetch** или **SQLFetchScroll** возникла ошибка при получении одной строки набора строк многострочные или если **SQLBulkOperations** с аргументом *операции* SQL_FETCH_BY_BOOKMARK встречает ошибку при выполнении групповой выборки, он устанавливает соответствующее значение в массиве состояния строки для SQL_ROW_ERROR, возобновляет выборку строк и возвращает SQL_SUCCESS_WITH_INFO. Дополнительные сведения об обработке ошибок и массиве состояния строк см. в описании функций [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md) и [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) .
