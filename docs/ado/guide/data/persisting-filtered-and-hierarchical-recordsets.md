---
title: Сохранение наборов записей отфильтрованные, так и иерархическим | Документы Microsoft
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
- filtered Recordset persistence [ADO]
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: d01aeb4d-4e43-450b-b3f2-0c27eaaf9f86
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d945999ef7feb34ebe7de3b945868bc35c154589
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Сохранение отфильтрованы и иерархические наборы записей
Если [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство действует для **записей**, сохраняются только те строки, которые доступны в фильтре. Если **набора записей** имеет иерархическую структуру, текущий дочерний элемент **набора записей** и его дочерние элементы сохраняются, включая родительскую **набора записей**. Если **Сохранить** метод дочернего **записей** является именем, дочерним элементом, а также все его дочерние элементы сохраняются, но не является родительским. Дополнительные сведения об иерархической **наборы записей**, в разделе [формирование](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Существуют некоторые ограничения при сохранении иерархические **наборы записей** (данные фигуры) в формате XML. Дополнительные сведения см. в разделе [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md).
