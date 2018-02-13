---
title: "Кэширование шаблонов (SQLXML 4.0) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- templates [SQLXML], caching
ms.assetid: 73e151c6-b24e-4422-a116-51e0846bc6f5
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 079817f1179d9fca165366fd67b3d4ab79adc01e
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="template-caching-sqlxml-40"></a>Кэширование шаблонов (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Кэширование шаблонов значительно повышает производительность. Если установлено кэширование шаблонов, при первом выполнении шаблон располагается в памяти. Это повышает производительность последующего выполнения шаблона.  
  
 Размер кэша шаблонов можно задать, добавив в реестр следующий ключ:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 Размер кэша необходимо указывать, исходя из объема доступной памяти и количества используемых шаблонов. Значение по умолчанию для **TemplateCacheSize** равно 31. Размер кэша можно увеличить, если доступ к шаблону кажется медленным, или уменьшить при небольшом объеме памяти.  
  
 Для повышения производительности рекомендуется установить **TemplateCacheSize** превышающее число обычно используемых шаблонов. Если **TemlateCacheSize** меньше, чем число имеющихся шаблонов, производительность снижается по мере число шаблонов. **TemplateCacheSize** можно задать не более чем 128.  
  
 При каждом использовании кэшированного шаблона проверяется время изменения файла шаблона, чтобы при необходимости его обновить. Это происходит потому, что копия на диске новее копии в кэше.  
  
> [!NOTE]  
>  Параметры шаблона и свойства команд не кэшируются.  
  
## <a name="see-also"></a>См. также:  
 [Кэширование схем &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)   
 [Кэширование XSL &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
  
  
