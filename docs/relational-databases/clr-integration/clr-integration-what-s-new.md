---
title: Новые возможности интеграции со средой CLR | Документация Майкрософт
description: Microsoft SQL Server размещения CLR называется интеграцией со средой CLR. В этой статье описаны новые функции интеграции со средой CLR в SQL Server 2012.
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: clr
ms.topic: conceptual
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
ms.openlocfilehash: d27bf0d925d3a98dda488fb85aff7446434cc8ad
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488095"
---
# <a name="clr-integration---what39s-new"></a>Интеграция со средой CLR — новые&#39;
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Ниже перечислены новые функции интеграции со средой CLR в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
-   В версии 4 среды CLR объекты базы данных среды CLR больше не перехватывают исключения состояния повреждения. Теперь эти исключения перехватываются на уровне интеграции со средой CLR. Эти исключения по-прежнему могут быть перехвачены компонентами базы данных CLR путем установки атрибута Code ([\<легацикорруптедстатиксцептионсполици> элемент](https://go.microsoft.com/fwlink/?LinkId=204954)). Тем не менее делать это не рекомендуется, поскольку при возникновении исключения состояния повреждения добиться хороших результатов невозможно.  
  
-   В соответствии с требованиями строгой безопасности [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], компоненты базы данных среды CLR продолжат использовать модель управления доступом для кода, определенную в среде CLR версии 2.0.  
  
-   В среде CLR версии 4 Ошибка формата в значении **System. TimeSpan** создаст объект **System. форматексцептионс**. До версии 4 среды CLR ошибка формата в значении **System. TimeSpan** была пропущена. Приложения базы данных, зависящие от поведения до версии 4 среды CLR, должны работать с уровнем совместимости базы данных (**уровень совместимости ALTER DATABASE**) 100 или ниже. Дополнительные сведения см. в разделе [<TimeSpan_LegacyFormatMode> element](https://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   Версия 4 среды CLR поддерживает Юникод 5.1. Операции сортировки с учетом некоторых диакритических знаков и символов будут улучшены. Если приложение использует устаревший порядок сортировки, могут возникнуть проблемы с совместимостью. Чтобы включить сортировку прежних версий, уровень совместимости базы данных (**уровень совместимости ALTER DATABASE**) должен быть установлен в 100 или ниже. Для поддержи этого порядка сортировки [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] установит файл sort00001000.dll в каталог .NET Framework 4 (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Дополнительные сведения см. в разделе [ \<компатсортнлсверсион> element](https://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   В [sys. dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md)были добавлены следующие столбцы: **total_processor_time_ms**, **total_allocated_memory_kb**и **survived_memory_kb**.  
  
  
