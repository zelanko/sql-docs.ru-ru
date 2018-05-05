---
title: Иерархические наборы записей fabricating | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset fabrication [ADO]
- hierarchical Recordsets [ADO]
- fabricating hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: a584e642-a4a3-418e-bc20-3aff81a5625a
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e9301ec9204b5d2d6768f7487f279dd5f1eb0f6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="fabricating-hierarchical-recordsets"></a>Fabricating иерархические наборы записей
Приведенный ниже показано, как используется иерархических записей без базового источника данных с помощью формирования Грамматика для определения столбцов для родительских, дочерних и внучатый данных для **наборы записей**.  
  
 При изготовлении иерархической **записей**, необходимо указать [службы Microsoft Data Shaping Service для OLE DB (ADO поставщиком услуг)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (MSDataShape), и указать поставщик данных значение NONE в параметр строки подключения из [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md) метод [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта. Дополнительные сведения см. в разделе [необходимые поставщики данных формировать](../../../ado/guide/data/required-providers-for-data-shaping.md).  
  
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
  
 Как только **записей** был подделаны, его может быть заполнен, управлять или сохранено в файле.  
  
## <a name="see-also"></a>См. также  
 [Доступ к строк в иерархических записей](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Грамматика формальных фигуры](../../../ado/guide/data/formal-shape-grammar.md)   
 [Для формирования данных службы необходимых поставщиков](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Предложение APPEND фигуры](../../../ado/guide/data/shape-append-clause.md)   
 [Общие сведения о командах формирования данных](../../../ado/guide/data/shape-commands-in-general.md)
