---
title: Что нового в интеграции CLR Документы Майкрософт
description: Хостинг CLR сервера Microsoft S'L называется интеграцией CLR. В этой статье описаны новые функции в интеграции CLR в S'L Server 2012.
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
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488095"
---
# <a name="clr-integration---what39s-new"></a>CLR Интеграция - Что&#39;нового
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Ниже перечислены новые функции интеграции со средой CLR в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
-   В версии 4 среды CLR объекты базы данных среды CLR больше не перехватывают исключения состояния повреждения. Теперь эти исключения перехватываются на уровне интеграции со средой CLR. Эти исключения все еще могут быть пойманы компонентами базы данных CLR, установив атрибут кода[\<(legacyCorruptStateExceptionsPolicy> Элемент).](https://go.microsoft.com/fwlink/?LinkId=204954) Тем не менее делать это не рекомендуется, поскольку при возникновении исключения состояния повреждения добиться хороших результатов невозможно.  
  
-   В соответствии с требованиями строгой безопасности [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], компоненты базы данных среды CLR продолжат использовать модель управления доступом для кода, определенную в среде CLR версии 2.0.  
  
-   В версии CLR 4 ошибка формата в значении **System.TimeSpan** будет генерировать **System.FormatExceptions.** До версии 4 CLR была проигнорирована ошибка формата в значении **System.TimeSpan.** Приложения базы данных, которые полагаются на поведение до версии 4 CLR, должны работать с уровнем совместимости базы данных **(level ALTER DATABASE Совместимость)** 100 или ниже. Для получения дополнительной информации см. [<TimeSpan_LegacyFormatMode> элемент](https://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   Версия 4 среды CLR поддерживает Юникод 5.1. Операции сортировки с учетом некоторых диакритических знаков и символов будут улучшены. Если приложение использует устаревший порядок сортировки, могут возникнуть проблемы с совместимостью. Для обеспечения устаревшей сортировки уровень совместимости базы данных **(alter DATABASE Уровень совместимости)** должен быть установлен до 100 или ниже. Для поддержи этого порядка сортировки [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] установит файл sort00001000.dll в каталог .NET Framework 4 (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Для получения дополнительной информации [ \<см. CompatSortNLSVersion> Элемент](https://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   Следующие столбцы были добавлены в [sys.dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md): **total_processor_time_ms,** **total_allocated_memory_kb**и **survived_memory_kb.**  
  
  
