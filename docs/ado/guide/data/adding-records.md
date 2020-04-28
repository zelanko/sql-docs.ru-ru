---
title: Добавление записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- editing data [ADO], AddNew method
- editing data [ADO], adding data
ms.assetid: dd34669e-6f06-403b-9241-1c85c82aecc2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1f4ec0934fbf75de18f460abae84b8117e99f452
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926267"
---
# <a name="adding-records-to-a-recordset"></a>Добавление записей в набор записей
Используйте метод **AddNew** для создания и инициализации новой записи в существующем **наборе записей**. Можно использовать метод **поддерживает** со значением **курсороптионенум** , равным **ададднев** , чтобы проверить, можно ли добавлять записи в текущий объект **Recordset** .

 После вызова метода **AddNew** новая запись становится текущей и остается текущей после вызова метода **Update** . Если объект **Recordset** не поддерживает закладки, доступ к новой записи после перехода на другую запись может оказаться невозможным. Поэтому, в зависимости от типа курсора, может потребоваться вызвать метод **Requery** , чтобы сделать новую запись доступной.

 При вызове **AddNew** во время редактирования текущей записи или при добавлении новой записи ADO вызывает метод **Update** для сохранения любых изменений, а затем создает новую запись.

 Этот раздел содержит следующие подразделы.

-   [Добавление записей с помощью AddNew](../../../ado/guide/data/adding-records-using-addnew.md)

-   [Добавление нескольких полей](../../../ado/guide/data/adding-multiple-fields.md)

-   [Определение режима изменения](../../../ado/guide/data/determining-edit-mode.md)

-   [Использование AddNew в режиме интерпретации и пакетном режиме](../../../ado/guide/data/using-addnew-in-immediate-and-batch-modes.md)
