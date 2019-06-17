---
title: Составление иерархических наборов записей | Документация Майкрософт
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
manager: jroth
ms.openlocfilehash: a5dc84c5bacca8951576e572b90fa28a8408e48d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700723"
---
# <a name="fabricating-hierarchical-recordsets"></a>Составление иерархических наборов записей
Приведенный ниже показано, как для создания иерархических наборах записей без базового источника данных с помощью формирования Грамматика для определения столбцов для родительских, дочерних и внучатый данных **наборы записей**.  
  
 При изготовлении иерархической **записей**, необходимо указать [службы Microsoft Data Shaping Service для OLE DB (ADO поставщиком услуг)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (MSDataShape), и можно указать значение NONE в поставщик данных параметр строки подключения [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md) метод [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта. Дополнительные сведения см. в разделе [необходимые поставщики для формирования данных](../../../ado/guide/data/required-providers-for-data-shaping.md).  
  
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
  
 Сразу же **записей** были подделаны, его могут заполняться, управлять или сохраняется в файл.  
  
## <a name="see-also"></a>См. также  
 [Доступ к строкам в иерархических наборах записей](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Грамматика формального формирования данных](../../../ado/guide/data/formal-shape-grammar.md)   
 [Обязательные поставщики для формирования данных](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Предложение APPEND для формирования](../../../ado/guide/data/shape-append-clause.md)   
 [Общие сведения о командах формирования данных](../../../ado/guide/data/shape-commands-in-general.md)
