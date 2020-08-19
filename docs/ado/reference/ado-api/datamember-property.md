---
description: Свойство DataMember
title: Свойство DataMember | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::DataMember
helpviewer_keywords:
- DataMember property
ms.assetid: 2c8fb09e-10ad-49b5-ab41-2603771780d9
author: rothja
ms.author: jroth
ms.openlocfilehash: f698c4a20fb76839460ca0930d45b8d18b2738be
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444236"
---
# <a name="datamember-property"></a>Свойство DataMember
Указывает имя элемента данных, который будет извлечен из [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) , на который ссылается свойство [DataSource](../../../ado/reference/ado-api/datasource-property-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **строковое** значение. Имя без учета регистра.  
  
## <a name="remarks"></a>Remarks  
 Это свойство используется для создания элементов управления с привязкой к данным в среде данных. Среда данных хранит коллекции данных (источники данных), содержащие именованные объекты (элементы данных), которые будут представлены в виде объекта [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
 Свойства **DataMember** и **DataSource** должны использоваться вместе.  
  
 Свойство **DataMember** определяет, какой объект, заданный свойством **DataSource** , будет представлен как объект **набора записей** . Перед установкой этого свойства объект **набора записей** должен быть закрыт. Если свойство **DataMember** не задано перед свойством **DataSource** или если имя **DataMember** не распознается объектом, указанным в свойстве **DataSource** , возникает ошибка.  
  
## <a name="usage"></a>Использование  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to  
Set rs.DataSource = myDE      'Name of the object containing an IRowset  
```  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Свойство DataSource (ADO)](../../../ado/reference/ado-api/datasource-property-ado.md)
