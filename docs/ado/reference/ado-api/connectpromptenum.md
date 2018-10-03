---
title: ConnectPromptEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ConnectPromptEnum
helpviewer_keywords:
- ConnectPromptEnum enumeration [ADO]
ms.assetid: 21026e24-62b7-4cc9-8aef-62c1fc6cba75
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9434c4cc81e8a94e87a3afceedc1b40d5ece2c29
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696903"
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
Указывает, следует ли отображать диалоговое окно запрашивать отсутствуют параметры, при открытии соединения с источником данных.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adPromptAlways**|1|Запросы всегда.|  
|**adPromptComplete**|2|Запрос, если требуются дополнительные сведения.|  
|**adPromptCompleteRequired**|3|Запрашивает, если больше данных, но необязательные параметры не допускаются.|  
|**adPromptNever**|4|Никогда не запрашивает.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.ConnectPrompt.ALWAYS|  
|AdoEnums.ConnectPrompt.COMPLETE|  
|AdoEnums.ConnectPrompt.COMPLETEREQUIRED|  
|AdoEnums.ConnectPrompt.NEVER|  
  
## <a name="applies-to"></a>Объект применения  
 [Свойство Prompt (динамическое) (ADO)](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)
