---
description: Добавление нескольких полей и значений
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e2543741749c1521526aea18bc4600168559eb45
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453896"
---
# <a name="adding-multiple-fields-and-values"></a>Добавление нескольких полей и значений
Иногда может оказаться более эффективным передать массив полей и их соответствующие значения в метод **AddNew** , а не задавать **значение** несколько раз для каждого нового поля. Если *списокполей* является массивом, то *значения* также должны быть массивом с одинаковым числом членов. в противном случае возникает ошибка. Порядок имен полей должен совпадать с порядком значений полей в каждом массиве. Следующий код передает массив полей и массив значений в метод **AddNew** .

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
