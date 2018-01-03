---
title: "Свойство StayInSync | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset20::StayInSync
- Recordset20::put_StayInSync
- Recordset20::PutStayInSync
- Recordset20::get_StayInSync
- Recordset20::GetStayInSync
helpviewer_keywords: StayInSync property
ms.assetid: 502d69b5-dc9a-455d-b115-a03bd39a552b
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6ef263a54892c31df4c44de8ebdb29308ef3dfb5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="stayinsync-property"></a>Свойство StayInSync
Указывает в иерархической [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, является ли ссылку на основные дочерние записи (т. е *главе*) изменяется при изменения позиции родительской строки.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **логическое** значение. Значение по умолчанию — **True**. Если **True**, главе будут обновлены, если родительский **записей** позиция; строки изменения объекта, если **False**, глава продолжат ссылаться на данные в предыдущем разделе Несмотря на то что родительского **записей** объекта был изменен позиции строки.  
  
## <a name="remarks"></a>Remarks  
 Это свойство применяется к иерархические наборы записей, например поддерживаемым [службы Microsoft Data Shaping Service для OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)и должны быть заданы для родительского **записей** перед дочерним элементом  **Набор записей** извлекается. Это свойство упрощает перемещение иерархические наборы записей.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства StayInSync (Visual Basic)](../../../ado/reference/ado-api/stayinsync-property-example-vb.md)   
 [Microsoft службы формирования данных для OLE DB (ADO поставщиком услуг)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)
