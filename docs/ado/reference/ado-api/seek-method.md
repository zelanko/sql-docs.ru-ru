---
description: Метод Seek
title: Seek, метод | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset21::Seek
- Recordset21::raw_Seek
helpviewer_keywords:
- Seek method [ADO]
ms.assetid: 129293d2-19d3-4940-bf64-483ee72fb4a1
author: rothja
ms.author: jroth
ms.openlocfilehash: b9eecf5caee690687adaffda7ccd56d869abb9e3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442103"
---
# <a name="seek-method"></a>Метод Seek
Выполняет поиск индекса [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) , чтобы быстро найти строку, совпадающую с указанными значениями, и изменяет положение текущей строки на эту строку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Seek KeyValues, SeekOption  
```  
  
#### <a name="parameters"></a>Параметры  
 *кэйвалуес*  
 Массив значений **типа Variant** . Индекс состоит из одного или нескольких столбцов, а массив содержит значение, сравниваемое с каждым соответствующим столбцом.  
  
 *сикоптион*  
 Значение [сикенум](../../../ado/reference/ado-api/seekenum.md) , указывающее тип сравнения между столбцами индекса и соответствующим *кэйвалуес*.  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **Seek** в сочетании со свойством [index](../../../ado/reference/ado-api/index-property.md) , если базовый поставщик поддерживает индексы в объекте **Recordset** . Используйте метод [поддерживает](../../../ado/reference/ado-api/supports-method.md)**(адсик)** , чтобы определить, поддерживает ли базовый поставщик **Поиск**, и **поддерживает метод (адиндекс)** , чтобы определить, поддерживает ли поставщик индексы. (Например, [поставщик OLE DB для Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) поддерживает **Поиск** и **индексирование**.)  
  
 Если **Seek** не находит нужную строку, ошибка не возникает и строка располагается в конце **набора записей**. Перед выполнением этого метода задайте для свойства **index** нужный индекс.  
  
 Этот метод поддерживается только с курсорами на стороне сервера. Поиск не поддерживается, если значение свойства [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) объекта **Recordset** равно **адусеклиент**.  
  
 Этот метод можно использовать только при открытии объекта **Recordset** с [коммандтипинум](../../../ado/reference/ado-api/commandtypeenum.md) значением **адкмдтабледирект**.  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример метода Seek и свойства Index (Visual Basic)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Пример метода Seek и свойства Index (Visual c++)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vc.md)   
 [Метод Find (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Свойство Index](../../../ado/reference/ado-api/index-property.md)
