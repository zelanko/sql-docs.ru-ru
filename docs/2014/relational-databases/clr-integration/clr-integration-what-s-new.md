---
title: Новые возможности интеграции со средой CLR&#39;| Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
ms.openlocfilehash: b51eb5d8bee5ff8e514f294d5e9facca93a30bfa
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953556"
---
# <a name="what39s-new-in-clr-integration"></a>Новые возможности интеграции со средой CLR&#39;
  Ниже перечислены новые функции интеграции со средой CLR в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
-   В версии 4 среды CLR объекты базы данных среды CLR больше не перехватывают исключения состояния повреждения. Теперь эти исключения перехватываются на уровне интеграции со средой CLR. Эти исключения по-прежнему могут быть перехвачены компонентами базы данных CLR путем задания атрибута кода ([ \<legacyCorruptedStateExceptionsPolicy> element](https://go.microsoft.com/fwlink/?LinkId=204954)). Тем не менее делать это не рекомендуется, поскольку при возникновении исключения состояния повреждения добиться хороших результатов невозможно.  
  
-   В соответствии с требованиями строгой безопасности [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], компоненты базы данных среды CLR продолжат использовать модель управления доступом для кода, определенную в среде CLR версии 2.0.  
  
-   В среде CLR версии 4 ошибка формата в значении `System.TimeSpan` формирует исключение `System.FormatExceptions`. До выхода версии 4 среды CLR ошибка формата в значении `System.TimeSpan` не обрабатывалась. Приложения баз данных, которые зависят от поведения, характерного для среды CLR версии ниже 4, должны выполняться с уровнем совместимости базы данных (`ALTER DATABASE Compatibility Level`) 100 или ниже. Дополнительные сведения см. в разделе [<TimeSpan_LegacyFormatMode> element](https://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   Версия 4 среды CLR поддерживает Юникод 5.1. Операции сортировки с учетом некоторых диакритических знаков и символов будут улучшены. Если приложение использует устаревший порядок сортировки, могут возникнуть проблемы с совместимостью. Чтобы включить устаревший порядок сортировки, необходимо установить уровень совместимости базы данных (`ALTER DATABASE Compatibility Level`) 100 или ниже. Для поддержи этого порядка сортировки [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] установит файл sort00001000.dll в каталог .NET Framework 4 (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Дополнительные сведения см. в разделе [\<CompatSortNLSVersion>Element](https://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   В [sys. dm_clr_appdomains](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql)были добавлены следующие столбцы: `total_processor_time_ms` , `total_allocated_memory_kb` и `survived_memory_kb` .  
  
  
