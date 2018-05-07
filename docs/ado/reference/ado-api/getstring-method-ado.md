---
title: Метод GetString (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::raw_GetString
- Recordset20::GetString
helpviewer_keywords:
- GetString method [ADO]
ms.assetid: 92452940-b2a7-456e-94fc-3780c71da33c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 373ef70e69d528d41fc2631610a7f31f72c3eec7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getstring-method-ado"></a>Метод GetString (ADO)
Возвращает [записей](../../../ado/reference/ado-api/recordset-object-ado.md) как строка.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Variant = recordset.GetString(StringFormat, NumRows, ColumnDelimiter, RowDelimiter, NullExpr)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **записей** как строковое значение **Variant** (BSTR).  
  
#### <a name="parameters"></a>Параметры  
 *StringFormat*  
 Объект [StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md) значение, указывающее, как **записей** должны преобразовываться в строку. *RowDelimiter*, *ColumnDelimiter*, и *NullExpr* параметры используются только вместе с *StringFormat* из  **adClipString**.  
  
 *NumRows*  
 Необязательно. Число строк, которые должны преобразовываться в **записей**. Если *NumRows* не указан, или если это значение превышает общее число строк в **записей**, затем все строки **записей** преобразуются.  
  
 *ColumnDelimiter*  
 Необязательно. Разделитель, используемый между столбцами, если указано, в противном случае символ табуляции.  
  
 *rowDelimiter*  
 Необязательно. Разделитель, используемый между строками, если указано, в противном случае символ возврата каретки.  
  
 *NullExpr*  
 Необязательно. Выражение, используемое вместо значения null, если указано, в противном случае — пустая строка.  
  
## <a name="remarks"></a>Замечания  
 Строки данных, но не данные схемы, сохраняется в строке. Таким образом **записей** нельзя открыть повторно с помощью этой строки.  
  
 Этот метод эквивалентен методу RDO **GetClipString** метод.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода GetString (Visual Basic)](../../../ado/reference/ado-api/getstring-method-example-vb.md)
