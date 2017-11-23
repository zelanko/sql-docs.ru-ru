---
title: "С помощью закладок | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bookmarks [ADO]
- Recordset object [ADO]
ms.assetid: cca244e6-84f8-4394-bca9-f7a819b8f4df
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a1cfde267a31b3e11f1c869ac96b652b9db5af16
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="using-bookmarks"></a>С помощью закладок
Часто полезно для возврата непосредственно на определенную запись после перемещаться **записей** без необходимости прокрутки всех записей и сравнения значений. Например, при попытке выполнить поиск записи с помощью **найти** поиска, но метод не возвращает записи, вы автоматически оказываетесь на любом конце **записей**. Если поставщик поддерживает их, чтобы отметить место перед использованием может использоваться закладки **найти** метод, поэтому можно вернуться к папке. Закладка представляет **Variant** введите значение, которое однозначно определяет запись в **записей** объекта.  
  
 Можно также использовать массив вариантов закладок с **фильтра набора записей** метода для фильтрации по выбранного набора записей. Дополнительные сведения об этом методе см. в разделе Фильтрация результатов в разделе [работа с наборами записей](../../../ado/guide/data/working-with-recordsets.md)далее в этом разделе.  
  
 Можно использовать **закладки** для получения закладку для записи, и использовать текущую запись **записей** объект для записи, определяемый допустимую закладку. В следующем коде используется **закладки** свойство установить закладку, а затем вернитесь к закладкой записи после переноса другие записи. Чтобы определить, если ваш **записей** поддерживает закладки, используйте **поддерживает** метод.  
  
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
  
 [Поддерживает](../../../ado/reference/ado-api/supports-method.md) метода является более подробно описаны ниже.  
  
 За исключением случая клонированного **наборы записей**, закладки являются уникальными для **записей** , в котором они были созданы, даже при использовании той же команде. Это означает, что нельзя использовать **закладки** получения **набора записей** для перемещения в той же записи в секунду **набора записей** открыт с помощью одной команды.
