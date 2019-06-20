---
title: Метод clone (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::Clone
- Recordset20::raw_Clone
helpviewer_keywords:
- Clone method [ADO]
ms.assetid: ad49265f-1c05-4271-9bbf-7c00010ac18c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: fbeedf9e56c1f0606a7c8f842baedc9d11ad3929
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698793"
---
# <a name="clone-method-ado"></a>Метод Clone (ADO)
Создает дубликат [записей](../../../ado/reference/ado-api/recordset-object-ado.md) из существующего **записей** объекта. При необходимости указывает, что клона быть доступны только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set rstDuplicate = rstOriginal.Clone (LockType)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **записей** ссылка на объект.  
  
#### <a name="parameters"></a>Параметры  
 *rstDuplicate*  
 Объектную переменную, которая идентифицирует дубликат **записей** создаваемого объекта.  
  
 *rstOriginal*  
 Объектную переменную, которая идентифицирует **записей** объекта к дублированию.  
  
 *LockType*  
 Необязательный. Объект [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) значение, указывающее тип блокировки исходного **записей**, или только для чтения **записей**. Допустимые значения: **adLockUnspecified** или **adLockReadOnly**.  
  
## <a name="remarks"></a>Примечания  
 Используйте **клона** повторяющийся метод для создания нескольких **записей** объектов, особенно в том случае, если вы хотите поддерживать более чем одна текущая запись в заданном наборе записей. С помощью **клона** метод является более эффективным, чем создание и открытие нового **записей** объект, который использует то же определение, что и исходный.  
  
 [Фильтра](../../../ado/reference/ado-api/filter-property.md) свойства исходного **записей**, если есть, не будут применяться к клона. Задайте **фильтра** свойства нового **записей** для фильтрации результатов. Самый простой способ скопировать все существующие **фильтра** значение присваивается его напрямую, как показано ниже.  
  
```  
rsNew.Filter = rsOriginal.Filter  
```  
  
 Текущую запись в только что созданный клона имеет значение первой записи.  
  
 Изменения, вносимые на один **записей** объект видны во всех его клонов, вне зависимости от типа курсора. Однако после выполнения [Requery](../../../ado/reference/ado-api/requery-method.md) на исходном **записей**, клонов больше не будут синхронизированы с исходным.  
  
 Закрытие исходного **записей** не закрывает его копии, а также закрытие копию Закройте исходный или любого из этих копий.  
  
 Можно клонировать только **записей** объект, который поддерживает закладки. Закладка значения являются взаимозаменяемыми; то есть ссылку закладку из одного **записей** объект ссылается на одной и той же записи в любой из его клонов.  
  
 Некоторые **записей** события, запущенные также может возникнуть во всех **записей** Клонирует. Тем не менее, так как текущей записи могут различаться в разных клонировать **наборы записей**, события могут оказаться недопустимыми для клона. Например, если изменяется значение поля [события WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md) событие произойдет в измененная **записей** и в все клоны. *Поля* параметр **события WillChangeField** событие клонированный **записей** (где изменение было не сделано) будет ссылаться на поля текущей записи клона, которое может иметь другую запись чем текущей записи исходного **записей** где произошло изменение.  
  
 Следующая таблица содержит полный список всех **записей** события. Указывает, являются ли они допустим и активированных клонов любой набор записей, созданных с помощью **клона** метод.  
  
|Событие|Активировано в клонов?|  
|-----------|--------------------------|  
|[EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|Нет|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|Нет|  
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|Нет|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Да|  
|[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Нет|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Да|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Нет|  
|[WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Да|  
|[WillChangeRecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Да|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Нет|  
|[WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Нет|  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода clone (Visual Basic)](../../../ado/reference/ado-api/clone-method-example-vb.md)   
 [Пример метода clone (VBScript)](../../../ado/reference/ado-api/clone-method-example-vbscript.md)   
 [Пример метода Clone (Visual C++)](../../../ado/reference/ado-api/clone-method-example-vc.md)   
