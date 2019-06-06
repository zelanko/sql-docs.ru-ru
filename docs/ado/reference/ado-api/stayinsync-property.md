---
title: Пример свойства StayInSync | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::StayInSync
- Recordset20::put_StayInSync
- Recordset20::PutStayInSync
- Recordset20::get_StayInSync
- Recordset20::GetStayInSync
helpviewer_keywords:
- StayInSync property
ms.assetid: 502d69b5-dc9a-455d-b115-a03bd39a552b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 98a0cc1df12f905cd0d22d05b162983742d0f355
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66710787"
---
# <a name="stayinsync-property"></a>Свойство StayInSync
Указывает, в иерархической [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект ли ссылку на основные дочерние записи (т. е *глава*) сохранение изменений, если изменения размещения родительской строки.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **логическое** значение. Значение по умолчанию ― **True**. Если **True**, главы будут обновлены, если родительский **записей** позиция; строки изменения объекта, если **False**, глава по-прежнему ссылаются на данные в предыдущей главе Несмотря на то что родительского **записей** объекта изменилось позиции строки.  
  
## <a name="remarks"></a>Примечания  
 Это свойство применяется к иерархических наборов записей, например поддерживаемый [службы Microsoft Data Shaping Service для OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)и должно задаваться в родительском **записей** перед дочерним элементом  **Набор записей** извлекается. Это свойство упрощает перемещение иерархических наборов записей.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства StayInSync (Visual Basic)](../../../ado/reference/ado-api/stayinsync-property-example-vb.md)   
 [Служба для OLE DB (ADO поставщиком услуг) формирования данных](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)
