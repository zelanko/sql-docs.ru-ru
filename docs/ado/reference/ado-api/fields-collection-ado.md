---
title: Коллекция Fields (ADO) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: ecf6d672bd82b6ac532306cd1ca6fc2400b215e8
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762565"
---
# <a name="fields-collection-ado"></a>Коллекция Fields (ADO)
Содержит все объекты [полей](../../../ado/reference/ado-api/field-object.md) [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) или объекта [записи](../../../ado/reference/ado-api/record-object-ado.md) .  
  
## <a name="remarks"></a>Remarks  
 Объект **набора записей** содержит коллекцию **Fields** , состоящие из объектов **полей** . Каждый объект **field** соответствует столбцу в **наборе записей**. Можно заполнить коллекцию **Fields** перед открытием **набора записей** , вызвав метод [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) в коллекции.  
  
> [!NOTE]
>  Более подробное описание использования объектов **полей** см. в разделе объект **поля** .  
  
 Коллекция **Fields** имеет метод [append](../../../ado/reference/ado-api/append-method-ado.md) , который подготавливает создание и добавление объекта **field** в коллекцию, и метод **Update** , который завершает любые добавления или удаления.  
  
 Объект **Record** имеет два специальных поля, которые можно индексировать с помощью констант [фиелденум](../../../ado/reference/ado-api/fieldenum.md) . Одна константа обращается к полю, содержащему поток по умолчанию для **записи**, а другой — к полю, содержащему абсолютную строку URL-адреса для **записи**.  
  
 Некоторые поставщики (например, [поставщик Microsoft OLE DB для публикации в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)) могут заполнить коллекцию **Fields** набором доступных полей для **записи** или **набора записей**. Другие поля не добавляются в коллекцию до тех пор, пока на них не будет первая ссылка по имени или индексу в коде.  
  
 При попытке сослаться на несуществующее поле по имени новый объект **field** будет добавлен в коллекцию **Fields** с [состоянием](../../../ado/reference/ado-api/status-property-ado-field.md) **адфиелдпендингинсерт**. При вызове [Update](../../../ado/reference/ado-api/update-method.md)объект ADO создает новое поле в источнике данных, если оно разрешено поставщиком.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события коллекции Fields](../../../ado/reference/ado-api/fields-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)
