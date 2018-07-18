---
title: Необходимые поставщики данных формировать | Документы Microsoft
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
- providers [ADO], data shaping
- data shaping [ADO], providers required
ms.assetid: d49d48d2-ac2d-4c11-895c-5a149b444620
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d53ea24bdd91950754de626683f013d1cb7301a2
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272903"
---
# <a name="required-providers-for-data-shaping"></a>Для формирования данных службы необходимых поставщиков
Формирование данных обычно требует двух поставщиков. Поставщик услуг [службы Data Shaping Service для OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md), предоставляющий формирования функциональные возможности и поставщика данных, например поставщик OLE DB для SQL Server данных, передает строки данных для заполнения формы [набора записей ](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 В качестве значения можно указать имя поставщика услуг (MSDataShape) [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойства или ключевое слово строки подключения «поставщик = MSDataShape;».  
  
 Имя поставщика данных можно указать в качестве значения **поставщик данных** динамические свойства, которое добавляется к **подключения** объекта [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции с помощью службы Data Shaping Service для OLE DB или ключевое слово строки соединения «**поставщик данных = *** поставщика*».  
  
 Поставщик данных не является обязательным, если **записей** не заполняется (например, как создано **записей** где столбцы создаются с помощью ключевого слова NEW). В этом случае указать "**поставщик данных =** none;».  
  
## <a name="example"></a>Пример  
  
```  
Dim cnn As New ADODB.Connection  
cnn.Provider = "MSDataShape"  
cnn.Open "Data Provider=SQLOLEDB;Integrated Security=SSPI;Database=Northwind"  
```  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)   
 [Грамматика формальных фигуры](../../../ado/guide/data/formal-shape-grammar.md)   
 [Общие сведения о командах формирования данных](../../../ado/guide/data/shape-commands-in-general.md)
