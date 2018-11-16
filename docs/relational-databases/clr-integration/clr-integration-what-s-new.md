---
title: Что&#39;возможности в интеграции со средой CLR | Документация Майкрософт
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: clr
ms.topic: conceptual
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 09cce119f74bcdf858887078c0a78046dedde7d2
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51677983"
---
# <a name="clr-integration---what39s-new"></a>Интеграция со средой CLR - что&#39;новые
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Ниже перечислены новые функции интеграции со средой CLR в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
-   В версии 4 среды CLR объекты базы данных среды CLR больше не перехватывают исключения состояния повреждения. Теперь эти исключения перехватываются на уровне интеграции со средой CLR. Эти исключения можно по-прежнему перехватываться компоненты базы данных среды CLR, задав для атрибута code ([\<legacyCorruptedStateExceptionsPolicy > элемент](https://go.microsoft.com/fwlink/?LinkId=204954)). Тем не менее делать это не рекомендуется, поскольку при возникновении исключения состояния повреждения добиться хороших результатов невозможно.  
  
-   В соответствии с требованиями строгой безопасности [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], компоненты базы данных среды CLR продолжат использовать модель управления доступом для кода, определенную в среде CLR версии 2.0.  
  
-   В среде CLR версии 4 ошибка формата в **System.TimeSpan** создаст значение **System.FormatExceptions**. До выхода версии 4 среды CLR ошибка формата в **System.TimeSpan** значение было пропущено. Приложения базы данных, которые зависят от поведения до версии 4 среды CLR, должны выполняться с уровнем совместимости базы данных (**уровень совместимости ALTER DATABASE**) 100 или ниже. Дополнительные сведения см. в разделе [< TimeSpan_LegacyFormatMode > элемент](https://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   Версия 4 среды CLR поддерживает Юникод 5.1. Операции сортировки с учетом некоторых диакритических знаков и символов будут улучшены. Если приложение использует устаревший порядок сортировки, могут возникнуть проблемы с совместимостью. Чтобы включить устаревший порядок сортировки, уровень совместимости базы данных (**уровень совместимости ALTER DATABASE**) необходимо задать 100 или ниже. Для поддержи этого порядка сортировки [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] установит файл sort00001000.dll в каталог .NET Framework 4 (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Дополнительные сведения см. в разделе [ \<CompatSortNLSVersion > элемент](https://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   Были добавлены следующие столбцы [sys.dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md): **total_processor_time_ms**, **total_allocated_memory_kb**, и **survived_ memory_kb**.  
  
  
