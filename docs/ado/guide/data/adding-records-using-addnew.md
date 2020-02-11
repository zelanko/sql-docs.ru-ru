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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 36f6bad9a8f0d74a81d02ce64c78d7a91ddc0fa8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926282"
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
