---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97add08a1d656e8c163600bb0ea8dda7fca264b5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67932645"
---
# <a name="filtergroupenum"></a>FilterGroupEnum
Указывает группу записей для фильтрации из [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адфилтераффектедрекордс**|2|Фильтры для просмотра только тех записей, на которые повлияли последние операции [удаления](../../../ado/reference/ado-api/delete-method-ado-recordset.md), повторной [синхронизации](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) .|  
|**адфилтерконфликтингрекордс**|5|Фильтры для просмотра записей, которые не прошли Последнее обновление пакета.|  
|**адфилтерфетчедрекордс**|3|Фильтры для просмотра записей в текущем кэше, то есть результатов последнего вызова для получения записей из базы данных.|  
|**адфилтерноне**|0|Удаляет текущий фильтр и восстанавливает все записи для просмотра.|  
|**адфилтерпендингрекордс**|1|Фильтры для просмотра только тех записей, которые были изменены, но еще не отправлены на сервер. Применяется только для режима пакетного обновления.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Постоянно|  
|--------------|  
|Адоенумс. Филтерграуп. АФФЕКТЕДРЕКОРДС|  
|Адоенумс. Филтерграуп. КОНФЛИКТИНГРЕКОРДС|  
|Адоенумс. Филтерграуп. ФЕТЧЕДРЕКОРДС|  
|Адоенумс. Филтерграуп. NONE|  
|Адоенумс. Филтерграуп. ПЕНДИНГРЕКОРДС|  
  
## <a name="applies-to"></a>Применяется к  
 [Свойство Filter](../../../ado/reference/ado-api/filter-property.md)
