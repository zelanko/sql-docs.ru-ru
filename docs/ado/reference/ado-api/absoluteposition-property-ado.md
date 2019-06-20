---
title: Свойство AbsolutePosition (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::AbsolutePosition
helpviewer_keywords:
- AbsolutePosition property [ADO]
ms.assetid: 79f8ee5e-fc70-46d8-8c29-ebf943c66592
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 467834d2cfd5e56c14d9c7565d6749fa6848251e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718345"
---
# <a name="absoluteposition-property-ado"></a>Свойство AbsolutePosition (ADO)
Указывает порядковый номер [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта текущей записи.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 32-разрядного кода, задает или возвращает **Long** значение от 1 до количество записей в **записей** объекта ([RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)), или возвращает одно из [ PositionEnum](../../../ado/reference/ado-api/positionenum.md) значения.  
  
 Для 64-разрядного кода используйте тип данных, который предоставляет для хранения 64-разрядное значение. К примеру, можно использовать долго или другое значение, которое является 64-разрядных длину, например DBORDINAL. Не используйте **PositionEnum** значения, так как они ограничены длиной в 32-разрядной.  
  
## <a name="remarks"></a>Примечания  
 Чтобы задать **примеры AbsolutePosition** требует ADO свойство, что при использовании поставщика OLE DB реализовать [IRowsetLocate:IRowset](https://msdn.microsoft.com/library/windows/desktop/ms721190.aspx) интерфейс.  
  
 Доступ к **примеры AbsolutePosition** свойство **записей** , был открыт с помощью последовательного или динамический курсор вызывает ошибку **adErrFeatureNotAvailable**. Для других типов курсоров правильной позиции будет возвращаться до тех пор, пока поставщик OLE DB поддерживает **IRowsetScroll:IRowsetLocate** интерфейс. Если поставщик не поддерживает **IRowsetScroll** интерфейс, свойство имеет значение **adPosUnknown**. См. в документации вашего поставщика, чтобы определить, поддерживает ли он **IRowsetScroll**.  
  
 Используйте **примеры AbsolutePosition** значение, чтобы перейти к записи в зависимости от его порядковый номер в **записей** объекта, или чтобы определить порядковый номер текущей записи. Поставщик должен поддерживать соответствующие функциональные возможности для этого свойства доступен.  
  
 Как и [примеры AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) свойство, **примеры AbsolutePosition** отсчитывается от 1, и равняется 1 при первой записи в текущей записи **записей**. Можно получить общее число записей в **записей** объекта из [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) свойство.  
  
 При задании **примеры AbsolutePosition** свойство, даже если это запись в текущем кэше ADO перезагружает кэша с новой группой записей, начиная с записи, вы указали. [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) свойство определяет размер этой группы.  
  
> [!NOTE]
>  Не следует использовать **примеры AbsolutePosition** свойство как число записей суррогат. Определенной записи перемещается при удалении предыдущей записи. Нет также никакой гарантий, что определенной записи будет иметь тот же **примеры AbsolutePosition** Если **записей** опросить или повторном открытии объекта. Закладки, по-прежнему являются рекомендуемым способом сохранения и возврат к заданной позиции и являются единственным способом размещения во всех типах **записей** объектов.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры AbsolutePosition и CursorLocation свойства (Visual Basic)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vb.md)   
 [Примеры AbsolutePosition и CursorLocation свойства (Visual C++)](../../../ado/reference/ado-api/absoluteposition-and-cursorlocation-properties-example-vc.md)   
 [Свойство AbsolutePage (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [Свойство RecordCount (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)
