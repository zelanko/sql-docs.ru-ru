---
title: "Метод GetString (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset20::raw_GetString
- Recordset20::GetString
helpviewer_keywords: GetString method [ADO]
ms.assetid: 92452940-b2a7-456e-94fc-3780c71da33c
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 6f92e1be67ce0eb26f300cde4b1ef53bfc5dc49c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
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
 Необязательный параметр. Число строк, которые должны преобразовываться в **записей**. Если *NumRows* не указан, или если это значение превышает общее число строк в **записей**, затем все строки **записей** преобразуются.  
  
 *ColumnDelimiter*  
 Необязательный параметр. Разделитель, используемый между столбцами, если указано, в противном случае символ табуляции.  
  
 *RowDelimiter*  
 Необязательный параметр. Разделитель, используемый между строками, если указано, в противном случае символ возврата каретки.  
  
 *NullExpr*  
 Необязательный параметр. Выражение, используемое вместо значения null, если указано, в противном случае — пустая строка.  
  
## <a name="remarks"></a>Remarks  
 Строки данных, но не данные схемы, сохраняется в строке. Таким образом **записей** нельзя открыть повторно с помощью этой строки.  
  
 Этот метод эквивалентен методу RDO **GetClipString** метод.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример метода GetString (Visual Basic)](../../../ado/reference/ado-api/getstring-method-example-vb.md)
