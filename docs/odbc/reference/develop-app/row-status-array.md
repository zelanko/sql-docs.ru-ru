---
title: Массив состояний строк | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- row status array [ODBC]
- cursors [ODBC], block
- result sets [ODBC], row status array
- block cursors [ODBC]
- result sets [ODBC], block cursors
- rowset status [ODBC]
ms.assetid: 4b69f189-2722-4314-8a02-f4ffecd6dabd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 57b187bf4f14bd5c05f91a433fa331e954fa0fb9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020368"
---
# <a name="row-status-array"></a>Массив статусов строк
Помимо данных, **SQLFetch** и **SQLFetchScroll** могут возвращать массив, который предоставляет состояние каждой строки в наборе строк. Этот массив задается с помощью атрибута инструкции SQL_ATTR_ROW_STATUS_PTR. Этот массив выделяется приложением и должен иметь столько же элементов, сколько указано в атрибуте инструкции SQL_ATTR_ROW_ARRAY_SIZE. Значения в массиве задаются с помощью **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**и **SQLSetPos.** Значения описывают состояние строки и значение, указывающее, изменилось ли это состояние со времени последней выборки.  
  
|Значение массива состояния строки|Description|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|Строка была успешно получена и не изменилась со времени последней выборки.|  
|SQL_ROW_SUCCESS_WITH_INFO|Строка была успешно получена и не изменилась со времени последней выборки. Однако в строке было возвращено предупреждение.|  
|SQL_ROW_ERROR|Произошла ошибка при выборке строки.|  
|SQL_ROW_UPDATED|Строка была успешно получена и была обновлена с момента последней выборки. Если строка извлекается повторно или обновляется с помощью функции **SQLSetPos**, ее состояние меняется на новое состояние.<br /><br /> Некоторые драйверы не могут обнаруживать изменения в данных и поэтому не могут возвращать это значение. Чтобы определить, может ли драйвер обнаружить обновления для повторной выборки строк, приложение вызывает **SQLGetInfo** с параметром SQL_ROW_UPDATES.|  
|SQL_ROW_DELETED|Строка была удалена с момента последней выборки.|  
|SQL_ROW_ADDED|Строка была вставлена с помощью **SQLBulkOperations**. Если строка извлекается повторно или обновляется с помощью функции **SQLSetPos**, ее состояние — SQL_ROW_SUCCESS.<br /><br /> Это значение не задается **SQLFetch** или **SQLFetchScroll**.|  
|SQL_ROW_NOROW|Набор строк, перекрывающийся с концом результирующего набора, и ни одна строка не была возвращена, соответствующая этому элементу массива состояния строки.|
