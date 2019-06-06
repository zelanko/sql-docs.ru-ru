---
title: Свойство CursorType (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::CursorType
helpviewer_keywords:
- CursorType property [ADO]
ms.assetid: b62c66ca-58d5-430e-9257-eb38c65e48c2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7361b453272289107ea3c5ae268b951178aa1b43
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66695507"
---
# <a name="cursortype-property-ado"></a>Свойство CursorType (ADO)
Указывает тип курсора, используемого в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) значение. Значение по умолчанию — **adOpenForwardOnly**.  
  
## <a name="remarks"></a>Примечания  
 Используйте **CursorType** свойство, чтобы указать тип курсора, который должен использоваться при открытии **записей** объекта.  
  
 Только значение **adOpenStatic** поддерживается, если [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойству **adUseClient**. Если задано неподдерживаемое значение, сообщение об ошибке не приведет к; ближайшим поддерживается **CursorType** вместо него будет использоваться.  
  
 Если поставщик не поддерживает курсора запрошенного типа, он может вернуть другой тип курсора. **CursorType** свойство изменятся в соответствии фактический тип курсора используется при [записей](../../../ado/reference/ado-api/recordset-object-ado.md) открыт. Для проверки определенных функциональных возможностей, возвращенный курсора, используйте [поддерживает](../../../ado/reference/ado-api/supports-method.md) метод. После того как вы закроете **записей**, **CursorType** , свойство возвращается к исходному.  
  
 На следующей диаграмме показаны функциональные возможности поставщика (определяется **поддерживает** метод константы) требуется для каждого типа курсора.  
  
|Для объекта Recordset этот CursorType|Поддерживает метод должен возвращать значение True для всех этих констант|  
|----------------------------------------|---------------------------------------------------------------------|  
|**adOpenForwardOnly**|none|  
|**adOpenKeyset**|**adBookmark**, **adHoldRecords**, **adMovePrevious**, **adResync**|  
|**adOpenDynamic**|**adMovePrevious**|  
|**adOpenStatic**|**adBookmark**, **adHoldRecords**, **adMovePrevious**, **adResync**|  
  
> [!NOTE]
>  Несмотря на то что **поддерживает**(**adUpdateBatch**) может иметь значение true, если динамические и однонаправленные курсоры для пакета обновления, вам следует использовать либо курсора keyset или static. Задайте [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) свойства **adLockBatchOptimistic** и **CursorLocation** свойства **adUseClient** Чтобы включить курсор Служба для OLE DB, который необходим для пакетных обновлений.  
  
 **CursorType** свойство доступно для чтения/записи при **записей** является закрытым или только для чтения, когда он открыт.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **записей** объекта, **CursorType** свойству можно присвоить только значение **adOpenStatic**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры CursorType, LockType и EditMode по свойства (Visual Basic)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [Примеры CursorType, LockType и EditMode пример свойства (Visual C++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Метод Supports](../../../ado/reference/ado-api/supports-method.md)
