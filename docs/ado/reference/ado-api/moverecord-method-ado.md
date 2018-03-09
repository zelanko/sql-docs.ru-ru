---
title: "Метод MoveRecord (ADO) | Документы Microsoft"
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
- _Record::MoveRecord
- _Record::raw_MoveRecord
helpviewer_keywords:
- MoveRecord method [ADO]
ms.assetid: 6d2807b0-b861-4583-bcaf-fb0b82e0f2d0
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a626e6f86d2e44fed972f8043b556d233fdf1d17
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="moverecord-method-ado"></a>Метод MoveRecord (ADO)
Перемещает сущности, представленной [записи](../../../ado/reference/ado-api/record-object-ado.md) в другое место.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Record.MoveRecord (Source, Destination, UserName, Password, Options, Async)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Необязательно. Объект **строка** значение, содержащее URL-адрес определения **запись** для перемещения. Если *источника* опущен или указывает на пустую строку, объект, представленный этим **записи** перемещается. Например если **запись** представляет файл, содержимое файла перемещаются в расположении, заданном *назначения*.  
  
 *Назначение*  
 Необязательно. Объект **строка** значение, содержащее URL-адрес, указывающий местоположение где *источника* будет перемещен.  
  
 *UserName*  
 Необязательно. Объект **строка** значение, содержащее идентификатор пользователя, при необходимости, дающая право на доступ к *назначения*.  
  
 *Пароль*  
 Необязательно. Объект **строка** , содержащее пароль, при необходимости проверяет *UserName*.  
  
 *Параметры*  
 Необязательно. Объект [MoveRecordOptionsEnum](../../../ado/reference/ado-api/moverecordoptionsenum.md) значение, определяющее по умолчанию **adMoveUnspecified**. Задает поведение данного метода.  
  
 *Async*  
 Необязательно. Объект **логическое** значением, которое при **True**, указывает этой операции должен быть асинхронным.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** значение. Как правило, значение *назначения* возвращается. Тем не менее возвращаемое точное значение зависит от поставщика.  
  
## <a name="remarks"></a>Remarks  
 Значения *источника* и *назначения* не должна одинаковы; в противном случае возникает ошибка времени выполнения. По крайней мере имена сервера, путь и ресурс должны отличаться.  
  
 Для файлов, перемещенных с помощью службу публикации в Интернете, этот метод обновляет все гипертекстовые ссылки в файлах, перемещается в случае, если не указано иначе *параметры*. Этот метод завершается ошибкой, если *назначения* указывает существующий объект (например, файл или каталог), если не **adMoveOverWrite** указано.  
  
> [!NOTE]
>  Используйте **adMoveOverWrite** параметр обдуманно. Например задание этого параметра при перемещении файла в каталог будет удалите каталог и замените файл.  
  
 Некоторые атрибуты **запись** объект, такой как [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md) свойства, не будет обновляться после завершения этой операции. Обновить **запись** свойств объекта, закрывая **записи**, а затем повторно открыть его URL-адрес расположения, где был перемещен в файл или каталог.  
  
 Если этот **запись** была получена с [записей](../../../ado/reference/ado-api/recordset-object-ado.md), новое расположение перемещенного файла или каталога не будут отражены немедленно, в **записей**. Обновить **записей** , закрытия и повторного открытия.  
  
> [!NOTE]
>  URL-адреса, с помощью схемы http автоматически вызывает [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Move-метод (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [MoveFirst, MoveLast, MoveNext и MovePrevious методов (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [Методы MoveFirst, MoveLast, MoveNext и MovePrevious (служба удаленных рабочих столов)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)
