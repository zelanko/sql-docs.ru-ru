---
title: Кэширование шаблонов (SQLXML)
description: Узнайте, как значительно повысить производительность при выполнении шаблонов с помощью кэширования шаблонов в SQLXML 4,0.
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- templates [SQLXML], caching
ms.assetid: 73e151c6-b24e-4422-a116-51e0846bc6f5
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5b8bb4225d5c977cb516de8a17037c92e22658b4
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97479315"
---
# <a name="template-caching-sqlxml-40"></a>Кэширование шаблонов (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Кэширование шаблонов значительно повышает производительность. Если установлено кэширование шаблонов, при первом выполнении шаблон располагается в памяти. Это повышает производительность последующего выполнения шаблона.  
  
 Размер кэша шаблонов можно задать, добавив в реестр следующий ключ:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 Размер кэша необходимо указывать, исходя из объема доступной памяти и количества используемых шаблонов. По умолчанию размер **темплатекачесизе** равен 31. Размер кэша можно увеличить, если доступ к шаблону кажется медленным, или уменьшить при небольшом объеме памяти.  
  
 Для повышения производительности рекомендуется задать **темплатекачесизе** выше, чем количество шаблонов, которые обычно используются. Если **темлатекачесизе** меньше числа шаблонов, производительность снижается по мере увеличения количества шаблонов. Для **темплатекачесизе** можно задать не более 128.  
  
 При каждом использовании кэшированного шаблона проверяется время изменения файла шаблона, чтобы при необходимости его обновить. Это происходит потому, что копия на диске новее копии в кэше.  
  
> [!NOTE]  
>  Параметры шаблона и свойства команд не кэшируются.  
  
## <a name="see-also"></a>См. также:  
 [Кэширование схемы &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)   
 [Кэширование XSL &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
  
  
