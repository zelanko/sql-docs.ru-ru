---
title: Свойство LockType (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::LockType
helpviewer_keywords:
- LockType property [ADO]
ms.assetid: 9920c14e-033a-4de1-8149-0ce9737a3246
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05670439a8f14018a999557dd135912e0c2e0159
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864100"
---
# <a name="locktype-property-ado"></a>Свойство LockType (ADO)
Указывает тип блокировки записей во время редактирования.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) значение. Значение по умолчанию — **adLockReadOnly**.  
  
## <a name="remarks"></a>Примечания  
 Задайте **LockType** свойство перед открытием [записей](../../../ado/reference/ado-api/recordset-object-ado.md) для указания, какой тип блокировки поставщик следует использовать при его открытии. Чтение свойства, чтобы оно возвращало тип блокировки используется при открытии **записей** объекта.  
  
 Поставщики могут не поддерживать все типы блокировки. Если поставщик не поддерживает запрошенный **LockType** задание, он заменит другой тип блокировки. Чтобы определить фактический блокировки функциональные возможности, доступные в **записей** , используйте [поддерживает](../../../ado/reference/ado-api/supports-method.md) метод с **adUpdate** и **adUpdateBatch**.  
  
 **AdLockPessimistic** параметр не поддерживается, если [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойству **adUseClient**. Если задано неподдерживаемое значение, сообщение об ошибке не приведет к; ближайшим поддерживается **LockType** вместо него будет использоваться.  
  
 **LockType** свойство доступно для чтения/записи при **записей** является закрытым или только для чтения, когда он открыт.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **записей** объекта, **LockType** свойство может устанавливаться только **adLockBatchOptimistic**.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры CursorType, LockType и EditMode по свойства (Visual Basic)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [Примеры CursorType, LockType и EditMode пример свойства (Visual C++)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Метод CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Метод UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)
