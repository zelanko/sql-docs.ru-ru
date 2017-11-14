---
title: "Поддерживает метод | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::raw_Supports
- Recordset15::Supports
helpviewer_keywords:
- Supports method [ADO]
ms.assetid: 298fc41c-0b55-42fc-b373-c5133b4da6a5
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 60e3039e48ea203b0585dba1ecbeaf7ad3e57907
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="supports-method"></a>Поддерживает метод
Определяет, является ли заданное [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект поддерживает функциональные возможности определенного типа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **логическое** значение, указывающее, ли все функции, определяемые *CursorOptions* аргумент поддерживаются поставщиком.  
  
#### <a name="parameters"></a>Параметры  
 *CursorOptions*  
 Объект **длинные** выражение, которое состоит из одного или нескольких [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md) значения.  
  
## <a name="remarks"></a>Замечания  
 Используйте **поддерживает** метод, чтобы определить, какие функциональные возможности **записей** поддерживает. Если **записей** объект поддерживает функции, соответствующей константы, в *CursorOptions*, **поддерживает** возвращает **True**. В противном случае он возвращает **False**.  
  
> [!NOTE]
>  Несмотря на то что **поддерживает** метод может возвращать **True** для данной функции, он не гарантирует, что поставщика можно включить ни при каких обстоятельствах. **Поддерживает** метод просто возвращает поставщик поддерживает ли эта функция, при условии, что определенных условий. Например **поддерживает** метод могут свидетельствовать о попытках **записей** объект поддерживает обновления, даже если курсор основан на нескольких соединение таблиц, некоторые столбцы не являются обновляемыми.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Поддерживает пример метода (Visual Basic)](../../../ado/reference/ado-api/supports-method-example-vb.md)   
 [Пример метода поддерживает (VC ++)](../../../ado/reference/ado-api/supports-method-example-vc.md)   
 [Свойство CursorType (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)

