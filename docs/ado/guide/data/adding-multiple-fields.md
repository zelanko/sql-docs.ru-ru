---
title: Добавление нескольких полей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, adding data
- editing data [ADO], adding multiple fields
- editing data [ADO], AddNew method
ms.assetid: f3648ef4-9f36-4991-a868-83a617389844
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 90904154f324a86088fac0d637301193464feb2c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701233"
---
# <a name="adding-multiple-fields-and-values"></a>Добавление нескольких полей и значений
В некоторых случаях может оказаться более эффективной, передаваемые в массив полей и их соответствующие значения для **AddNew** метод, а не параметр **значение** несколько раз для каждого нового поля. Если *"списокполей"* является массивом, *значения* также должен быть массивом с тем же число членов; в противном случае возникает ошибка. Порядок имен полей должен соответствовать порядку значений полей в каждом массиве. Следующий код передает массив полей и массив значений для **AddNew** метод.

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
