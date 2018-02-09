---
title: "Clone-метод (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset20::Clone
- Recordset20::raw_Clone
helpviewer_keywords:
- Clone method [ADO]
ms.assetid: ad49265f-1c05-4271-9bbf-7c00010ac18c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: db5785a40527f4f85558961068d2cb67eeabbfbc
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="clone-method-ado"></a>Метод clone (ADO)
Создает дубликат [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта из существующего **записей** объекта. При необходимости указывает точную копию только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set rstDuplicate = rstOriginal.Clone (LockType)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **записей** ссылку на объект.  
  
#### <a name="parameters"></a>Параметры  
 *rstDuplicate*  
 Объектную переменную, которая идентифицирует дубликаты **записей** создаваемого объекта.  
  
 *rstOriginal*  
 Объектную переменную, которая идентифицирует **записей** объекта к дублированию.  
  
 *LockType*  
 Необязательно. Объект [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) значение, указывающее тип блокировки исходного **записей**, или только для чтения **записей**. Допустимые значения: **adLockUnspecified** или **adLockReadOnly**.  
  
## <a name="remarks"></a>Remarks  
 Используйте **клон** повторяющийся метод, чтобы создать несколько **записей** объектов, особенно в том случае, если вы хотите поддерживать более чем одна текущая запись в заданном наборе записей. С помощью **клон** метод является более эффективным, чем создание и открытие нового **записей** объект, который использует то же определение оригинала.  
  
 [Фильтра](../../../ado/reference/ado-api/filter-property.md) свойства исходного **записей**, если таковая имеется, не будет применяться клон. Задать **фильтра** нового **записей** для фильтрации результатов. Самый простой способ скопировать все существующие **фильтра** значения — присвоить это напрямую, как показано ниже.  
  
```  
rsNew.Filter = rsOriginal.Filter  
```  
  
 Текущая запись вновь созданный клон устанавливается на первую запись.  
  
 Изменения, вносимые в один **записей** объект видны во всех его клонов независимо от типа курсора. Однако после выполнения [Requery](../../../ado/reference/ado-api/requery-method.md) на исходном **записей**, клонов больше не будут синхронизированы с исходным.  
  
 Закрытие исходного **записей** не закрывает ее копии также не закрывает копии закройте исходные или любой из других копий.  
  
 Можно клонировать только **записей** объект, который поддерживает закладки. Закладка значения являются взаимозаменяемыми; то есть закладки ссылку из одного **записей** относится к одной и той же записи в одном из его клонов.  
  
 Некоторые **записей** события, запущенные также может возникнуть во всех **записей** клонов. Тем не менее, так как текущей записи могут различаться между клонировать **наборы записей**, события могут не подходить для клона. Например, если изменить значение поля [WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md) событие происходит в измененные **записей** и всех клонов. *Поля* параметр **WillChangeField** событий клонированного **записей** (где не изменения) будет ссылаться на поля текущей записи клона что может быть другой записи, чем текущая запись исходного **записей** где произошло изменение.  
  
 Следующая таблица содержит полный список всех **записей** события. Он указывает ли они допустимые и триггеру любой клонов набора записей, созданный с помощью **клон** метод.  
  
|Событие|Запускаются в клоны?|  
|-----------|--------------------------|  
|[EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|нет|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|нет|  
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|нет|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Да|  
|[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|нет|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Да|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|нет|  
|[WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Да|  
|[WillChangeRecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Да|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|нет|  
|[WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|нет|  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода клона (Visual Basic)](../../../ado/reference/ado-api/clone-method-example-vb.md)   
 [Пример метода клона (VBScript)](../../../ado/reference/ado-api/clone-method-example-vbscript.md)   
 [Пример метода Clone (Visual C++)](../../../ado/reference/ado-api/clone-method-example-vc.md)   
