---
title: "Иерархические наборы записей fabricating | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Recordset fabrication [ADO]
- hierarchical Recordsets [ADO]
- fabricating hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: a584e642-a4a3-418e-bc20-3aff81a5625a
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f8b01b8cd08c46f641fbd713f4acbdeca53db5c6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
  
## <a name="see-also"></a>См. также:  
 [Доступ к строк в иерархических записей](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Грамматика формальных фигуры](../../../ado/guide/data/formal-shape-grammar.md)   
 [Для формирования данных службы необходимых поставщиков](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Предложение APPEND фигуры](../../../ado/guide/data/shape-append-clause.md)   
 [Команды фигуры в целом](../../../ado/guide/data/shape-commands-in-general.md)

