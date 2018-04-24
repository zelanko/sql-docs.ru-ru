---
title: Свойство CursorType (ADO) | Документы Microsoft
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
- Recordset15::CursorType
helpviewer_keywords:
- CursorType property [ADO]
ms.assetid: b62c66ca-58d5-430e-9257-eb38c65e48c2
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ae4864ef3b02ccd51c90cce85c15ca64ea150072
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="cursortype-property-ado"></a>Свойство CursorType (ADO)
Указывает тип курсора, используемого в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) значение. Значение по умолчанию — **adOpenForwardOnly**.  
  
## <a name="remarks"></a>Замечания  
 Используйте **CursorType** свойство, чтобы указать тип курсора, который должен использоваться при открытии **записей** объекта.  
  
 Только если параметр **adOpenStatic** поддерживается, если [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойству **adUseClient**. Если задано недопустимое значение, ошибка не приведет к; ближайшее поддерживается **CursorType** вместо него будет использоваться.  
  
 Если поставщик не поддерживает тип курсора, может вернуть другой тип курсора. **CursorType** свойство изменятся с учетом фактический тип курсора в используется, когда [записей](../../../ado/reference/ado-api/recordset-object-ado.md) открыт объект. Чтобы проверить определенных функций возвращаемый курсор, используйте [поддерживает](../../../ado/reference/ado-api/supports-method.md) метод. После того как вы закроете **записей**, **CursorType** восстанавливает исходное значение свойства.  
  
 В следующей таблице представлены функциональные возможности поставщика (определяется **поддерживает** константы метод) для каждого типа курсора.  
  
|Для набора записей этого CursorType|Поддерживает метод должен возвращать значение True для всех этих констант|  
|----------------------------------------|---------------------------------------------------------------------|  
|**adOpenForwardOnly**|none|  
|**adOpenKeyset**|**adBookmark**, **adHoldRecords**, **adMovePrevious**, **adResync**|  
|**adOpenDynamic**|**adMovePrevious**|  
|**adOpenStatic**|**adBookmark**, **adHoldRecords**, **adMovePrevious**, **adResync**|  
  
> [!NOTE]
>  Несмотря на то что **поддерживает**(**adUpdateBatch**) может быть значение true для динамических и однонаправленные курсоры, для пакета обновления, вы должны использовать управляемые набором ключей или статических курсоров. Задать [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) свойства **adLockBatchOptimistic** и **CursorLocation** свойства **adUseClient** для включения курсора Служба для OLE DB, который необходим для пакетных обновлений.  
  
 **CursorType** свойство доступно для чтения/записи при **записей** будет закрыто, только для чтения при открытом.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **записей** объекта, **CursorType** может быть задано только в **adOpenStatic**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [CursorType LockType и пример EditMode свойства (Visual Basic)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [CursorType LockType и пример использования свойств EditMode (VC ++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Метод Supports](../../../ado/reference/ado-api/supports-method.md)
