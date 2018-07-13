---
title: Кэширование схем (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- schemas [SQLXML]
ms.assetid: 7e5fda21-b435-41fd-b637-8b616560a93f
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2bf1398a83badd1ea52fd15484b4e2cda8ec8b8f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37186201"
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
  
  
