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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 97c0e4660c14845ddfb59ce4f5f509a0954d98f0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616982"
---
# <a name="supports-method"></a>Метод Supports
Определяет, является ли заданное [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект поддерживает определенный тип функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **логическое** значение, указывающее, ли все функции, определяемые *CursorOptions* аргумент поддерживаются поставщиком.  
  
#### <a name="parameters"></a>Параметры  
 *CursorOptions*  
 Объект **Long** выражение, которое состоит из одного или нескольких [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md) значения.  
  
## <a name="remarks"></a>Примечания  
 Используйте **поддерживает** метод, чтобы определить, какие функциональные возможности **записей** поддерживает. Если **записей** объект поддерживает функции, соответствующие константы находятся в *CursorOptions*, **поддерживает** возвращает метод **True**. В противном случае возвращается **False**.  
  
> [!NOTE]
>  Несмотря на то что **поддерживает** метод может вернуть **True** для данной функциональности, она не гарантирует, что поставщик можно включить при любых обстоятельствах. **Поддерживает** метод просто возвращает поставщик поддерживает ли эта функция, при условии, что определенных условий. Например **поддерживает** метод может указать, что **записей** объект поддерживает обновления, несмотря на то, что курсор основан на нескольких соединение таблиц, некоторые столбцы, которые не являются обновляемыми.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Поддерживает метод пример (Visual Basic)](../../../ado/reference/ado-api/supports-method-example-vb.md)   
 [Поддерживает метод пример (Visual C++)](../../../ado/reference/ado-api/supports-method-example-vc.md)   
 [Свойство CursorType (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
