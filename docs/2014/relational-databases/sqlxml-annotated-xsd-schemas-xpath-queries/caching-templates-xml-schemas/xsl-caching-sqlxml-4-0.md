---
title: Кэширование XSL (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- XSL caching [SQLXML]
ms.assetid: 91994142-32f0-4d8d-a8cf-eb0d8b1f1999
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ff1d92a054d85c52e5b69044a2c25da31eb35705
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48166734"
---
# <a name="xsl-caching-sqlxml-40"></a>Кэширование XSL (SQLXML 4.0)
  Кэширование таблиц стилей XSL повышает производительность. Если кэширование XSL включено, то после первого выполнения таблица стилей XSL остается в памяти. Это повышает производительность последующей обработки. Значение по умолчанию — ON.  
  
 Можно задать размер кэша XSL, добавив в реестр следующий раздел.  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\XSLCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 Размер кэша XSL должен указываться исходя из доступного объема памяти и количества используемых таблиц стилей XSL. По умолчанию значение **XSLCacheSize** равно 31. Размер кэша можно увеличить, если доступ к XSL кажется медленным, или уменьшить при небольшом объеме памяти.  
  
 Чтобы обеспечить наилучшую производительность, рекомендуется указывать значение **XSLCacheSize** , превышающее число обычно используемых таблиц стилей XSL. Если значение **XSLCacheSize** меньше числа имеющихся таблиц стилей XSL, то производительность снижается по мере увеличения количества таблиц стилей XSL. Максимальное значение **XSLCacheSize** — 128.  
  
 При каждом использовании кэшированной таблицы стилей XSL проверяется время изменения файла XSL, чтобы определить необходимость его обновления. Это происходит потому, что копия на диске новее копии в кэше.  
  
## <a name="see-also"></a>См. также  
 [Кэширование шаблонов &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md)   
 [Кэширование схем &#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md)  
  
  
