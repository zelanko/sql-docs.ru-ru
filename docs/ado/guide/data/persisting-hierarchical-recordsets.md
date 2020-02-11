---
title: Сохранение иерархических наборов записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchical Recordsets [ADO], persisting
- persisting hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: 43798bb5-98a6-4ad6-9bf8-78154b3a1827
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 34649bba37f922e7597bf09870e3e9d3bcf522dc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924628"
---
# <a name="persisting-hierarchical-recordsets"></a>Сохранение иерархических наборов записей
Можно сохранить иерархический **набор записей** в файл в формате АДТГ или XML, вызвав метод [Save](../../../ado/reference/ado-api/save-method.md) . Однако при сохранении иерархических **наборов записей**в формате XML применяются два ограничения: невозможно сохранить в XML, если иерархический **набор** записей содержит ожидающие обновления, и нельзя сохранить параметризованный иерархический **набор записей**.  
  
 Дополнительные сведения о поставщике формирования данных см. в статьях [Служба формирования данных Майкрософт для OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (ADO) и [Общие сведения о службе формирования данных для OLE DB](https://msdn.microsoft.com/9f51e471-8e85-448e-9fb8-b64bbf767bf3).  
  
## <a name="see-also"></a>См. также:  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)   
 [Грамматика формальной фигуры](../../../ado/guide/data/formal-shape-grammar.md)   
 [Общие сведения о командах формирования данных](../../../ado/guide/data/shape-commands-in-general.md)
