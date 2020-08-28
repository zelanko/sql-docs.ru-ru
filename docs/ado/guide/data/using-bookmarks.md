---
description: Использование закладок
title: Использование закладок | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- bookmarks [ADO]
- Recordset object [ADO]
ms.assetid: cca244e6-84f8-4394-bca9-f7a819b8f4df
author: rothja
ms.author: jroth
ms.openlocfilehash: 34fc17275609dbf08ffa02a1bc89902c904cac85
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979044"
---
# <a name="using-bookmarks"></a>Использование закладок
Часто бывает полезно возвращаться к определенной записи после перемещения по **набору записей** без необходимости прокручивать каждую запись и сравнивать значения. Например, при попытке поиска записи с помощью метода **Find** , но при поиске не возвращаются записи, вы автоматически Помещаетесь в любой конец **набора записей**. Если поставщик поддерживает их, можно использовать закладки, чтобы отметить место до использования метода **Find** , чтобы вы могли вернуться к Вашему расположению. Закладка — это значение типа **Variant** , однозначно идентифицирующее запись в объекте **набора записей** .  
  
 Можно также использовать массив вариантов закладок с методом **фильтрации набора записей** для фильтрации по выбранному набору записей. Дополнительные сведения об этом методе см. в разделе Фильтрация результатов в статье [Работа с наборами записей](../../../ado/guide/data/working-with-recordsets.md)далее в этом разделе.  
  
 Можно использовать свойство **Bookmark** , чтобы получить закладку для записи, или установить текущую запись в объекте **набора записей** на запись, определяемую допустимой закладкой. В следующем коде свойство **Bookmark** используется для задания закладки, а затем возвращается к записи с закладкой после перехода к другим записям. Чтобы определить, поддерживает ли **набор записей** закладки, используйте метод **поддерживает** .  
  
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
  
 Метод [поддержки](../../../ado/reference/ado-api/supports-method.md) более подробно рассматривается далее.  
  
 За исключением случаев клонированных **наборов записей**, закладки уникальны для **набора записей** , в котором они были созданы, даже если используется та же команда. Это означает, что нельзя использовать **закладку** , полученную из одного **набора записей** , чтобы перейти к той же записи во втором **наборе записей** , открытом с помощью той же команды.
