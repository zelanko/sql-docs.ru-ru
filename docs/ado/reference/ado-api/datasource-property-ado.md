---
description: Свойство DataSource (ADO)
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
ms.openlocfilehash: 8b85f163ddb3f1fc31116966127bc01efa17a262
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444226"
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
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство DataMember](../../../ado/reference/ado-api/datamember-property.md)
