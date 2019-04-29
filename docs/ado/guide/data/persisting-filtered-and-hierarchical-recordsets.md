---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 53e28fdfbc49b53c4927bbcc0d5a6a8dc44b3d6d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913319"
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Сохранение отфильтрованных и иерархических наборов записей
Если [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство распространяется на **записей**, сохраняются только те строки, которые доступны в разделе фильтра. Если **записей** является иерархической, текущий дочерний элемент **записей** и его дочерние элементы сохраняются, включая родительский элемент **набор записей**. Если **Сохранить** метод дочернего **записей** — вызывается, дочерние и все его дочерние элементы сохраняются, но не является родительским. Дополнительные сведения об иерархической **наборы записей**, см. в разделе [формирования данных](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Некоторые ограничения применяются при сохранении иерархические **наборы записей** (данные фигуры) в формате XML. Дополнительные сведения см. в разделе [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md).
