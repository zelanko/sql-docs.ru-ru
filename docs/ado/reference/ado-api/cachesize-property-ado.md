---
title: Свойство CacheSize (ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::CacheSize
helpviewer_keywords:
- CacheSize property [ADO]
ms.assetid: 49dc9a49-af7b-433b-be36-7a14ca984fb7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a3e27d5ce3302ea6c356ee84b9cc767bbde76c72
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35276163"
---
# <a name="cachesize-property-ado"></a>Свойство CacheSize (ADO)
Указывает количество записей из [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, которые локально кэшируются в памяти.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **длинные** значение, которое должно быть больше 0. По умолчанию — 1.  
  
## <a name="remarks"></a>Примечания  
 Используйте **CacheSize** свойства, сколько записей следует извлекать за один раз в локальную память от поставщика. Например если **CacheSize** равно 10, после первого открытия **записей** объекта, поставщик возвращает первые 10 записей в локальную память. При перемещении по **записей** объекта, поставщик возвращает данные из буфера локальной памяти. После перемещения за последней записью в кэше, поставщик извлекает следующие 10 записей из источника данных в кэш.  
  
> [!NOTE]
>  **CacheSize** на основе **максимальное число открытых строк** свойства поставщика (в **свойства** коллекцию **записей** объекта). Не удается задать **CacheSize** больше, чем значение **максимальное число открытых строк**. Чтобы изменить число строк, которые можно открыть поставщиком, задайте **максимальное число открытых строк**.  
  
 Значение **CacheSize** может настраиваться в течение жизни **записей** объект, но изменить это значение влияет только на число записей в кэше после последующих получений из источника данных. Изменение значения свойства сама по себе не повлияет на текущее содержимое кэша.  
  
 Если меньше записей для извлечения чем **CacheSize** указывает поставщик возвращает оставшиеся записи и ошибка не возникает.  
  
 Объект **CacheSize** значение 0 не разрешается и возвращает сообщение об ошибке.  
  
 Записей, полученных из кэша не отражает параллельных изменений, внесенных другими пользователями в исходных данных. Чтобы принудительно обновить кэшированные данные, используйте [Resync](../../../ado/reference/ado-api/resync-method.md) метод.  
  
 Если **CacheSize** задано значение больше одной, методы навигации ([переместить](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst, MoveLast, MoveNext и MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)) может привести к переходу для удалена запись, если происходит удаление после записи были получены. После первоначальной fetch последующих операций удаления не отразится в кэше данных до попытки получить доступ к значению данных из удаленной строки. Однако задание **CacheSize** одно устраняет эту проблему, так как удаленные строки не могут быть выбраны.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства CacheSize (Visual Basic)](../../../ado/reference/ado-api/cachesize-property-example-vb.md)   
 [Пример свойства CacheSize (VC ++)](../../../ado/reference/ado-api/cachesize-property-example-vc.md)   
 [Пример свойства CacheSize (JScript)](../../../ado/reference/ado-api/cachesize-property-example-jscript.md)
