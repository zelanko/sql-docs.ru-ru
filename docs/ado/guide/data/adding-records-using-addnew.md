---
title: Добавление записей с помощью AddNew | Документация Майкрософт
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
- editing data [ADO], AddNew method
ms.assetid: cab4adff-f22f-4fb1-9217-f8138c795268
author: rothja
ms.author: jroth
ms.openlocfilehash: abdd3bf7e23c74624a7eaa70c102112593fd3648
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761410"
---
# <a name="adding-records-using-addnew-method"></a>Добавление записей с помощью метода AddNew
Это базовый синтаксис метода **AddNew** :

 *набор записей*. *Списокполей*AddNew, *значения*

 Аргументы *списокполей* и *Values* являются необязательными. *Списокполей* — это либо одно имя, либо массив имен или порядкового номера полей в новой записи.

 Аргумент *Values* — это либо одиночное значение, либо массив значений для полей в новой записи.

 Как правило, если предполагается добавить одну запись, то метод **AddNew** будет вызываться без аргументов. В частности, будет вызван метод **AddNew**; Задайте **значение** каждого поля в новой записи. затем вызовите **Update** или **UpdateBatch**или оба. Можно убедиться, что **набор записей** поддерживает добавление новых записей с помощью свойства **поддерживает** с константой перечисления **ададднев** .

 В следующем коде этот метод используется для добавления нового поставщика в образец **набора записей**. SQL Server автоматически предоставляет значение поля Шипперид. Поэтому код не пытается предоставить значение поля для новых записей.

```
'BeginAddNew1.1
If objRs.Supports(adAddNew) Then
    With objRs
        .AddNew
        .Fields("CompanyName") = "Sample Shipper"
        .Fields("Phone") = "(931) 555-6334"
        .Update
    End With
End If
'EndAddNew1.1
```

## <a name="remarks"></a>Remarks
 Поскольку этот код использует несвязанный **набор записей** с курсором на стороне клиента в пакетном режиме, необходимо повторно подключить **набор записей** к источнику данных с помощью нового объекта **соединения** , прежде чем вызывать метод **UpdateBatch** для публикации изменений в базе данных. Это легко сделать с помощью новой функции **жетневконнектион**.
