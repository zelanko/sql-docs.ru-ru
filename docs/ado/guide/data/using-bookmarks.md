---
title: Использование закладок | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- bookmarks [ADO]
- Recordset object [ADO]
ms.assetid: cca244e6-84f8-4394-bca9-f7a819b8f4df
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a083f9d411474769335fdfae32bd59dfe455a9f8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47660642"
---
# <a name="using-bookmarks"></a>Использование закладок
Часто бывает полезно для возврата непосредственно к конкретной записи, после, перемещаются **записей** без необходимости прокрутки всех записей и сравнение значений. Например, при попытке найти записи с помощью **найти** метод, но поиск не возвращает записи, вы автоматически оказываетесь на любом конце **записей**. Если поставщик поддерживает их, чтобы отметить место, прежде чем использовать может использоваться закладки **найти** метод, поэтому можно вернуться в папку. Закладка представляет **Variant** введите значение, которое однозначно определяет запись в **записей** объекта.  
  
 Можно также использовать массив вариантов закладок с **фильтр набора записей** способ фильтрации на выбранный набор записей. Дополнительные сведения об этом методе см. в разделе Фильтрация результатов в разделе [работа с наборами записей](../../../ado/guide/data/working-with-recordsets.md)далее в этом разделе.  
  
 Можно использовать **закладки** для получения закладку для записи, и задать текущую запись в **записей** объект для записи, определяемой закладкой допустимым. В следующем коде используется **закладки** свойство, чтобы установить закладку, а затем вернитесь к отмеченному закладкой записи после переноса другие записи. Чтобы определить, если ваш **набор записей** поддерживает закладки, используйте **поддерживает** метод.  
  
```  
'BeginBookmarkEg  
Dim varBookmark As Variant  
Dim blnCanBkmrk As Boolean  
  
objRs.Open strSQL, strConnStr, adOpenStatic, adLockOptimistic, adCmdText  
  
If objRs.RecordCount > 4 Then  
    objRs.Move 4                       ' move to the fifth record  
    blnCanBkmrk = objRs.Supports(adBookmark)  
    If blnCanBkmrk = True Then  
        varBookmark = objRs.Bookmark   ' record the bookmark  
        objRs.MoveLast                 ' move to a different record  
        objRs.Bookmark = varBookmark   ' return to the bookmarked (sixth) record  
    End If  
End If  
'EndBookmarkEg  
```  
  
 [Поддерживает](../../../ado/reference/ado-api/supports-method.md) метод рассматривается более подробно позже.  
  
 За исключением случая клонированный **наборы записей**, закладки уникальны для **записей** в которой они были созданы, даже если использовать ту же команду. Это означает, что нельзя использовать **закладки** получения **набор записей** для перемещения к одной записи за секунду **набор записей** открыт с той же команды.
