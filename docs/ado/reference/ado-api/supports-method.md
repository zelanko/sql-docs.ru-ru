---
title: Поддерживает метод | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_Supports
- Recordset15::Supports
helpviewer_keywords:
- Supports method [ADO]
ms.assetid: 298fc41c-0b55-42fc-b373-c5133b4da6a5
author: rothja
ms.author: jroth
ms.openlocfilehash: 3fbfbf28c430fb698f5e024fe3359027c84512c0
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765365"
---
# <a name="supports-method"></a>Метод Supports
Определяет, поддерживает ли указанный объект [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) определенный тип функциональности.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **логическое** значение, указывающее, поддерживаются ли поставщиком все компоненты, определенные аргументом *курсороптионс* .  
  
#### <a name="parameters"></a>Параметры  
 *курсороптионс*  
 **Длинное** выражение, состоящее из одного или нескольких значений [курсороптионенум](../../../ado/reference/ado-api/cursoroptionenum.md) .  
  
## <a name="remarks"></a>Примечания  
 Используйте метод **поддерживает** , чтобы определить, какие типы функций поддерживает объект **Recordset** . Если объект **набора записей** поддерживает функции, соответствующие константы которых находятся в *Курсороптионс*, метод **поддерживает** возврат значения **true**. В противном случае возвращается **значение false**.  
  
> [!NOTE]
>  Несмотря на то, что метод **поддерживает** возврат значения **true** для заданной функциональности, он не гарантирует, что поставщик может сделать эту функцию доступной во всех обстоятельствах. Метод Supports просто **возвращает значение,** указывающее, может ли поставщик поддерживать указанные функциональные возможности при условии, что выполняются определенные условия. Например, метод **поддержки** может указывать на то, что объект **набора записей** поддерживает обновления, даже если курсор основан на множественном соединении таблиц, некоторые столбцы, не являющиеся обновляемыми.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода поддержки (Visual Basic)](../../../ado/reference/ado-api/supports-method-example-vb.md)   
 [Пример метода поддержки (Visual c++)](../../../ado/reference/ado-api/supports-method-example-vc.md)   
 [Свойство CursorType (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
