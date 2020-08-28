---
description: Сохранение отфильтрованных и иерархических наборов записей
title: Сохранение отфильтрованных и иерархических наборов записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: fc18622d3fda977d4a19d9946430c9e1cd0b2444
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980095"
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Сохранение отфильтрованных и иерархических наборов записей
Если свойство [фильтра](../../../ado/reference/ado-api/filter-property.md) действует для **набора записей**, сохраняются только те строки, которые доступны в фильтре. Если **набор записей** является иерархическим, текущий дочерний **набор записей** и его дочерние элементы сохраняются, включая родительский **набор записей**. Если вызывается метод **Save** дочернего **набора записей** , дочерний элемент и все его дочерние элементы сохраняются, но родительский элемент не является. Дополнительные сведения о иерархических **наборах записей**см. в разделе [формирование данных](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Некоторые ограничения применяются при сохранении иерархических **наборов записей** (фигур данных) в формате XML. Дополнительные сведения см. [в разделе Сохранение записей в формате XML](../../../ado/guide/data/persisting-records-in-xml-format.md).
