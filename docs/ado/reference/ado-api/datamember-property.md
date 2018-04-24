---
title: Свойства DataMember | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::DataMember
helpviewer_keywords:
- DataMember property
ms.assetid: 2c8fb09e-10ad-49b5-ab41-2603771780d9
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3fc5803fb60ecfeee7f25943fa5b930b79c5fb4c
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="datamember-property"></a>Свойства DataMember
Указывает имя элемента данных, которые будут извлечены из [записей](../../../ado/reference/ado-api/recordset-object-ado.md) ссылается [DataSource](../../../ado/reference/ado-api/datasource-property-ado.md) свойство.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение. Имя не учитывается регистр.  
  
## <a name="remarks"></a>Замечания  
 Это свойство используется для создания элементов управления с привязкой к данным со средой данных. Среде данных поддерживает наборами данных (источники данных), содержащий именованные объекты (элементы данных), будут представлены в виде [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
 **DataMember** и **DataSource** свойства, которые должны использоваться совместно.  
  
 **DataMember** свойство определяет, какой объект, заданный параметром **DataSource** свойства будут представлены в виде **записей** объекта. **Записей** объект должен быть закрыт, пока это свойство задано. Создается сообщение об ошибке, если **DataMember** перед не задано свойство **DataSource** свойства, или, если **DataMember** имя не распознается объекта, указанного в **DataSource** свойство.  
  
## <a name="usage"></a>Использование  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to  
Set rs.DataSource = myDE      'Name of the object containing an IRowset  
```  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Свойство DataSource (ADO)](../../../ado/reference/ado-api/datasource-property-ado.md)
