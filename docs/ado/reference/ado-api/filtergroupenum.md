---
title: FilterGroupEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FilterGroupEnum
helpviewer_keywords:
- FilterGroupEnum enumeration [ADO]
ms.assetid: b22e725e-84bd-4286-a070-290c278c3783
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 89cab313736a8d5acf2f7796ea79fb5649f85ab2
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52525873"
---
# <a name="filtergroupenum"></a>FilterGroupEnum
Указывает группу записей, которые будут отфильтрованы из [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|Фильтры для просмотра только записей, затронутых последней [удалить](../../../ado/reference/ado-api/delete-method-ado-recordset.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) вызова.|  
|**adFilterConflictingRecords**|5|Фильтры для просмотра записей, которые не удалось последнего пакета обновления.|  
|**adFilterFetchedRecords**|3|Фильтры для просмотра записей в текущем кэше — то есть результаты последнего вызова метода для извлечения записей из базы данных.|  
|**adFilterNone**|0|Удаляет текущий фильтр и восстанавливает все записи для просмотра.|  
|**adFilterPendingRecords**|1|Фильтры для просмотра только записей, были изменены, но еще не были отправлены на сервер. Применимо только для пакетный режим обновления.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.FilterGroup.AFFECTEDRECORDS|  
|AdoEnums.FilterGroup.CONFLICTINGRECORDS|  
|AdoEnums.FilterGroup.FETCHEDRECORDS|  
|AdoEnums.FilterGroup.NONE|  
|AdoEnums.FilterGroup.PENDINGRECORDS|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство Filter](../../../ado/reference/ado-api/filter-property.md)
