---
title: Сохранение наборов записей отфильтрованные, так и иерархическим | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: da1d0d1538d86738e576b01aa176ffde206a9cdb
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272193"
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Сохранение отфильтрованы и иерархические наборы записей
Если [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство действует для **записей**, сохраняются только те строки, которые доступны в фильтре. Если **набора записей** имеет иерархическую структуру, текущий дочерний элемент **набора записей** и его дочерние элементы сохраняются, включая родительскую **набора записей**. Если **Сохранить** метод дочернего **записей** является именем, дочерним элементом, а также все его дочерние элементы сохраняются, но не является родительским. Дополнительные сведения об иерархической **наборы записей**, в разделе [формирование](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Существуют некоторые ограничения при сохранении иерархические **наборы записей** (данные фигуры) в формате XML. Дополнительные сведения см. в разделе [Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md).
