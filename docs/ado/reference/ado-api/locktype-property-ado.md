---
title: "Свойство LockType (ADO) | Документы Microsoft"
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
f1_keywords: Recordset15::LockType
helpviewer_keywords: LockType property [ADO]
ms.assetid: 9920c14e-033a-4de1-8149-0ce9737a3246
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c3b9a206a312fcd0ac113f19de73979050e35c78
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="locktype-property-ado"></a>Свойство LockType (ADO)
Указывает тип блокировки записей во время редактирования.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) значение. Значение по умолчанию — **adLockReadOnly**.  
  
## <a name="remarks"></a>Замечания  
 Задать **LockType** свойство перед открытием [записей](../../../ado/reference/ado-api/recordset-object-ado.md) для указания, какой поставщик блокировки следует использовать при его открытии. Прочесть свойство для возврата типа блокировки используется открытый **записей** объекта.  
  
 Поставщики могут не поддерживать все типы блокировок. Если поставщик не поддерживает запрошенный **LockType** задание, он заменит другой тип блокировки. Чтобы определить фактический блокировки функциональные возможности, доступные в **записей** , используйте [поддерживает](../../../ado/reference/ado-api/supports-method.md) метод с **adUpdate** и **adUpdateBatch**.  
  
 **AdLockPessimistic** параметр не поддерживается, если [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойству **adUseClient**. Если задано недопустимое значение, ошибка не приведет к; ближайшее поддерживается **LockType** вместо него будет использоваться.  
  
 **LockType** свойство доступно для чтения/записи при **записей** будет закрыто, только для чтения при открытом.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **записей** объекта, **LockType** свойству можно присвоить только значение **adLockBatchOptimistic**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [CursorType LockType и пример EditMode свойства (Visual Basic)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [CursorType LockType и пример использования свойств EditMode (VC ++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Метод CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Метод UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)
