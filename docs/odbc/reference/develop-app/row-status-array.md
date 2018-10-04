---
title: Массив состояния строк | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 1d2a04f5052a0b686d3669c976ec7c4bee09e52b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706412"
---
# <a name="row-status-array"></a>Массив статусов строк
В дополнение к данным **SQLFetch** и **SQLFetchScroll** может возвращать массив, который задает статус каждой строки в наборе строк. Этот массив указывается через атрибут значения SQL_ATTR_ROW_STATUS_PTR инструкции. Этот массив выделенная приложением и должен иметь столько элементов задаются с помощью атрибута SQL_ATTR_ROW_ARRAY_SIZE инструкции. Задаются значения в массиве **SQLBulkOperations**, **SQLFetch**, **SQLFetchScroll**, и **SQLSetPos.** Значения описывают состояние строки, а также изменилось ли состояние с момента последней загрузки.  
  
|Значение массива строки состояния|Описание|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|Строка была успешно получен и не изменилась со времени последней загрузки.|  
|SQL_ROW_SUCCESS_WITH_INFO|Строка была успешно получен и не изменилась со времени последней загрузки. Тем не менее предупреждение было возвращено о строке.|  
|SQL_ROW_ERROR|Произошла ошибка при извлечении строки.|  
|SQL_ROW_UPDATED|Строка была успешно сделана выборка и изменился со времени последней загрузки. Если строки заново извлечь или обновить, **SQLSetPos**, его состояние изменяется на новое состояние.<br /><br /> Некоторые драйверы не может обнаружить изменения данных и поэтому не может возвращать это значение. Чтобы определить, может ли драйвер определить обновления refetched строк, приложение вызывает **SQLGetInfo** с параметром SQL_ROW_UPDATES.|  
|ЗНАЧЕНИЕ SQL_ROW_DELETED|Строка была удалена с момента последней загрузки.|  
|SQL_ROW_ADDED|Строка была вставлена **SQLBulkOperations**. Если строка выбирается заново или обновляется в **SQLSetPos**, его состояние будет SQL_ROW_SUCCESS.<br /><br /> Это значение не задано **SQLFetch** или **SQLFetchScroll**.|  
|SQL_ROW_NOROW|Набор строк overlapped конец результирующего набора, и строка не был возвращен, что, предоставивших к данному элементу массив статусов строк.|
