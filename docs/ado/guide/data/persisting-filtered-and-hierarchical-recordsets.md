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
manager: jroth
ms.openlocfilehash: cbd237580dc8c56284552e6fe2fb00e469832c5b
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66702047"
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Сохранение отфильтрованных и иерархических наборов записей
Если [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство распространяется на **записей**, сохраняются только те строки, которые доступны в разделе фильтра. Если **записей** является иерархической, текущий дочерний элемент **записей** и его дочерние элементы сохраняются, включая родительский элемент **набор записей**. Если **Сохранить** метод дочернего **записей** — вызывается, дочерние и все его дочерние элементы сохраняются, но не является родительским. Дополнительные сведения об иерархической **наборы записей**, см. в разделе [формирования данных](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Некоторые ограничения применяются при сохранении иерархические **наборы записей** (данные фигуры) в формате XML. Дополнительные сведения см. в разделе [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md).
