---
title: Кэширование схем (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- schemas [SQLXML]
ms.assetid: 7e5fda21-b435-41fd-b637-8b616560a93f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2a9b4eced3cb4e02e2053a90edd701bda3139358
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52793636"
---
# <a name="schema-caching-sqlxml-40"></a>Кэширование схем (SQLXML 4.0)
  При установке side-by-side XML для Microsoft SQL Server 2000 Web Release 1, Microsoft SQLXML 2.0 и SQLXML 3.0 можно явно управлять схемы, кэширование во всех версиях ОС, используя следующие разделы реестра:  
  
 Web Release 1.  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXMLX\SchemaCacheSize  
```  
  
 SQLXML 2.0:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML2\SchemaCacheSize  
```  
  
 SQLXML 3.0:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML3\SchemaCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 Дополнительные сведения об установке side-by-side см. в разделе [новые возможности в SQLXML 4.0 с пакетом обновления 1](../../sqlxml/what-s-new-in-sqlxml-4-0-sp1.md).  
  
 Кэширование схем значительно повышает производительность запроса XPath. При выполнении запроса XPath к схеме сопоставления эта схема хранится в памяти, и необходимые структуры данных строятся в памяти. Если задано кэширование схем, то схема остается в памяти, тем самым повышая производительность последующих запросов XPath.  
  
 Размер кэша для схем можно задать, добавив в реестр указанный выше раздел.  
  
 Размер схемы устанавливается в зависимости от доступной памяти и количества используемых схем. Значение по умолчанию **SchemaCacheSize** равно 31. Если задать **SchemaCacheSize** более поздней версии, используется больше памяти. Поэтому можно увеличить размер кэша, если доступ к схеме происходит медленно, и уменьшить его при нехватке памяти.  
  
 Из соображений производительности рекомендуется установить **SchemaCacheSize** выше, чем количество обычно используемых схем сопоставления. Как увеличить количество схем, если **SchemaCacheSize** меньше, чем количество схем, у вас есть, то производительность снижается.  
  
> [!NOTE]  
>  Не рекомендуется кэшировать схемы во время разработки программ, поскольку изменения, вносимые в схемы, отражаются в кэше примерно через две минуты.  
  
## <a name="see-also"></a>См. также  
 [Кэширование шаблонов &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md)   
 [Кэширование XSL &#40;SQLXML 4.0&#41;](xsl-caching-sqlxml-4-0.md)  
  
  
