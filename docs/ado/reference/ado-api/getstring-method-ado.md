---
description: Метод GetString (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: ef3d32e1caae337ecb2a03bba6af8c7b4cd858de
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443516"
---
# <a name="getstring-method-ado"></a>Метод GetString (ADO)
Возвращает [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md) в виде строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Variant = recordset.GetString(StringFormat, NumRows, ColumnDelimiter, RowDelimiter, NullExpr)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **набор записей** как строковый **вариант** (BSTR).  
  
#### <a name="parameters"></a>Параметры  
 *StringFormat*  
 Значение [стрингформатенум](../../../ado/reference/ado-api/stringformatenum.md) , указывающее, как **набор записей** должен быть преобразован в строку. Параметры *RowDelimiter*, *ColumnDelimiter*и *Нуллекспр* используются только с *StringFormat* **адклипстринг**.  
  
 *нумровс*  
 Необязательный параметр. Число строк для преобразования в **наборе записей**. Если *нумровс* не указан или превышает общее число строк в **наборе записей**, то преобразуются все строки в **наборе записей** .  
  
 *ColumnDelimiter*  
 Необязательный параметр. Разделитель, используемый между столбцами, если он указан; в противном случае — символ ТАБУЛЯЦИи.  
  
 *RowDelimiter*  
 Необязательный параметр. Разделитель, используемый между строками, если они заданы; в противном случае — символ возврата КАРЕТки.  
  
 *нуллекспр*  
 Необязательный параметр. Выражение, используемое вместо значения NULL, если оно указано, в противном случае — пустая строка.  
  
## <a name="remarks"></a>Remarks  
 Данные строк, но отсутствуют данные схемы, сохраняются в строке. Таким образом, **набор записей** нельзя открыть повторно с помощью этой строки.  
  
 Этот метод эквивалентен методу RDO **жетклипстринг** .  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример метода GetString (Visual Basic)](../../../ado/reference/ado-api/getstring-method-example-vb.md)
