---
title: "CursorOptionEnum | Документы Microsoft"
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
- CursorOptionEnum
helpviewer_keywords:
- CursorOptionEnum enumeration [ADO]
ms.assetid: 4e10cda7-ce81-4466-94c2-844d38191cf1
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 93999724b38f670f8462ae62c9052b10028bf929
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="cursoroptionenum"></a>CursorOptionEnum
Указывает, какие функции [поддерживает](../../../ado/reference/ado-api/supports-method.md) метода следует проверить.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adAddNew**|0x1000400|Поддерживает [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) метод, чтобы добавить новые записи.|  
|**adApproxPosition**|0x4000|Поддерживает [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) и [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) свойства.|  
|**adBookmark**|0x2000|Поддерживает [закладки](../../../ado/reference/ado-api/bookmark-property-ado.md) свойство для доступа к определенной записи.|  
|**adDelete**|0x1000800|Поддерживает [удалить](../../../ado/reference/ado-api/delete-method-ado-recordset.md) метод для удаления записей.|  
|**adFind**|0x80000|Поддерживает [найти](../../../ado/reference/ado-api/find-method-ado.md) метод для поиска строки в [записей](../../../ado/reference/ado-api/recordset-object-ado.md).|  
|**adHoldRecords**|0x100|Извлекает дополнительные записи или изменяет следующей позиции без фиксации все ожидающие изменения.|  
|**adIndex**|0x100000|Поддерживает [индекс](../../../ado/reference/ado-api/index-property.md) свойство имя индекса.|  
|**adMovePrevious**|0x200|Поддерживает [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) и [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) методов, и [переместить](../../../ado/reference/ado-api/move-method-ado.md) или [GetRows](../../../ado/reference/ado-api/getrows-method-ado.md) методов для перемещения к текущей записи позиции назад без использования закладок.|  
|**adNotify**|0x40000|Указывает, что базовый поставщик данных поддерживает уведомления (который определяет ли **записей** события поддерживаются).|  
|**adResync**|0x20000|Поддерживает [Resync](../../../ado/reference/ado-api/resync-method.md) метод обновления курсора с данными, которое видимо в основной базе данных.|  
|**adSeek**|0x200000|Поддерживает [Seek](../../../ado/reference/ado-api/seek-method.md) метод для поиска строки в **записей**.|  
|**adUpdate**|0x1008000|Поддерживает [обновление](../../../ado/reference/ado-api/update-method.md) метод для изменения существующих данных.|  
|**adUpdateBatch**|0x10000|Поддерживает обновление пакета ([UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) и [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) методы) для передачи групп изменение поставщика.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.CursorOption.ADDNEW|  
|AdoEnums.CursorOption.APPROXPOSITION|  
|AdoEnums.CursorOption.BOOKMARK|  
|AdoEnums.CursorOption.DELETE|  
|AdoEnums.CursorOption.FIND|  
|AdoEnums.CursorOption.HOLDRECORDS|  
|AdoEnums.CursorOption.INDEX|  
|AdoEnums.CursorOption.MOVEPREVIOUS|  
|AdoEnums.CursorOption.NOTIFY|  
|AdoEnums.CursorOption.RESYNC|  
|AdoEnums.CursorOption.SEEK|  
|AdoEnums.CursorOption.UPDATE|  
|AdoEnums.CursorOption.UPDATEBATCH|  
  
## <a name="applies-to"></a>Объект применения  
 [Метод Supports](../../../ado/reference/ado-api/supports-method.md)
