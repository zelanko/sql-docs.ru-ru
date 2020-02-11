---
title: Персистформатенум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PersistFormatEnum
helpviewer_keywords:
- PersistFormatEnum enumeration [ADO]
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2a26fd370e80cb288ee62b0fc53ed6670300172e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67917615"
---
# <a name="persistformatenum"></a>PersistFormatEnum
Задает формат, в котором сохраняется [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адперсистадтг**|0|Указывает формат Microsoft Advanced Data Таблеграм (АДТГ).|  
|**адперсистадо**|1|Указывает, что будет использоваться собственный формат язык XML ADO (XML). Это значение совпадает с Адперсистксмл и включено для обеспечения обратной совместимости.|  
|**адперсистксмл**|1|Указывает формат язык XML (XML).|  
|**адперсистпровидерспеЦифик**|2|Указывает, что поставщик будет сохранять **набор записей** в собственном формате.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Постоянно|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>Применяется к  
 [Метод Save](../../../ado/reference/ado-api/save-method.md)
