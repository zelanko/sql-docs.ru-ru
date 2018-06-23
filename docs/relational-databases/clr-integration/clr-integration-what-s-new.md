---
title: Что&#39;новые возможности интеграции со средой CLR | Документы Microsoft
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: reference
ms.topic: conceptual
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
caps.latest.revision: 7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 88796ef0cf870764b50d691b5eacc0205afba390
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2018
ms.locfileid: "35697105"
---
# <a name="clr-integration---what39s-new"></a>Интеграция со средой CLR - что&#39;новые s
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Ниже перечислены новые функции интеграции со средой CLR в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
-   В версии 4 среды CLR объекты базы данных среды CLR больше не перехватывают исключения состояния повреждения. Теперь эти исключения перехватываются на уровне интеграции со средой CLR. Эти исключения по-прежнему может быть перехвачено обработчиком компоненты базы данных среды CLR, задав для атрибута code ([\<legacyCorruptedStateExceptionsPolicy > элемент](http://go.microsoft.com/fwlink/?LinkId=204954)). Тем не менее делать это не рекомендуется, поскольку при возникновении исключения состояния повреждения добиться хороших результатов невозможно.  
  
-   В соответствии с требованиями строгой безопасности [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], компоненты базы данных среды CLR продолжат использовать модель управления доступом для кода, определенную в среде CLR версии 2.0.  
  
-   В среде CLR версии 4 ошибка формата в **System.TimeSpan** выдаст значение **System.FormatExceptions**. До выхода версии 4 среды CLR ошибка формата в **System.TimeSpan** значение было пропущено. Приложения баз данных, зависят от поведения до выхода версии 4 среды CLR должна быть запущена с уровнем совместимости базы данных (**уровень совместимости инструкции ALTER DATABASE**) 100 или ниже. Дополнительные сведения см. в разделе [< TimeSpan_LegacyFormatMode > элемент](http://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   Версия 4 среды CLR поддерживает Юникод 5.1. Операции сортировки с учетом некоторых диакритических знаков и символов будут улучшены. Если приложение использует устаревший порядок сортировки, могут возникнуть проблемы с совместимостью. Чтобы включить устаревший порядок сортировки, уровень совместимости базы данных (**уровень совместимости инструкции ALTER DATABASE**) должен иметь значение 100 или ниже. Для поддержи этого порядка сортировки [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] установит файл sort00001000.dll в каталог .NET Framework 4 (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Дополнительные сведения см. в разделе [ \<CompatSortNLSVersion > элемент](http://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   Были добавлены следующие столбцы [sys.dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md): **total_processor_time_ms**, **total_allocated_memory_kb**, и **survived_ memory_kb**.  
  
  
