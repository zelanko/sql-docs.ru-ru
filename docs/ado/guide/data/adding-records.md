---
title: Добавление записей | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- editing data [ADO], AddNew method
- editing data [ADO], adding data
ms.assetid: dd34669e-6f06-403b-9241-1c85c82aecc2
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aeaf7182685ff0b7621d208ba684976da7bf07bd
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="adding-records-to-a-recordset"></a>Добавление записей в наборе записей
Используйте **AddNew** метод для создания и инициализации новой записи в существующем **записей**. Можно использовать **поддерживает** метод с **CursorOptionEnum** значение **adAddNew** Чтобы проверить возможность добавления записи в текущий **наборазаписей** объекта.

 После вызова метода **AddNew** метод, новая запись становится текущей записью и остаются актуальными после вызова метода **обновление** метод. Если **записей** объект не поддерживает закладки, не может иметь доступ к новой записи, то при перемещении в другую запись. Таким образом, в зависимости от типа курсора, может потребоваться вызвать **Requery** метод для предоставления специальных возможностей новой записи.

 При вызове метода **AddNew** при изменении текущей записи или при добавлении новой записи ADO вызывает **обновление** метод, чтобы сохранить любые изменения, а затем создает новую запись.

 Этот раздел содержит следующие подразделы.

-   [Добавление записей с помощью AddNew](../../../ado/guide/data/adding-records-using-addnew.md)

-   [Добавление нескольких полей](../../../ado/guide/data/adding-multiple-fields.md)

-   [Определение режима изменения](../../../ado/guide/data/determining-edit-mode.md)

-   [Использование AddNew в режиме интерпретации и пакетном режиме](../../../ado/guide/data/using-addnew-in-immediate-and-batch-modes.md)
