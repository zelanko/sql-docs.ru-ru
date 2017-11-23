---
title: "Кэширование XSL (SQLXML 4.0) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- XSL caching [SQLXML]
ms.assetid: 91994142-32f0-4d8d-a8cf-eb0d8b1f1999
caps.latest.revision: "24"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: aac6234ff9b041839f537bb074dac6ce3dcf0435
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="xsl-caching-sqlxml-40"></a>Кэширование XSL (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Кэширование таблиц стилей XSL повышает производительность. Если кэширование XSL включено, то после первого выполнения таблица стилей XSL остается в памяти. Это повышает производительность последующей обработки. Значение по умолчанию — ON.  
  
 Можно задать размер кэша XSL, добавив в реестр следующий раздел.  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\XSLCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 Размер кэша XSL должен указываться исходя из доступного объема памяти и количества используемых таблиц стилей XSL. По умолчанию значение **XSLCacheSize** равно 31. Размер кэша можно увеличить, если доступ к XSL кажется медленным, или уменьшить при небольшом объеме памяти.  
  
 Чтобы обеспечить наилучшую производительность, рекомендуется указывать значение **XSLCacheSize** , превышающее число обычно используемых таблиц стилей XSL. Если значение **XSLCacheSize** меньше числа имеющихся таблиц стилей XSL, то производительность снижается по мере увеличения количества таблиц стилей XSL. Максимальное значение **XSLCacheSize** — 128.  
  
 При каждом использовании кэшированной таблицы стилей XSL проверяется время изменения файла XSL, чтобы определить необходимость его обновления. Это происходит потому, что копия на диске новее копии в кэше.  
  
## <a name="see-also"></a>См. также:  
 [Кэширование шаблонов &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/template-caching-sqlxml-4-0.md)   
 [Кэширование схем &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)  
  
  
