---
title: Добавление нескольких полей | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, adding data
- editing data [ADO], adding multiple fields
- editing data [ADO], AddNew method
ms.assetid: f3648ef4-9f36-4991-a868-83a617389844
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23d13c750b3140090fa66efaec8aa57e2afe77db
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271183"
---
# <a name="adding-multiple-fields-and-values"></a>Добавление нескольких полей и значений
В некоторых случаях может быть более эффективно передавать массив полей и их соответствующие значения для **AddNew** метод, а не параметр **значение** несколько раз для каждого нового поля. Если *списка полей* является массивом, *значения* также должен быть массивом с тем же число членов; в противном случае возникает ошибка. Порядок полей имен должен соответствовать порядку значений полей в каждом массиве. Приведенный ниже код передает массив полей и массив значений для **AddNew** метод.

```
'BeginAddNew2
    Dim avarFldNames As Variant
    Dim avarFldValues As Variant

    avarFldNames = Array("CompanyName", "Phone")
    avarFldValues = Array("Sample Shipper 2", "(931) 555-6334")

    If objRs1.Supports(adAddNew) Then
        objRs1.AddNew avarFldNames, avarFldValues
    End If

    'Re-establish a Connection and update
    Set objRs1.ActiveConnection = GetNewConnection
    objRs1.UpdateBatch
'EndAddNew2
```
