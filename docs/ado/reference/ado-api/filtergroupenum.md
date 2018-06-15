---
title: FilterGroupEnum | Документы Microsoft
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
- FilterGroupEnum
helpviewer_keywords:
- FilterGroupEnum enumeration [ADO]
ms.assetid: b22e725e-84bd-4286-a070-290c278c3783
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dd0af463cf9ebc5bad28665cad32fc49fce5fb5b
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278653"
---
# <a name="filtergroupenum"></a>FilterGroupEnum
Указывает группу записей, которые будут отфильтрованы из [записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|Фильтры для просмотра только записей, затронутых последней [удаление](../../../ado/reference/ado-api/delete-method-ado-recordset.md), [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) вызова.|  
|**adFilterConflictingRecords**|5|Фильтры для просмотра записей, прошедших с последнего пакета обновления.|  
|**adFilterFetchedRecords**|3|Фильтры для просмотра записей в текущем кэше — то есть, результаты последнего вызова для получения записей из базы данных.|  
|**adFilterNone**|0|Удаляет текущий фильтр и восстанавливает все записи для просмотра.|  
|**adFilterPendingRecords**|1|Фильтры для просмотра только записей, были изменены, но еще не отправлены на сервер. Применимо только для режима обновления пакета.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
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
