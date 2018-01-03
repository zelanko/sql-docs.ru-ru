---
title: "Метод GetRows (ADO) | Документы Microsoft"
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
- Recordset15::GetRows
- Recordset15::raw_GetRows
helpviewer_keywords: Getrows method [ADO]
ms.assetid: 14b92860-4171-47d9-a413-dd60dd6a8880
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 317e654699ab6e2c6abc349d91ed58d4c97a7a19
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="getrows-method-ado"></a>Метод GetRows (ADO)
Возвращает множество записей, имеющих [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект в массив.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
array = recordset.GetRows(Rows, Start, Fields )  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **Variant** , значение которого является двумерным массивом.  
  
#### <a name="parameters"></a>Параметры  
 *Строки*  
 Необязательный параметр. Объект [GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md) значение, указывающее число получаемых записей. Значение по умолчанию — **adGetRowsRest**.  
  
 *Запуск*  
 Необязательный параметр. Объект **строка** значение или **Variant** , результатом которого является закладка для записи из которого **GetRows** должна начаться операция. Можно также использовать [BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md) значение.  
  
 *Fields*  
 Необязательный параметр. Объект **Variant** , представляющий одно поле имя или порядковый номер или массив имен полей или номера порядковый номер. ADO возвращает только данные в этих полях.  
  
## <a name="remarks"></a>Remarks  
 Используйте **GetRows** метод копирования записей из **записей** в двухмерный массив. Первый индекс определяет поля, а второй определяет номер записи. *Массива* переменной автоматически измеренных правильный размер при **GetRows** метод возвращает данные.  
  
 Если не указать значение для *строк* аргумент, **GetRows** метод автоматически получает все записи в **записей** объекта. Если запрос больше записей, чем доступно, **GetRows** возвращает число доступных записей.  
  
 Если **записей** объект поддерживает закладки, можно указать на какие записи **GetRows** метод должен начать извлечение данных путем передачи значения этой записи [закладки](../../../ado/reference/ado-api/bookmark-property-ado.md)свойство в *запустить* аргумент.  
  
 Если вы хотите ограничить поля, **GetRows** вызов возвращает, можно передать одно поле имя или номер или массив имен полей и количества *поля* аргумент.  
  
 После вызова метода **GetRows**, далее непрочитанные запись становится текущей записи или [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) свойству **True** Если нет дополнительных записей.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример метода GetRows (Visual Basic)](../../../ado/reference/ado-api/getrows-method-example-vb.md)   
 [Пример метода GetRows (Visual C++)](../../../ado/reference/ado-api/getrows-method-example-vc.md)   
