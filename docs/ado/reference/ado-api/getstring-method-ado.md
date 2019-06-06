---
title: Метод GetString (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::raw_GetString
- Recordset20::GetString
helpviewer_keywords:
- GetString method [ADO]
ms.assetid: 92452940-b2a7-456e-94fc-3780c71da33c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 14bb7fd2e4a6dd8e6eb8f369342923ce1a9728c9
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66697613"
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
 Объект [StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md) значение, которое указывает, каким образом **набор записей** должен быть преобразован в строку. *RowDelimiter*, *ColumnDelimiter*, и *NullExpr* параметры используются только совместно с *StringFormat* из  **adClipString**.  
  
 *NumRows*  
 Необязательный параметр. Число строк для преобразования в **записей**. Если *NumRows* не указан, или если оно превышает общее число строк в **записей**, затем все строки **записей** преобразуются.  
  
 *ColumnDelimiter*  
 Необязательный. Разделитель, используемый между столбцами, если указано, в противном случае символ табуляции.  
  
 *RowDelimiter*  
 Необязательный параметр. Разделитель, используемый между строками, если указано, в противном случае символ возврата каретки.  
  
 *NullExpr*  
 Необязательный. Выражение, используемое вместо значение null, если указано, в противном случае пустая строка.  
  
## <a name="remarks"></a>Примечания  
 Данные строк, но не данные схемы, сохраняется в строку. Таким образом **записей** нельзя открыть повторно с помощью этой строки.  
  
 Этот метод эквивалентен RDO **GetClipString** метод.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода GetString (Visual Basic)](../../../ado/reference/ado-api/getstring-method-example-vb.md)
