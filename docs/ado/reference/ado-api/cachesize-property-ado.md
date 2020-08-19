---
description: Свойство CacheSize (ADO)
title: Свойство CacheSize (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::CacheSize
helpviewer_keywords:
- CacheSize property [ADO]
ms.assetid: 49dc9a49-af7b-433b-be36-7a14ca984fb7
author: rothja
ms.author: jroth
ms.openlocfilehash: 3cafee5dbcc5d6469df2d733f1898806069dd112
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451106"
---
# <a name="cachesize-property-ado"></a>Свойство CacheSize (ADO)
Указывает число записей из объекта [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) , которые кэшируются локально в памяти.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **длинное** значение, которое должно быть больше 0. Значение по умолчанию: 1.  
  
## <a name="remarks"></a>Remarks  
 Свойство **CacheSize** используется для управления количеством записей, получаемых за один раз в локальную память от поставщика. Например, если **CacheSize** имеет значение 10, после первого открытия объекта **Recordset** поставщик получает первые 10 записей в локальную память. При перемещении по объекту **Recordset** поставщик возвращает данные из буфера локальной памяти. Как только вы перейдете за последнюю запись в кэше, поставщик извлекает следующие 10 записей из источника данных в кэш.  
  
> [!NOTE]
>  **CacheSize** основан на максимальном свойстве, специфическом для поставщика **открытых строк** (в коллекции **свойств** объекта **Recordset** ). Нельзя задать для **CacheSize** значение, превышающее **Максимальное число открытых строк**. Чтобы изменить количество строк, которые могут быть открыты поставщиком, установите **Максимальное число открытых строк**.  
  
 Значение **CacheSize** можно скорректировать в течение жизненного цикла объекта **Recordset** , но изменение этого значения влияет только на количество записей в кэше после последующих извлечений из источника данных. Изменение только значения свойства не приведет к изменению текущего содержимого кэша.  
  
 Если число записей для получения меньше, чем **CacheSize** , поставщик возвращает оставшиеся записи и не выдает ошибку.  
  
 Нулевой параметр **CacheSize** не допускается и возвращает ошибку.  
  
 Записи, полученные из кэша, не отображают параллельные изменения, внесенные другими пользователями в исходные данные. Чтобы принудительно обновить все кэшированные данные, используйте метод [Resync](../../../ado/reference/ado-api/resync-method.md) .  
  
 Если для **CacheSize** задано значение больше единицы, методы навигации ([Move](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst, MoveLast, MoveNext и MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)) могут привести к перемещению удаленной записи, если удаление происходит после извлечения записей. После первоначальной выборки последующие удаления не будут отражены в кэше данных до тех пор, пока не будет произведена попытка получить доступ к значению данных из удаленной строки. Однако если установить для **CacheSize** значение 1, это не позволит получить доступ к удаленным строкам.  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства CacheSize (Visual Basic)](../../../ado/reference/ado-api/cachesize-property-example-vb.md)   
 [Пример свойства CacheSize (Visual c++)](../../../ado/reference/ado-api/cachesize-property-example-vc.md)   
 [Пример свойства CacheSize (JScript)](../../../ado/reference/ado-api/cachesize-property-example-jscript.md)
