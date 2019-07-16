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
ms.openlocfilehash: afd5d9ca0de6b8d2ffba75f862e6ca0afb594848
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67919443"
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
