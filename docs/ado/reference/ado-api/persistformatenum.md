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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917615"
---
# <a name="persistformatenum"></a>PersistFormatEnum
Задает формат, в котором сохраняется [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Константа|Применение|Описание|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Указывает формат Microsoft Advanced Data Таблеграм (АДТГ).|  
|**adPersistADO**|1|Указывает, что будет использоваться собственный формат язык XML ADO (XML). Это значение совпадает с Адперсистксмл и включено для обеспечения обратной совместимости.|  
|**adPersistXML**|1|Указывает формат язык XML (XML).|  
|**adPersistProviderSpecific**|2|Указывает, что поставщик будет сохранять **набор записей** в собственном формате.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>Применяется к  
 [Метод Save](../../../ado/reference/ado-api/save-method.md)
