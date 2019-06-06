---
title: Пример свойства CacheSize (ADO) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f5824141f57838f676b2e1af3e3e9c4f3041648b
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718095"
---
# <a name="cachesize-property-ado"></a>Свойство CacheSize (ADO)
Указывает количество записей из [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, которые локально кэшируются в памяти.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **Long** значение, которое должно быть больше 0. По умолчанию — 1.  
  
## <a name="remarks"></a>Примечания  
 Используйте **CacheSize** свойства для управления, сколько записей следует извлечь за один раз в локальную память от поставщика. Например если **CacheSize** — 10, после первого открытия **записей** объекта, поставщик извлекает первые 10 записей в локальной памяти. По мере продвижения по **записей** объекта, поставщик возвращает данные из локальной памяти буфера. После перемещения за последней записью в кэше, поставщик извлекает следующие 10 записей из источника данных в кэш.  
  
> [!NOTE]
>  **CacheSize** основан на **максимальное число открытых строк** свойства поставщика (в **свойства** коллекцию **записей** объекта). Невозможно задать **CacheSize** больше, чем значение **максимальное число открытых строк**. Чтобы изменить число строк, которые можно открыть поставщиком, задайте **максимальное число открытых строк**.  
  
 Значение **CacheSize** может корректироваться в течение жизненного цикла **записей** объект, но изменить это значение влияет только на число записей в кэше после последующих получений из источника данных. Изменение только значение свойства не повлияет на текущее содержимое кэша.  
  
 При наличии меньшего числа записей для извлечения чем **CacheSize** указывает, поставщик возвращает оставшиеся записи и ошибка не возникает.  
  
 Объект **CacheSize** не допускается значение 0 и возвращает сообщение об ошибке.  
  
 Записей, полученных из кэша не отражает параллельные изменения, внесенные другими пользователями в исходных данных. Чтобы выполнить принудительное обновление всех кэшированных данных, используйте [Resync](../../../ado/reference/ado-api/resync-method.md) метод.  
  
 Если **CacheSize** присваивается значение больше единицы, методы навигации ([переместить](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst, MoveLast, MoveNext и MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)) может привести к переход к удалена запись, если удаление происходит после записи были получены. После первоначальной выборки последующих операций удаления не отражаются в кэше данных до попытки получить доступ к значению данных из удаленной строки. Однако можно присвоить **CacheSize** к одному устраняет эту проблему, так как удаленные строки не могут быть выбраны.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства CacheSize (Visual Basic)](../../../ado/reference/ado-api/cachesize-property-example-vb.md)   
 [Пример свойства CacheSize (Visual C++)](../../../ado/reference/ado-api/cachesize-property-example-vc.md)   
 [Пример свойства CacheSize (JScript)](../../../ado/reference/ado-api/cachesize-property-example-jscript.md)
