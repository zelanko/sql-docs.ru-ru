---
title: Кэширование схем (SQLXML 4,0) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ca536125be481766e41c3665dd313d483160ae0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66013278"
---
# <a name="schema-caching-sqlxml-40"></a>Кэширование схем (SQLXML 4.0)
  При параллельной установке XML для Microsoft SQL Server 2000 Web Release 1, Microsoft SQLXML 2.0 и SQLXML 3.0 можно в явном виде контролировать кэширование схем всех версий с помощью следующих разделов реестра.  
  
 Web Release 1.  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXMLX\SchemaCacheSize  
```  
  
 SQLXML 2,0:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML2\SchemaCacheSize  
```  
  
 SQLXML 3.0:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML3\SchemaCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 Дополнительные сведения о параллельной установке см. [в статье новые возможности SQLXML 4,0 с пакетом обновления 1 (SP1)](../../sqlxml/what-s-new-in-sqlxml-4-0-sp1.md).  
  
 Кэширование схем значительно повышает производительность запроса XPath. При выполнении запроса XPath к схеме сопоставления эта схема хранится в памяти, и необходимые структуры данных строятся в памяти. Если задано кэширование схем, то схема остается в памяти, тем самым повышая производительность последующих запросов XPath.  
  
 Размер кэша для схем можно задать, добавив в реестр указанный выше раздел.  
  
 Размер схемы устанавливается в зависимости от доступной памяти и количества используемых схем. Размер **счемакачесизе** по умолчанию — 31. Если задать **счемакачесизе** выше, будет использоваться больше памяти. Поэтому можно увеличить размер кэша, если доступ к схеме происходит медленно, и уменьшить его при нехватке памяти.  
  
 По соображениям производительности рекомендуется задавать **счемакачесизе** выше числа используемых схем сопоставления. При увеличении числа схем, если **счемакачесизе** меньше числа схем, производительность снижается.  
  
> [!NOTE]  
>  Не рекомендуется кэшировать схемы во время разработки программ, поскольку изменения, вносимые в схемы, отражаются в кэше примерно через две минуты.  
  
## <a name="see-also"></a>См. также:  
 [Кэширование шаблонов &#40;SQLXML 4,0&#41;](template-caching-sqlxml-4-0.md)   
 [Кэширование XSL &#40;SQLXML 4,0&#41;](xsl-caching-sqlxml-4-0.md)  
  
  
