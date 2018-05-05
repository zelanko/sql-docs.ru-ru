---
title: Фильтрация для обновления записей | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- filtering for updated records [ADO]
ms.assetid: 4a798921-d7bb-47c9-a252-550fd9463ec9
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b8ee03c015f7fa63980f549c8d9e7bef2df51426
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="filtering-for-updated-records"></a>Фильтрация для обновленных записей
Перед вызовом метода UpdateBatch, можно использовать свойство фильтра набора записей для просмотра только те записи, которые были изменены с момента открытия набора записей или последнего вызова UpdateBatch. Чтобы сделать это, задайте в фильтр adFilterPendingRecords, чтобы определить, сколько записей будет обновлено, как показано в примере кода в следующем разделе.  
  
## <a name="remarks"></a>Замечания  
 В этом примере в предыдущем примере UpdateBatch расширяет путем фильтрации набора записей, только в том случае, перед вызовом UpdateBatch, показывающая пользователя приведет к изменению записей и позволяя ему отменить обновление (с помощью метода CancelBatch).  
  
```  
'BeginFilterPend  
    '...  
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText  
  
    ' Change value of Phone field for first record in Recordset, saving value  
    ' for later restoration.  
    intId = objRs1("ShipperId")  
    sPhone = objRs1("Phone")  
  
    objRs1("Phone") = "(111) 555-1111"  
  
    'Add two new records  
    For i = 0 To 1  
        objRs1.AddNew  
        objRs1(1) = "New Shipper #" & CStr((i + 1))  
        objRs1(2) = "(nnn) 555-" & i & i & i & i  
    Next i  
  
    objRs1.Filter = adFilterPendingRecords  
  
    MsgBox "There are " & objRs1.RecordCount & " records pending.", _  
            , "Filter Pending"  
  
    ' Cancel the updates  
    objRs1.CancelBatch  
'EndFilterPend  
```  
  
## <a name="see-also"></a>См. также  
 [Пакетный режим](../../../ado/guide/data/batch-mode.md)
