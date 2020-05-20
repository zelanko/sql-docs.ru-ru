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
author: rothja
ms.author: jroth
ms.openlocfilehash: 166bfad93d994a4b85bdb944a5d5505987182044
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758750"
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
 Необязательный элемент. Число строк для преобразования в **наборе записей**. Если *нумровс* не указан или превышает общее число строк в **наборе записей**, то преобразуются все строки в **наборе записей** .  
  
 *ColumnDelimiter*  
 Необязательный элемент. Разделитель, используемый между столбцами, если он указан; в противном случае — символ ТАБУЛЯЦИи.  
  
 *RowDelimiter*  
 Необязательный элемент. Разделитель, используемый между строками, если они заданы; в противном случае — символ возврата КАРЕТки.  
  
 *нуллекспр*  
 Необязательный элемент. Выражение, используемое вместо значения NULL, если оно указано, в противном случае — пустая строка.  
  
## <a name="remarks"></a>Примечания  
 Данные строк, но отсутствуют данные схемы, сохраняются в строке. Таким образом, **набор записей** нельзя открыть повторно с помощью этой строки.  
  
 Этот метод эквивалентен методу RDO **жетклипстринг** .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода GetString (Visual Basic)](../../../ado/reference/ado-api/getstring-method-example-vb.md)
