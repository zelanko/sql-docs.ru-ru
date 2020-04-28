---
title: Упорядочение иерархических наборов записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset fabrication [ADO]
- hierarchical Recordsets [ADO]
- fabricating hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: a584e642-a4a3-418e-bc20-3aff81a5625a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6fcdb630f2391f685080ac594cfdb537edf626a2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925327"
---
# <a name="fabricating-hierarchical-recordsets"></a>Составление иерархических наборов записей
В следующем примере показано, как создать иерархический набор записей без базового источника данных, используя грамматику формирования данных для определения столбцов для родительских, дочерних и внучатый **наборов записей**.  
  
 Для формирования иерархического **набора записей**необходимо указать [службу формирования данных Майкрософт для OLE DB (поставщик служб ADO)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (мсдаташапе), а в параметре строки подключения метода [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) объекта [Connection](../../../ado/reference/ado-api/connection-object-ado.md) можно указать значение None для поставщика данных. Дополнительные сведения см. в разделе [необходимые поставщики для формирования данных](../../../ado/guide/data/required-providers-for-data-shaping.md).  
  
```  
Dim cn As New ADODB.Connection  
Dim rsCustomers As New ADODB.Recordset  
  
cn.Open "Provider=MSDataShape;Data Provider=NONE;"  
  
strShape = _  
"SHAPE APPEND NEW adInteger AS CustID," & _  
            " NEW adChar(25) AS FirstName," & _  
            " NEW adChar(25) AS LastName," & _  
            " NEW adChar(12) AS SSN," & _  
            " NEW adChar(50) AS Address," & _  
         " ((SHAPE APPEND NEW adChar(80) AS VIN_NO," & _  
                        " NEW adInteger AS CustID," & _  
                        " NEW adChar(20) AS BodyColor, " & _  
                     " ((SHAPE APPEND NEW adChar(80) AS VIN_NO," & _  
                                    " NEW adChar(20) AS Make, " & _  
                                    " NEW adChar(20) AS Model," & _  
                                    " NEW adChar(4) AS Year) " & _  
                        " AS VINS RELATE VIN_NO TO VIN_NO))" & _  
            " AS Vehicles RELATE CustID TO CustID) "  
  
rsCustomers.Open strShape, cn, adOpenStatic, adLockOptimistic, -1  
```  
  
 Как только **набор записей** будет создан, он может быть заполнен, обработан или сохранен в файле.  
  
## <a name="see-also"></a>См. также:  
 [Доступ к строкам в иерархическом наборе записей](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Грамматика формальной фигуры](../../../ado/guide/data/formal-shape-grammar.md)   
 [Необходимые поставщики для формирования данных](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Предложение APPEND для фигур](../../../ado/guide/data/shape-append-clause.md)   
 [Общие сведения о командах формирования данных](../../../ado/guide/data/shape-commands-in-general.md)
