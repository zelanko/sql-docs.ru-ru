---
title: Количество строк, извлеченных и статус (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 20e1632e8da765b0da2785bd846b67d13ebe01ed
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302365"
---
# <a name="number-of-rows-fetched-and-status"></a>Число строк в выборке и состояние
Если атрибут SQL_ATTR_ROWS_FETCHED_PTR оператора установлен, он определяет буфер, который возвращает количество строк, извлеченных вызовом, в **S'LFetch** или **S'LFetchScroll,** и строки ошибок. (Это число представляет собой количество всех строк, которые не имеют статуса SQL_ROW_NO_ROWS.) После вызова в **S'LBulkOperations** или **S'LSetPos**буфер содержит количество строк, которые были затронуты основной операцией, выполняемой функцией. Если атрибут SQL_ATTR_ROW_STATUS_PTR оператора установлен, **S'LFetch** или **S'LFetchScroll** возвращает *массив состояния строки,* который обеспечивает статус каждой возвращенной строки. Оба буфера, на которые указывают эти поля, выделяются приложением и заполняются водителем. Приложение должно убедиться, что эти указатели остаются действительными до тех пор, пока курсор не будет закрыт.  
  
 Записи в массиве состояния строки заявляют, была ли каждая строка успешно извлечена, была ли она обновлена, добавлена или удалена с момента ее последнего извлечения, и произошла ли ошибка при извлечении строки. Если **S'LFetch** или **S'LFetchScroll** сталкиваются с ошибкой при получении одного ряда многороу-ряда, или если **S'LBulkOperations** с *аргументом операции* SQL_FETCH_BY_BOOKMARK сталкивается с ошибкой при выполнении объемного извлечения, он устанавливает соответствующее значение в массиве состояния строки, чтобы SQL_ROW_ERROR, продолжает изгонять строки, и возвращает SQL_SUCCESS_WITH_INFO. Для получения дополнительной информации об обработке [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md) ошибок и [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) массиве состояния строки см.
