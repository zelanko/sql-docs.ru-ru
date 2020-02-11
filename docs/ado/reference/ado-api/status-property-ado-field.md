---
title: Свойство Status (поле ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field::Status
- Field::get_Status
- Field::GetStatus
helpviewer_keywords:
- Status property [ADO Field]
ms.assetid: 8cd1f7f4-0a3a-4f07-b8ba-6582e70140ad
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d90eff53ef998a009aecd4d82fc3b502a487c01d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67930837"
---
# <a name="status-property-ado-field"></a>Свойство Status (объект Field ADO)
Указывает состояние объекта [поля](../../../ado/reference/ado-api/field-object.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение [фиелдстатусенум](../../../ado/reference/ado-api/fieldstatusenum.md) . Значение по умолчанию — **адфиелдок**.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="record-field-status"></a>Состояние поля записи  
 Изменения значения объекта **поля** в коллекции полей объекта [записи](../../../ado/reference/ado-api/record-object-ado.md) кэшируются до тех пор, пока не будет вызван метод [обновления](../../../ado/reference/ado-api/update-method.md) объекта. Если в этот момент изменение значения поля привело к ошибке, OLE DB вызывает ошибку **DB_E_ERRORSOCCURRED** (2147749409). Свойство Status любого из объектов **field** в коллекции **Fields** , вызвавшей ошибку, будет содержать значение из [фиелдстатусенум](../../../ado/reference/ado-api/fieldstatusenum.md) , описывающее причину проблемы.  
  
 Чтобы повысить производительность, Добавление и удаление коллекций [полей](../../../ado/reference/ado-api/fields-collection-ado.md) объекта **Record** кэшируется до тех пор, пока не будет вызван метод **Update** , а затем изменения вносятся в пакетное обновление. Если метод **обновления** не вызывается, сервер не обновляется. Если какие-либо обновления завершаются сбоем, возвращается ошибка поставщика OLE DB (DB_E_ERRORSOCCURRED), а свойство **Status** указывает объединенные значения операции и кода состояния ошибки. Например, **АДФИЕЛДПЕНДИНГИНСЕРТ или адфиелдпермиссиондениед**. Свойство **Status** для каждого **поля** можно использовать для определения причины, по которой **поле** не было добавлено, изменено или удалено.  
  
 Многие типы проблем, возникающих при добавлении, изменении или удалении **поля** , передаются через свойство **Status** . Например, если пользователь удаляет **поле**, он помечается для удаления из коллекции **полей** . Если последующее **Обновление** возвращает ошибку, так как пользователь пытался удалить **поле** , для которого у него нет разрешения, **поле** будет иметь **состояние** **адфиелдпермиссиондениед или адфиелдпендингделете**. Вызов метода [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) восстанавливает исходные значения и устанавливает для **состояния** значение **адфиелдок**.  
  
 Аналогичным образом метод **Update** может возвращать ошибку, так как Добавлено новое **поле** , и ему присвоено неверное значение. В этом случае новое **поле** будет находиться в коллекции **полей** и иметь состояние **Адфиелдпендингинсерт** и, возможно, **адфиелдканткреате** (в зависимости от поставщика). Вы можете указать соответствующее значение для нового **поля** и снова вызвать **Update** .  
  
## <a name="recordset-field-status"></a>Состояние поля набора записей  
 Изменения значения объекта **field** в коллекции Fields либо [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) кэшируются до тех пор, пока не будет вызван метод [Update](../../../ado/reference/ado-api/update-method.md) объекта. Если в этот момент изменение значения поля привело к ошибке, OLE DB вызывает ошибку **DB_E_ERRORSOCCURRED** (2147749409). Свойство Status любого из объектов **field** в коллекции **Fields** , вызвавшей ошибку, будет содержать значение из [фиелдстатусенум](../../../ado/reference/ado-api/fieldstatusenum.md) , описывающее причину проблемы.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства Status (поле) (VB)](../../../ado/reference/ado-api/status-property-example-field-vb.md)   
 [Пример свойства Status (Visual C++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
