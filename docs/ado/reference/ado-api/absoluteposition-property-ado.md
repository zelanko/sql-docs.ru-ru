---
title: "Свойство AbsolutePosition (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Recordset15::AbsolutePosition
helpviewer_keywords: AbsolutePosition property [ADO]
ms.assetid: 79f8ee5e-fc70-46d8-8c29-ebf943c66592
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 491ed39340dd066955db2fd73ed986614744cff4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="absoluteposition-property-ado"></a>Свойство AbsolutePosition (ADO)
Указывает порядковый номер [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта текущей записи.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 32-разрядный код задает или возвращает **длинные** значение от 1 до числа записей в **записей** объекта ([RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)), или возвращает одно из [ PositionEnum](../../../ado/reference/ado-api/positionenum.md) значения.  
  
 Для 64-разрядного кода используйте тип данных, который обеспечивает хранение 64-разрядное значение. Например, можно использовать долго или другой значение, представляющее длину 64-разрядной, например DBORDINAL. Не используйте **PositionEnum** значения, так как они ограничены длиной 32 бит.  
  
## <a name="remarks"></a>Замечания  
 Чтобы задать **AbsolutePosition** свойства, ADO требуется реализовать, поставщик OLE DB, который вы используете [IRowsetLocate:IRowset](https://msdn.microsoft.com/library/windows/desktop/ms721190.aspx) интерфейса.  
  
 Доступ к **AbsolutePosition** свойство **записей** , был открыт с помощью последовательным или динамический курсор вызывает ошибку **adErrFeatureNotAvailable**. Для других типов курсоров правильное положение будут возвращены при условии, что поставщик OLE DB поддерживает **IRowsetScroll:IRowsetLocate** интерфейса. Если поставщик не поддерживает **IRowsetScroll** интерфейс, является свойство **adPosUnknown**. См. в документации для поставщика определить, поддерживает ли он **IRowsetScroll**.  
  
 Используйте **AbsolutePosition** на основе свойства, чтобы перейти к записи по его порядковому номеру в **записей** объекта, или чтобы определить порядковый номер текущей записи. Поставщик должен поддерживать соответствующие функциональные возможности для этого свойства доступно.  
  
 Как [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) свойства **AbsolutePosition** начинается с 1 и имеет значение 1, если текущая запись является первой записью в **записей**. Вы можете получить общее число записей в **записей** объекта из [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) свойство.  
  
 При задании **AbsolutePosition** свойство, даже если это записи в текущий кэш ADO перезагружает кэша с новой группой записей, начиная с указанной записи. [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) свойство определяет размер этой группы.  
  
> [!NOTE]
>  Не следует использовать **AbsolutePosition** свойство в качестве символов-заместителей номер записи. Позиция изменения определенной записи, при удалении предыдущей записи. Нет никакой гарантии, что данная запись будет иметь такой же **AbsolutePosition** Если **записей** опросить или повторном открытии объекта. Закладки, будут по-прежнему рекомендуемый способ сохранения и возврат к заданной позиции и являются единственным способом размещения различных типов **записей** объектов.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [AbsolutePosition и CursorLocation-пример свойства (Visual Basic)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vb.md)   
 [AbsolutePosition и пример свойства CursorLocation (VC ++)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vc.md)   
 [Свойство AbsolutePage (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [Свойство RecordCount (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)
