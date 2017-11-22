---
title: "ConnectPromptEnum | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: ConnectPromptEnum
helpviewer_keywords: ConnectPromptEnum enumeration [ADO]
ms.assetid: 21026e24-62b7-4cc9-8aef-62c1fc6cba75
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dbb4f3f854f319d31f91f8e7f0d8a15cf4263495
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
Указывает, следует ли отображать диалоговое окно для запроса отсутствуют параметры при открытии соединения с источником данных.  
  
|Константа|Значение|Description|  
|--------------|-----------|-----------------|  
|**adPromptAlways**|1|Запросы всегда.|  
|**adPromptComplete**|2|Запрос, если требуются дополнительные сведения.|  
|**adPromptCompleteRequired**|3|Запрашивает, если Дополнительные сведения не требуются, но необязательные параметры не допускаются.|  
|**adPromptNever**|4|Никогда не запрашивает.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.ConnectPrompt.ALWAYS|  
|AdoEnums.ConnectPrompt.COMPLETE|  
|AdoEnums.ConnectPrompt.COMPLETEREQUIRED|  
|AdoEnums.ConnectPrompt.NEVER|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство Prompt (динамическое) (ADO)](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)
