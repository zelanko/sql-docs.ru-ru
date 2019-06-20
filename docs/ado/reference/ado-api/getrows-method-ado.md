---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6babeebec1eac78949f0a80eb0701b5b5ba1dcc2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66694841"
---
# <a name="getrows-method-ado"></a>Метод GetRows (ADO)
Извлекает несколько записей для [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект в массив.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array = recordset.GetRows(Rows, Start, Fields )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **Variant** , значение которого является двумерным массивом.  
  
#### <a name="parameters"></a>Параметры  
 *Строки*  
 Необязательный параметр. Объект [GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md) значение, указывающее количество извлекаемых записей. По умолчанию используется **adGetRowsRest**.  
  
 *Запуск*  
 Необязательный. Объект **строка** значение или **Variant** , результатом которого является закладка для записи из которой **GetRows** должна начаться операция. Можно также использовать [BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md) значение.  
  
 *Fields*  
 Необязательный параметр. Объект **Variant** , представляющий одно поле имя или порядковый номер или массив имен полей или номера порядковый номер. ADO возвращает только данные в этих полях.  
  
## <a name="remarks"></a>Примечания  
 Используйте **GetRows** метод копирования записей из **записей** в двухмерный массив. Первый индекс определяет поле, а второй определяет номер записи. *Массива* переменная автоматически распределяться используют правильный размер при **GetRows** метод возвращает данные.  
  
 Если не указать значение для *строк* аргумент, **GetRows** метод автоматически получает все записи в **записей** объекта. Если вы запрашиваете большее число записей, чем доступно, **GetRows** возвращает только число доступных записей.  
  
 Если **записей** объект поддерживает закладки, можно указать на какие записи **GetRows** метод должен начать извлечение данных, передав значение этой записи [закладки](../../../ado/reference/ado-api/bookmark-property-ado.md)свойство в *запустить* аргумент.  
  
 Если вы хотите ограничить поля, **GetRows** вызов возвращает, можно передать одно поле номер и имя или массив имен полей и количества *поля* аргумент.  
  
 После вызова метода **GetRows**, далее непрочитанные запись становится текущей записи, или [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) свойству **True** Если отсутствуют дополнительные записи.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода GetRows (Visual Basic)](../../../ado/reference/ado-api/getrows-method-example-vb.md)   
 [Пример метода GetRows (Visual C++)](../../../ado/reference/ado-api/getrows-method-example-vc.md)   
