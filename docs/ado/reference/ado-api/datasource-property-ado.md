---
title: "Свойства источника данных (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset20::DataSource
helpviewer_keywords:
- DataSource property [ADO]
ms.assetid: 300a702a-3544-48c5-b759-83b511fe97e0
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b6003f19993835b937828948658e29cfb271cada
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="datasource-property-ado"></a>Свойства источника данных (ADO)
Указывает объект, содержащий данные для представления в виде [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="remarks"></a>Замечания  
 Это свойство используется для создания элементов управления с привязкой к данным со средой данных. Среде данных поддерживает наборами данных (источники данных), содержащий именованные объекты (элементы данных), будут представлены в виде **записей** объекта*.*  
  
 [DataMember](../../../ado/reference/ado-api/datamember-property.md) и **DataSource** свойства должен использоваться совместно.  
  
 Ссылка на объект должен реализовать **IDataSource** интерфейса и должен содержать **IRowset** интерфейса.  
  
## <a name="usage"></a>Использование  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to.  
Set rs.DataSource = myDE      'Name of the object containing an IRowset.  
```  
  
## <a name="applies-to"></a>Объект применения  
 [Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойства DataMember](../../../ado/reference/ado-api/datamember-property.md)

