---
title: Коннектпромптенум | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 61a66866f8206f2df4cbdeb3f2144e0ac12ac695
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762595"
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
Указывает, должно ли отображаться диалоговое окно для запроса отсутствующих параметров при открытии соединения с источником данных.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**адпромпталвайс**|1|Всегда запрашивает.|  
|**adPromptComplete**|2|Запрашивает, требуется ли дополнительная информация.|  
|**adPromptCompleteRequired**|3|Запрашивает дополнительные сведения, но необязательные параметры не допускаются.|  
|**adPromptNever**|4|Никогда не запрашивается.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. Коннектпромпт. ALWAYS|  
|Адоенумс. Коннектпромпт. COMPLETE|  
|Адоенумс. Коннектпромпт. КОМПЛЕТЕРЕКУИРЕД|  
|Адоенумс. Коннектпромпт. NEVER|  
  
## <a name="applies-to"></a>Применяется к  
 [Свойство Prompt (динамическое) (ADO)](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)
