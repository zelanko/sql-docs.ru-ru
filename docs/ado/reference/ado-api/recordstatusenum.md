---
title: RecordStatusEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordStatusEnum
helpviewer_keywords:
- RecordStatusEnum enumeration [ADO]
ms.assetid: 506fdd70-4452-4e83-95d5-c94311988dfa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e91f82595c8e4f6fe07969960959a12464bf53a9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47708758"
---
# <a name="recordstatusenum"></a>RecordStatusEnum
Указывает [состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md) записи по отношению к пакетного обновления и других операций массового.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adRecCanceled**|0x100|Указывает, что запись не была сохранена, поскольку операция была отменена.|  
|**adRecCantRelease**|0x400|Указывает, что новая запись не был сохранен, поскольку было заблокировано существующую запись.|  
|**adRecConcurrencyViolation**|0x800|Указывает, что запись не был сохранен, поскольку использовался оптимистичного параллелизма.|  
|**adRecDBDeleted**|0x40000|Указывает, что запись уже была удалена из источника данных.|  
|**adRecDeleted**|0x4|Указывает, что запись была удалена.|  
|**adRecIntegrityViolation**|0x1000|Указывает, что запись не была сохранена, так как он нарушает ограничения целостности.|  
|**adRecInvalid**|0x10|Указывает, что запись не была сохранена, из-за недопустимой ее закладки.|  
|**adRecMaxChangesExceeded**|0x2000|Указывает, что запись не была сохранена, из-за слишком много ожидающих изменений.|  
|**adRecModified**|0x2|Указывает, что запись была изменена.|  
|**adRecMultipleChanges**|0x40|Указывает, что запись не была сохранена, так как затрагивала несколько записей.|  
|**adRecNew**|0x1|Указывает, что запись является новой.|  
|**adRecObjectOpen**|0x4000|Указывает, что запись не была сохранена из-за конфликта с открытый объект хранилища.|  
|**adRecOK**|0|Указывает, что запись успешно обновлена.|  
|**adRecOutOfMemory**|0x8000|Указывает, что запись не была сохранена, поскольку компьютер хватает памяти.|  
|**adRecPendingChanges**|0x80|Указывает, что запись не была сохранена, так как он ссылается на ожидается Вставка.|  
|**adRecPermissionDenied**|0x10000|Указывает, что запись не была сохранена, поскольку у пользователя недостаточно разрешений.|  
|**adRecSchemaViolation**|0x20000|Указывает, что запись не была сохранена, так как он нарушает структуру базы данных.|  
|**adRecUnmodified**|0x8|Указывает, что запись не были изменены.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 AdoEnums.RecordStatus.  
  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.RecordStatus.CANCELED|  
|AdoEnums.RecordStatus.CANTRELEASE|  
|AdoEnums.RecordStatus.CONCURRENCYVIOLATION|  
|AdoEnums.RecordStatus.DBDELETED|  
|AdoEnums.RecordStatus.DELETED|  
|AdoEnums.RecordStatus.INTEGRITYVIOLATION|  
|AdoEnums.RecordStatus.INVALID|  
|AdoEnums.RecordStatus.MAXCHANGESEXCEEDED|  
|AdoEnums.RecordStatus.MODIFIED|  
|AdoEnums.RecordStatus.MULTIPLECHANGES|  
|AdoEnums.RecordStatus.NEW|  
|AdoEnums.RecordStatus.OBJECTOPEN|  
|AdoEnums.RecordStatus.OK|  
|AdoEnums.RecordStatus.OUTOFMEMORY|  
|AdoEnums.RecordStatus.PENDINGCHANGES|  
|AdoEnums.RecordStatus.PERMISSIONDENIED|  
|AdoEnums.RecordStatus.SCHEMAVIOLATION|  
|AdoEnums.RecordStatus.UNMODIFIED|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство Status (объект Recordset ADO)](../../../ado/reference/ado-api/status-property-ado-recordset.md)
