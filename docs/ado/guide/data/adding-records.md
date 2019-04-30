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
manager: craigg
ms.openlocfilehash: a17e09df7c7235e1361aae79bd89152c290b1bdb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63294397"
---
# <a name="adding-records-to-a-recordset"></a>Добавление записей в набор записей
Используйте **AddNew** метод для создания и инициализации новой записи в существующем **записей**. Можно использовать **поддерживает** метод с **CursorOptionEnum** значение **adAddNew** Чтобы проверить возможность добавления записи в текущий **наборазаписей** объекта.

 После вызова метода **AddNew** метод, новая запись становится текущей записью и остаются актуальными, после вызова метода **обновления** метод. Если **записей** объект не поддерживает закладки, не может быть возможность доступа к новой записи, то при перемещении на другую запись. Таким образом, в зависимости от типа курсора, может потребоваться вызвать **Requery** метод, чтобы сделать доступным новой записи.

 При вызове метода **AddNew** во время редактирования текущей записи или при добавлении новой записи ADO вызывает **обновления** метод, чтобы сохранить любые изменения, а затем создает новую запись.

 Этот раздел содержит следующие подразделы.

-   [Добавление записей с помощью AddNew](../../../ado/guide/data/adding-records-using-addnew.md)

-   [Добавление нескольких полей](../../../ado/guide/data/adding-multiple-fields.md)

-   [Определение режима изменения](../../../ado/guide/data/determining-edit-mode.md)

-   [Использование AddNew в режиме интерпретации и пакетном режиме](../../../ado/guide/data/using-addnew-in-immediate-and-batch-modes.md)
