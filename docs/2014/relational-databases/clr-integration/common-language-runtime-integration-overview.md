---
title: Среда CLR Integration Общие | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- managed code [SQL Server]
- common language runtime [SQL Server], about CLR integration
- cross-language integration
- integrating CLR [SQL Server]
- .NET Framework [SQL Server], common language runtime
- code access security [CLR integration]
- managed code [SQL Server], CLR integration
ms.assetid: 7be9e644-36a2-48fc-9206-faf59fdff4d7
caps.latest.revision: 63
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 291901016f703ff8be02189c23a54ad424c04b49
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191213"
---
# <a name="common-language-runtime-clr-integration-overview"></a>Общие сведения об интеграции со средой CLR
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] теперь содержит интеграцию компонента CLR платформы .NET Framework для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Среда CLR предоставляет управляемому коду такие услуги, как межъязыковая интеграция, управление доступом для кода, управление временем существования объекта, а также поддержку отладки и профилирования. Для пользователей и разработчиков [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] интеграция со средой CLR означает, что теперь можно писать хранимые процедуры, триггеры, определяемые пользователем типы и функции (скалярные и возвращающие табличное значение), а также определяемые пользователем агрегатные функции на любом языке среды .NET, включая [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic и [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включает в себя предварительно установленную платформу .NET Framework (версия 4).  
  
 Далее перечислены основные преимущества этой интеграции.  
  
-   **Улучшенная модель программирования.** Языки платформы .NET Framework во многих отношениях богаче языка Transact-SQL. Они предлагают конструкции и возможности, ранее не доступные разработчикам программ для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Разработчики могут также использовать всю мощь библиотеки платформы .NET Framework (.NET Framework Library), предоставляющей обширный набор классов, которые позволяют быстро и эффективно решать возникающие при разработке проблемы.   
  
-   **Улучшенная надежность и безопасность.** Управляемый код выполняется в среде CLR, размещаемой в компоненте Database Engine. В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таким образом обеспечивается более безопасная и надежная альтернатива расширенным хранимым процедурам, доступным в предыдущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   **Возможность определять типы данных и агрегатные функции.** Определяемые пользователем типы данных и статистические функции — два новых вида объектов в базе данных, расширяющие возможности запросов и хранения данных СУБД [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   **Упрощение процесса разработки в стандартизированной среде.** Разработка базы данных интегрирована в будущие версии среды разработки [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio .NET. Для разработки и отладки объектов и скриптов баз данных разработчики используют те же инструментальные средства, что и для разработки компонентов и служб платформы .NET Framework клиентского и среднего уровня.  
  
-   **Возможности для повышения производительности и масштабируемости.** Во многих случаях средства компиляции и модели выполнения платформы .NET Framework предоставляют выигрыш в производительности по сравнению с Transact-SQL.  
  
 В следующей таблице перечислены подразделы этого раздела.  
  
 [Общие сведения об интеграции со средой CLR](clr-integration-overview.md)  
 Описание видов объектов, которые можно построить с помощью интеграции со средой CLR, и обзор требований к построению объектов баз данных с помощью интеграции со средой CLR.  
  
 [Новые возможности в интеграции со средой CLR](clr-integration-what-s-new.md)  
 Описывает новые возможности в данном выпуске.  
  
 [Архитектура интеграции со средой CLR](../../database-engine/dev-guide/architecture-of-clr-integration.md)  
 Описание целей разработки интеграции со средой CLR.  
  
 [Включение интеграции со средой CLR](clr-integration-enabling.md)  
 Описание включения интеграции со средой CLR.  
  
## <a name="see-also"></a>См. также  
 [Установка .NET Framework](http://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx)   
 [Производительность интеграции со средой CLR](clr-integration-architecture-performance.md)  
  
  