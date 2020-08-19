---
description: Сохранение отфильтрованных и иерархических наборов записей
title: Сохранение отфильтрованных и иерархических наборов записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- filtered Recordset persistence [ADO]
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: d01aeb4d-4e43-450b-b3f2-0c27eaaf9f86
author: rothja
ms.author: jroth
ms.openlocfilehash: a69b491f4bb5834331b9cfa582b6f72d248ba317
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453066"
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Сохранение отфильтрованных и иерархических наборов записей
Если свойство [фильтра](../../../ado/reference/ado-api/filter-property.md) действует для **набора записей**, сохраняются только те строки, которые доступны в фильтре. Если **набор записей** является иерархическим, текущий дочерний **набор записей** и его дочерние элементы сохраняются, включая родительский **набор записей**. Если вызывается метод **Save** дочернего **набора записей** , дочерний элемент и все его дочерние элементы сохраняются, но родительский элемент не является. Дополнительные сведения о иерархических **наборах записей**см. в разделе [формирование данных](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Некоторые ограничения применяются при сохранении иерархических **наборов записей** (фигур данных) в формате XML. Дополнительные сведения см. [в разделе Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md).
