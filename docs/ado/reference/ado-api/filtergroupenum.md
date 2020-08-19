---
description: FilterGroupEnum
title: Филтерграупенум | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: f8d3c510cfd9fa6c4a28f78005021465b9b0917b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443666"
---
# <a name="filtergroupenum"></a>FilterGroupEnum
Указывает группу записей для фильтрации из [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|Фильтры для просмотра только тех записей, на которые повлияли последние операции [удаления](../../../ado/reference/ado-api/delete-method-ado-recordset.md), повторной [синхронизации](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) .|  
|**адфилтерконфликтингрекордс**|5|Фильтры для просмотра записей, которые не прошли Последнее обновление пакета.|  
|**adFilterFetchedRecords**|3|Фильтры для просмотра записей в текущем кэше, то есть результатов последнего вызова для получения записей из базы данных.|  
|**адфилтерноне**|0|Удаляет текущий фильтр и восстанавливает все записи для просмотра.|  
|**адфилтерпендингрекордс**|1|Фильтры для просмотра только тех записей, которые были изменены, но еще не отправлены на сервер. Применяется только для режима пакетного обновления.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. Филтерграуп. АФФЕКТЕДРЕКОРДС|  
|Адоенумс. Филтерграуп. КОНФЛИКТИНГРЕКОРДС|  
|Адоенумс. Филтерграуп. ФЕТЧЕДРЕКОРДС|  
|Адоенумс. Филтерграуп. NONE|  
|Адоенумс. Филтерграуп. ПЕНДИНГРЕКОРДС|  
  
## <a name="applies-to"></a>Применение  
 [Свойство Filter](../../../ado/reference/ado-api/filter-property.md)
