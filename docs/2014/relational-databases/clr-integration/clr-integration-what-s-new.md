---
title: Что&#39;возможности в интеграции со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 45e4f0578d06eeafc545bea2b6374a37b8ef7cbc
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53350979"
---
# <a name="what39s-new-in-clr-integration"></a>Что&#39;возможности в интеграции со средой CLR
  Ниже перечислены новые функции интеграции со средой CLR в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
-   В версии 4 среды CLR объекты базы данных среды CLR больше не перехватывают исключения состояния повреждения. Теперь эти исключения перехватываются на уровне интеграции со средой CLR. Эти исключения можно по-прежнему перехватываться компоненты базы данных среды CLR, задав для атрибута code ([\<legacyCorruptedStateExceptionsPolicy > элемент](https://go.microsoft.com/fwlink/?LinkId=204954)). Тем не менее делать это не рекомендуется, поскольку при возникновении исключения состояния повреждения добиться хороших результатов невозможно.  
  
-   В соответствии с требованиями строгой безопасности [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], компоненты базы данных среды CLR продолжат использовать модель управления доступом для кода, определенную в среде CLR версии 2.0.  
  
-   В среде CLR версии 4 ошибка формата в значении `System.TimeSpan` формирует исключение `System.FormatExceptions`. До выхода версии 4 среды CLR ошибка формата в значении `System.TimeSpan` не обрабатывалась. Приложения баз данных, которые зависят от поведения, характерного для среды CLR версии ниже 4, должны выполняться с уровнем совместимости базы данных (`ALTER DATABASE Compatibility Level`) 100 или ниже. Дополнительные сведения см. в разделе [< TimeSpan_LegacyFormatMode > элемент](https://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   Версия 4 среды CLR поддерживает Юникод 5.1. Операции сортировки с учетом некоторых диакритических знаков и символов будут улучшены. Если приложение использует устаревший порядок сортировки, могут возникнуть проблемы с совместимостью. Чтобы включить устаревший порядок сортировки, необходимо установить уровень совместимости базы данных (`ALTER DATABASE Compatibility Level`) 100 или ниже. Для поддержи этого порядка сортировки [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] установит файл sort00001000.dll в каталог .NET Framework 4 (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Дополнительные сведения см. в разделе [ \<CompatSortNLSVersion > элемент](https://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   Были добавлены следующие столбцы [sys.dm_clr_appdomains](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql): `total_processor_time_ms`, `total_allocated_memory_kb`, и `survived_memory_kb`.  
  
  
