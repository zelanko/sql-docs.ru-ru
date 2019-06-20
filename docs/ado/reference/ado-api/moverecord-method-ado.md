---
title: Метод MoveRecord (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::MoveRecord
- _Record::raw_MoveRecord
helpviewer_keywords:
- MoveRecord method [ADO]
ms.assetid: 6d2807b0-b861-4583-bcaf-fb0b82e0f2d0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: fe9dc770f537b9b9f8b53461c30b890a4144a821
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66707348"
---
# <a name="moverecord-method-ado"></a>Метод MoveRecord (ADO)
Перемещает сущности, представленной [записи](../../../ado/reference/ado-api/record-object-ado.md) в другое расположение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Record.MoveRecord (Source, Destination, UserName, Password, Options, Async)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Source*  
 Необязательный параметр. Объект **строка** значение, содержащее URL-адрес определения **записи** для перемещения. Если *источника* опущен или указывает пустую строку, объект, представленный этим объектом **записи** перемещается. Например если **записи** представляет файл, содержимое файла перемещаются в расположении, заданном параметром *назначения*.  
  
 *Назначение*  
 Необязательный. Объект **строка** значение, содержащее URL-адрес, указывающий местоположение где *источника* будет перемещен.  
  
 *UserName*  
 Необязательный. Объект **строка** значение, содержащее идентификатор пользователя, при необходимости, разрешает доступ к *назначения*.  
  
 *Пароль*  
 Необязательный параметр. Объект **строка** , содержащая пароль, который при необходимости, проверяет ли *UserName*.  
  
 *Параметры*  
 Необязательный параметр. Объект [MoveRecordOptionsEnum](../../../ado/reference/ado-api/moverecordoptionsenum.md) значение, значение которого по умолчанию равно **adMoveUnspecified**. Задает поведение этого метода.  
  
 *Async*  
 Необязательный. Объект **логическое** значением, которое при **True**, указывает, эта операция должна выполняться асинхронно.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **String**. Как правило, значение *назначения* возвращается. Тем не менее возвращаемое точное значение зависит от поставщика.  
  
## <a name="remarks"></a>Примечания  
 Значения *источника* и *назначения* не должно быть идентичны; в противном случае возникает ошибка времени выполнения. По крайней мере имена сервера, путь и ресурсов должны отличаться.  
  
 Для файлов, перенесена с использованием поставщика Интернет-публикаций, этот метод обновляет все гипертекстовых ссылок в файлах, перемещаемый в случае, если не указано иначе *параметры*. Этот метод завершается ошибкой, если *назначения* определяет существующий объект (например, файл или каталог), если не **adMoveOverWrite** указан.  
  
> [!NOTE]
>  Используйте **adMoveOverWrite** параметр осмотрительно. Например задание этого параметра, при перемещении файла в каталог будет удалите каталог и замените файл.  
  
 Некоторые атрибуты элемента **записи** объект, например [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md) свойство, не будет обновляться, после завершения этой операции. Обновить **записи** свойств объекта, закрывая **записи**, а затем повторно открыть его URL-адрес расположения, где был перемещен файл или каталог.  
  
 Если этот **записи** были получены из [записей](../../../ado/reference/ado-api/recordset-object-ado.md), новое расположение перемещенного файла или каталога не будут отражены немедленно, в **записей**. Обновить **записей** , закройте и повторно откройте его.  
  
> [!NOTE]
>  URL-адреса, с использованием схемы http, автоматически вызывает метод [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Метод Move (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [Примеры MoveFirst, MoveLast, MoveNext и MovePrevious методы (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [Методы MoveFirst, MoveLast, MoveNext и MovePrevious (служба удаленных рабочих столов)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)
