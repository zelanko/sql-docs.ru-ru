---
title: Число получаемых строк и состояние | Документация Майкрософт
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086334"
---
# <a name="number-of-rows-fetched-and-status"></a>Число строк в выборке и состояние
Если задана инструкция атрибута sql_attr_rows_fetched_ptr, которое указывает, он указывает буфера, который возвращает количество строк, вызов **SQLFetch** или **SQLFetchScroll**и ошибочных строк. (Это число является подсчет количества строк, у которых нет состояние SQL_ROW_NO_ROWS). После вызова **SQLBulkOperations** или **SQLSetPos**, буфер содержит количество строк, затронутых массовой операции, выполняемые с помощью функции. Если атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR **SQLFetch** или **SQLFetchScroll** возвращает *массив статусов строк,* который предоставляет сведения о состоянии каждого из них Возвращенная строка. Оба буферов, на которые указывают эти поля являются выделенная приложением и заполняется с помощью драйвера. Приложения необходимо убедиться в том, что эти указатели останутся действительными до закрытия курсора.  
  
 Записи в текущее состояние строки состояния массива ли каждая строка успешно, получено ли его обновления, добавленных или удаленных с момента последней загрузки, а также ли произошла ошибка при извлечении строки. Если **SQLFetch** или **SQLFetchScroll** возникает ошибка при извлечении одной строки многострочной набора строк, или если **SQLBulkOperations** с *операции*  аргумент SQL_FETCH_BY_BOOKMARK обнаруживает ошибку при выполнении массовой выборка, он задает соответствующее значение в массив статусов строк для SQL_ROW_ERROR, по-прежнему выборка строк и возвращает значение SQL_SUCCESS_WITH_INFO. Дополнительные сведения об обработке ошибок и массив статусов строк см. в разделе [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md) и [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) описания функции.
