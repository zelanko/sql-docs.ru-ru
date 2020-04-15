---
title: Ряд статуса Array (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 60dead23fe0051c05698e094f37ddad96b2b337d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304295"
---
# <a name="row-status-array"></a>Массив статусов строк
В дополнение к данным, **S'LFetch** и **S'LFetchScroll** могут вернуть массив, который дает статус каждой строки в строке. Этот массив указан через атрибут SQL_ATTR_ROW_STATUS_PTR оператора. Этот массив выделяется приложением и должен иметь столько элементов, сколько указано в атрибуте SQL_ATTR_ROW_ARRAY_SIZE оператора. Значения в массиве устанавливаются **S'LBulkOperations,** **S'LFetch,** **S'LFetchScroll**и **S'LSetPos.** Значения описывают состояние строки и изменился ли этот статус с момента его последнего извлечения.  
  
|Значение массива строки|Описание|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|Строка была успешно извлечена и не изменилась с момента последнего извлечения.|  
|SQL_ROW_SUCCESS_WITH_INFO|Строка была успешно извлечена и не изменилась с момента последнего извлечения. Тем не менее, предупреждение было возвращено о строке.|  
|SQL_ROW_ERROR|Ошибка произошла при извлечении строки.|  
|SQL_ROW_UPDATED|Строка была успешно извлечена и была обновлена с момента последнего извлечения. Если строка снова извлечена или обновлена **S'LSetPos,** ее статус изменен на новый статус.<br /><br /> Некоторые драйверы не могут обнаружить изменения в данных и поэтому не могут вернуть это значение. Чтобы определить, может ли драйвер обнаруживать обновления для восстановленных строк, приложение вызывает **s'LGetInfo** с опцией SQL_ROW_UPDATES.|  
|SQL_ROW_DELETED|Строка была удалена с момента последнего извлечения.|  
|SQL_ROW_ADDED|Строка была вставлена **с помощью S'LBulkOperations**. Если строка снова извлечена или обновлена **S'LSetPos,** ее статус SQL_ROW_SUCCESS.<br /><br /> Это значение не устанавливается **S'LFetch** или **S'LFetchScroll.**|  
|SQL_ROW_NOROW|Строка перекрывала конец набора результатов, и не было возвращено строки, соответствующей этому элементу массива состояния строки.|
