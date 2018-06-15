---
title: Сохранение иерархические наборы записей | Документы Microsoft
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
- hierarchical Recordsets [ADO], persisting
- persisting hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: 43798bb5-98a6-4ad6-9bf8-78154b3a1827
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ef907391ad15cb5dd4d58efb6268a0b1688274fb
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272523"
---
# <a name="persisting-hierarchical-recordsets"></a>Сохранение иерархические наборы записей
Вы можете сохранить иерархической **записей** в файл в формате XML или ADTG путем вызова [Сохранить](../../../ado/reference/ado-api/save-method.md) метод. Однако два ограничения применяются при сохранении иерархические **набора записей**s в формате XML: не удается сохранить в формате XML, если иерархическое **записей** содержит отложенные обновления, и не удается сохранить параметризованную иерархические **записей**.  
  
 Дополнительные сведения о поставщике формирования данных см. в разделе [службы Microsoft Data Shaping Service для OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (ADO) и [Обзор службы Data Shaping Service для OLE DB](http://msdn.microsoft.com/en-us/9f51e471-8e85-448e-9fb8-b64bbf767bf3).  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)   
 [Грамматика формальных фигуры](../../../ado/guide/data/formal-shape-grammar.md)   
 [Общие сведения о командах формирования данных](../../../ado/guide/data/shape-commands-in-general.md)
