---
title: Свойство DataSource (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::DataSource
helpviewer_keywords:
- DataSource property [ADO]
ms.assetid: 300a702a-3544-48c5-b759-83b511fe97e0
author: rothja
ms.author: jroth
ms.openlocfilehash: cbaff4a2bf03e524018c0c8d1b163925aa40b3ea
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763475"
---
# <a name="datasource-property-ado"></a>Свойство DataSource (ADO)
Указывает объект, содержащий данные, которые должны быть представлены как объект [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
## <a name="remarks"></a>Remarks  
 Это свойство используется для создания элементов управления с привязкой к данным в среде данных. Среда данных хранит коллекции данных (источники данных), содержащие именованные объекты (элементы данных), которые будут представлены в виде объекта **набора записей** .  
  
 Свойства [DataMember](../../../ado/reference/ado-api/datamember-property.md) и **DataSource** должны использоваться совместно.  
  
 Объект, на который указывает ссылка, должен реализовать интерфейс **IDataSource** и должен содержать интерфейс **IRowset** .  
  
## <a name="usage"></a>Использование  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to.  
Set rs.DataSource = myDE      'Name of the object containing an IRowset.  
```  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство DataMember](../../../ado/reference/ado-api/datamember-property.md)
