---
title: "Сохранение наборов записей отфильтрованные, так и иерархическим | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filtered Recordset persistence [ADO]
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: d01aeb4d-4e43-450b-b3f2-0c27eaaf9f86
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6d7ad27e3694b7a92e560170e699f62d76d5e6b0
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Сохранение отфильтрованы и иерархические наборы записей
Если [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство действует для **записей**, сохраняются только те строки, которые доступны в фильтре. Если **набора записей** имеет иерархическую структуру, текущий дочерний элемент **набора записей** и его дочерние элементы сохраняются, включая родительскую **набора записей**. Если **Сохранить** метод дочернего **записей** является именем, дочерним элементом, а также все его дочерние элементы сохраняются, но не является родительским. Дополнительные сведения об иерархической **наборы записей**, в разделе [формирование](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Существуют некоторые ограничения при сохранении иерархические **наборы записей** (данные фигуры) в формате XML. Дополнительные сведения см. в разделе [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md).
