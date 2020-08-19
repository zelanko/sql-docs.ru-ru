---
description: SeekEnum
title: Сикенум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SeekEnum
helpviewer_keywords:
- SeekEnum enumeration [ADO]
ms.assetid: f0ec0c92-8253-47c6-9a14-e5dbccbad219
author: rothja
ms.author: jroth
ms.openlocfilehash: 1bea36687e0fbe8aea4768386f4435ceece621bb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442116"
---
# <a name="seekenum"></a>SeekEnum
Указывает тип выполняемого [поиска](../../../ado/reference/ado-api/seek-method.md) .  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**adSeekFirstEQ**|1|Ищет первый ключ, равный *кэйвалуес*.|  
|**адсикластек**|2|Ищет последний ключ, равный *кэйвалуес*.|  
|**адсикафтерек**|4|Ищет либо ключ, равный *кэйвалуес* , либо сразу после того, как было выполнено совпадение.|  
|**adSeekAfter**|8|Ищет ключ сразу после того, как произошло совпадение с *кэйвалуес* .|  
|**adSeekBeforeEQ**|16|Поиск либо ключа, равного *кэйвалуес*, либо непосредственно перед тем, как было выполнено совпадение.|  
|**adSeekBefore**|32|Ищет ключ непосредственно перед тем, как произошло совпадение с *кэйвалуес* .|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. Seek. ФИРСТЕК|  
|Адоенумс. Seek. ЛАСТЕК|  
|Адоенумс. Seek. АФТЕРЕК|  
|Адоенумс. Seek. После|  
|Адоенумс. Seek. БЕФОРИК|  
|Адоенумс. Seek. до|  
  
## <a name="applies-to"></a>Применение  
 [Seek, метод](../../../ado/reference/ado-api/seek-method.md)
