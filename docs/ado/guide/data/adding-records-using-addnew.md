---
title: Добавление нескольких записей с помощью команды AddNew | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 68b1a34a5d23d9aab32b6216eda3b3ef8f977e79
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63010732"
---
# <a name="adding-records-using-addnew-method"></a>Добавление записей с помощью метода AddNew
Это базовый синтаксис **AddNew** метод:

 *набор записей*. AddNew *"списокполей"*, *значения*

 *"Списокполей"* и *значения* аргументы необязательны. *"Списокполей"* одно имя или массив имен или порядковые номера поля в новой записи.

 *Значения* аргументом является одиночное значение или массив значений для полей новой записи.

 Как правило, если вы намереваетесь добавить только одну запись, будет вызывать **AddNew** метода без аргументов. В частности, вы будете вызывать **AddNew**; set **значение** каждого поля в новой записи; а затем вызвать **обновление** или **UpdateBatch**, или оба. Можно убедитесь, что ваш **записей** поддерживает добавление новых записей с помощью **поддерживает** свойство с **adAddNew** константы перечислимого типа.

 Следующий код использует эту методику для добавления нового поставщика в пример **записей**. SQL Server предоставляет значение поля ShipperID автоматически. Таким образом код не пытается предоставить значение поля для новых записей.

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

## <a name="remarks"></a>Примечания
 Так как этот код использует отключенного **записей** с клиентский курсор в пакетном режиме, необходимо повторно подключить **записей** к источнику данных с новым **подключения** объект перед вызовом **UpdateBatch** метод, чтобы учесть изменения в базу данных. Это легко сделать с помощью новой функции **GetNewConnection**.
