---
description: Добавление записей в набор записей
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e38dbfbf8b0a92a0d1a8a2eff1b8b8d4d5374057
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806708"
---
# <a name="adding-records-to-a-recordset"></a>Добавление записей в набор записей
Используйте метод **AddNew** для создания и инициализации новой записи в существующем **наборе записей**. Можно использовать метод **поддерживает** со значением **курсороптионенум** , равным **ададднев** , чтобы проверить, можно ли добавлять записи в текущий объект **Recordset** .

 После вызова метода **AddNew** новая запись становится текущей и остается текущей после вызова метода **Update** . Если объект **Recordset** не поддерживает закладки, доступ к новой записи после перехода на другую запись может оказаться невозможным. Поэтому, в зависимости от типа курсора, может потребоваться вызвать метод **Requery** , чтобы сделать новую запись доступной.

 При вызове **AddNew** во время редактирования текущей записи или при добавлении новой записи ADO вызывает метод **Update** для сохранения любых изменений, а затем создает новую запись.

 Этот раздел содержит следующие подразделы.

-   [Добавление записей с помощью AddNew](./adding-records-using-addnew.md)

-   [Добавление нескольких полей](./adding-multiple-fields.md)

-   [Определение режима изменения](./determining-edit-mode.md)

-   [Использование AddNew в режиме интерпретации и пакетном режиме](./using-addnew-in-immediate-and-batch-modes.md)