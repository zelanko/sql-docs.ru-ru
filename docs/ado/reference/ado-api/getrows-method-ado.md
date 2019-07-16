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
ms.openlocfilehash: d96b7968c7aba8d1249db2f43b53fc8a22596419
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67918452"
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
 Необязательный. Объект [GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md) значение, указывающее количество извлекаемых записей. По умолчанию используется **adGetRowsRest**.  
  
 *Запуск*  
 Необязательный. Объект **строка** значение или **Variant** , результатом которого является закладка для записи из которой **GetRows** должна начаться операция. Можно также использовать [BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md) значение.  
  
 *Fields*  
 Необязательный. Объект **Variant** , представляющий одно поле имя или порядковый номер или массив имен полей или номера порядковый номер. ADO возвращает только данные в этих полях.  
  
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
