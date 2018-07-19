---
title: Кэширование шаблонов (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- templates [SQLXML], caching
ms.assetid: 73e151c6-b24e-4422-a116-51e0846bc6f5
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: f4ba78383ac3b0b8b1065ae27aa064a99b3566d9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38050054"
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
  
 Размер кэша необходимо указывать, исходя из объема доступной памяти и количества используемых шаблонов. Значение по умолчанию **TemplateCacheSize** равно 31. Размер кэша можно увеличить, если доступ к шаблону кажется медленным, или уменьшить при небольшом объеме памяти.  
  
 Для повышения производительности рекомендуется установить **TemplateCacheSize** выше, чем количество обычно используемых шаблонов. Если **TemlateCacheSize** меньше, чем число имеющихся шаблонов, производительность снижается по мере число шаблонов. **TemplateCacheSize** можно задать до максимального размера в 128.  
  
 При каждом использовании кэшированного шаблона проверяется время изменения файла шаблона, чтобы при необходимости его обновить. Это происходит потому, что копия на диске новее копии в кэше.  
  
> [!NOTE]  
>  Параметры шаблона и свойства команд не кэшируются.  
  
## <a name="see-also"></a>См. также  
 [Кэширование схем &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)   
 [Кэширование XSL &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
  
  
