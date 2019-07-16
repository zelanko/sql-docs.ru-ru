---
title: RecordTypeEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordTypeEnum
helpviewer_keywords:
- RecordTypeEnum enumeration [ADO]
ms.assetid: f557e537-015d-4ba7-8a41-a6f00b366a91
author: MightyPen
ms.author: genemi
ms.openlocfilehash: df70838b7986993459df4f37af8b7043626a5d7b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931267"
---
# <a name="recordtypeenum"></a>RecordTypeEnum
Указывает тип [записи](../../../ado/reference/ado-api/record-object-ado.md) объекта.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adSimpleRecord**|0|Указывает *простой* записи (не содержит дочерних узлов).|  
|**adCollectionRecord**|1|Указывает *коллекции* записи (содержит дочерние узлы).|  
|**adRecordUnknown**|-1|Указывает, что тип этого **записи** неизвестно.|  
|**adStructDoc**|2|Указывает специальный вид *коллекции* запись, которая представляет COM структурированных документов.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Эти константы не имеют эквивалентов ADO и WFC.  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство RecordType (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)
