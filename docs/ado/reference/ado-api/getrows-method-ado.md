---
description: Метод GetRows (ADO)
title: Метод GetRows (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::GetRows
- Recordset15::raw_GetRows
helpviewer_keywords:
- Getrows method [ADO]
ms.assetid: 14b92860-4171-47d9-a413-dd60dd6a8880
author: rothja
ms.author: jroth
ms.openlocfilehash: 3a197cf085c4c1d741c19a55524313edbd4c5906
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443566"
---
# <a name="getrows-method-ado"></a>Метод GetRows (ADO)
Извлекает несколько записей объекта [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) в массив.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array = recordset.GetRows(Rows, Start, Fields )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **вариант** , значение которого является двумерным массивом.  
  
#### <a name="parameters"></a>Параметры  
 *Строки*  
 Необязательный параметр. Значение [жетровсоптионенум](../../../ado/reference/ado-api/getrowsoptionenum.md) , указывающее количество извлекаемых записей. Значение по умолчанию — **аджетровсрест**.  
  
 *Начало*  
 Необязательный параметр. **Строковое** значение или **вариант** , результатом которого является закладка для записи, из которой должна начинаться операция **GetRows** . Можно также использовать значение [букмаркенум](../../../ado/reference/ado-api/bookmarkenum.md) .  
  
 *Поля*  
 Необязательный параметр. **Вариант** , представляющий одно имя поля или порядковый номер, либо массив имен полей или порядковые номера позиций. ADO возвращает только данные из этих полей.  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **GetRows** для копирования записей из **набора записей** в двухмерный массив. Первый подстрочный индекс определяет поле, а второе — номер записи. Если метод **GetRows** возвращает данные, переменная *массива* автоматически изменяется в размерах до нужного размера.  
  
 Если не указать значение для аргумента ROWS **, метод** *GetRows* автоматически извлекает все записи в объекте **Recordset** . Если запрашивается больше записей, чем доступно, функция **GetRows** возвращает только количество доступных записей.  
  
 Если объект **Recordset** поддерживает закладки, можно указать, в какой записи метод **GetRows** должен начинать извлечение данных, передав значение свойства [закладки](../../../ado/reference/ado-api/bookmark-property-ado.md) этой записи в аргументе *Start* .  
  
 Если необходимо ограничить поля, возвращаемые вызовом **GetRows** , можно передать одно имя поля или число или массив имен полей в аргументе *Fields* .  
  
 После вызова метода **GetRows**Следующая непрочтенная запись становится текущей записью, либо свойство [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) имеет значение **true** , если больше нет записей.  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример метода GetRows (Visual Basic)](../../../ado/reference/ado-api/getrows-method-example-vb.md)   
 [Пример метода GetRows (Visual C++)](../../../ado/reference/ado-api/getrows-method-example-vc.md)   
