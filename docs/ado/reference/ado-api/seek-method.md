---
description: Метод Seek
title: Seek, метод | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 3b2058751177d0498e89d1f9bd631a3151490c9d
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989165"
---
# <a name="seek-method"></a>Метод Seek
Выполняет поиск индекса [набора записей](./recordset-object-ado.md) , чтобы быстро найти строку, совпадающую с указанными значениями, и изменяет положение текущей строки на эту строку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
recordset.Seek KeyValues, SeekOption  
```  
  
#### <a name="parameters"></a>Параметры  
 *кэйвалуес*  
 Массив значений **типа Variant** . Индекс состоит из одного или нескольких столбцов, а массив содержит значение, сравниваемое с каждым соответствующим столбцом.  
  
 *сикоптион*  
 Значение [сикенум](./seekenum.md) , указывающее тип сравнения между столбцами индекса и соответствующим *кэйвалуес*.  
  
## <a name="remarks"></a>Remarks  
 Используйте метод **Seek** в сочетании со свойством [index](./index-property.md) , если базовый поставщик поддерживает индексы в объекте **Recordset** . Используйте метод [поддерживает](./supports-method.md)**(адсик)** , чтобы определить, поддерживает ли базовый поставщик **Поиск**, и **поддерживает метод (адиндекс)** , чтобы определить, поддерживает ли поставщик индексы. (Например, [поставщик OLE DB для Microsoft Jet](../../guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) поддерживает **Поиск** и **индексирование**.)  
  
 Если **Seek** не находит нужную строку, ошибка не возникает и строка располагается в конце **набора записей**. Перед выполнением этого метода задайте для свойства **index** нужный индекс.  
  
 Этот метод поддерживается только с курсорами на стороне сервера. Поиск не поддерживается, если значение свойства [CursorLocation](./cursorlocation-property-ado.md) объекта **Recordset** равно **адусеклиент**.  
  
 Этот метод можно использовать только при открытии объекта **Recordset** с [коммандтипинум](./commandtypeenum.md) значением **адкмдтабледирект**.  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода Seek и свойства Index (Visual Basic)](./seek-method-and-index-property-example-vb.md)   
 [Пример метода Seek и свойства Index (Visual c++)](./seek-method-and-index-property-example-vc.md)   
 [Метод Find (ADO)](./find-method-ado.md)   
 [Свойство Index](./index-property.md)