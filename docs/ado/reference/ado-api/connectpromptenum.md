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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: afd5d9ca0de6b8d2ffba75f862e6ca0afb594848
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919443"
---
# <a name="connectpromptenum"></a>ConnectPromptEnum
Указывает, должно ли отображаться диалоговое окно для запроса отсутствующих параметров при открытии соединения с источником данных.  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адпромпталвайс**|1|Всегда запрашивает.|  
|**адпромпткомплете**|2|Запрашивает, требуется ли дополнительная информация.|  
|**адпромпткомплетерекуиред**|3|Запрашивает дополнительные сведения, но необязательные параметры не допускаются.|  
|**адпромптневер**|4|Никогда не запрашивается.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Постоянно|  
|--------------|  
|Адоенумс. Коннектпромпт. ALWAYS|  
|Адоенумс. Коннектпромпт. COMPLETE|  
|Адоенумс. Коннектпромпт. КОМПЛЕТЕРЕКУИРЕД|  
|Адоенумс. Коннектпромпт. NEVER|  
  
## <a name="applies-to"></a>Применяется к  
 [Свойство Prompt (динамическое) (ADO)](../../../ado/reference/ado-api/prompt-property-dynamic-ado.md)
