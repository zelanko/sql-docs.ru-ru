---
title: Коллекция (ADO) поля | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Fields
- Recordset15::Fields
- _Record::Fields
helpviewer_keywords:
- Fields collection [ADO]
ms.assetid: 7c371474-b88f-4730-afa5-44163a0488d5
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8483a908e31b9e4554c5594ecc5bbf186bbef88f
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66695041"
---
# <a name="fields-collection-ado"></a>Коллекция Fields (ADO)
Содержит все [поле](../../../ado/reference/ado-api/field-object.md) объектов [записей](../../../ado/reference/ado-api/recordset-object-ado.md) или [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта.  
  
## <a name="remarks"></a>Примечания  
 Объект **записей** объект имеет **поля** состоит из коллекции **поле** объектов. Каждый **поле** соответствует столбец в **записей**. Можно заполнить **поля** коллекции перед открытием **записей** путем вызова [обновить](../../../ado/reference/ado-api/refresh-method-ado.md) метод в коллекции.  
  
> [!NOTE]
>  См. в разделе **поле** разделе объекта более подробное описание способов использования **поле** объектов.  
  
 **Поля** коллекция имеет [Append](../../../ado/reference/ado-api/append-method-ado.md) метод, который условно создает и добавляет **поле** в коллекцию и **обновить**метод, который завершает добавлений или удалений.  
  
 Объект **записи** объект имеет два специальных поля могут быть проиндексированы с [FieldEnum](../../../ado/reference/ado-api/fieldenum.md) константы. Единственное, что постоянно обращается к полю, содержащему поток по умолчанию для **записи**, и другой обращается к полю, содержащий абсолютный URL-адрес строку для **записи**.  
  
 Некоторых поставщиков (например, [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)) может заполнить **поля** коллекции с подмножеством доступных полей для **записи** или **записей**. Другие поля не будут добавляться в коллекцию до сначала ссылаться по имени или проиндексирован кода.  
  
 При попытке сослаться на несуществующий поле по имени, новый **поле** объекта будут добавляться на **поля** коллекции с [состояние](../../../ado/reference/ado-api/status-property-ado-field.md) из  **adFieldPendingInsert**. При вызове [обновления](../../../ado/reference/ado-api/update-method.md), ADO будет создать новое поле в источнике данных, если это разрешено поставщиком.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства коллекции полей, методов и событий](../../../ado/reference/ado-api/fields-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)
