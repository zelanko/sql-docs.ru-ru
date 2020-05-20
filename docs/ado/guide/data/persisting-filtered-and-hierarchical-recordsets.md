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
author: rothja
ms.author: jroth
ms.openlocfilehash: 5fa3fdd55fb78f16629907c174b08aab64ceb86e
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763115"
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Сохранение отфильтрованных и иерархических наборов записей
Если свойство [фильтра](../../../ado/reference/ado-api/filter-property.md) действует для **набора записей**, сохраняются только те строки, которые доступны в фильтре. Если **набор записей** является иерархическим, текущий дочерний **набор записей** и его дочерние элементы сохраняются, включая родительский **набор записей**. Если вызывается метод **Save** дочернего **набора записей** , дочерний элемент и все его дочерние элементы сохраняются, но родительский элемент не является. Дополнительные сведения о иерархических **наборах записей**см. в разделе [формирование данных](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Некоторые ограничения применяются при сохранении иерархических **наборов записей** (фигур данных) в формате XML. Дополнительные сведения см. [в разделе Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md).
