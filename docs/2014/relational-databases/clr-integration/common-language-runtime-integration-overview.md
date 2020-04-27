---
title: Общие сведения об интеграции со средой CLR | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a7764c6e8e45b56e43e592e70b1c85b8d4744b69
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62919326"
---
# <a name="common-language-runtime-clr-integration-overview"></a>Общие сведения об интеграции со средой CLR
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] теперь включает в себя интеграцию компонента среды CLR .NET Framework для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Среда CLR предоставляет управляемому коду такие услуги, как межъязыковая интеграция, управление доступом для кода, управление временем существования объекта, а также поддержку отладки и профилирования. Для пользователей и разработчиков [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] интеграция со средой CLR означает, что теперь можно писать хранимые процедуры, триггеры, определяемые пользователем типы и функции (скалярные и возвращающие табличное значение), а также определяемые пользователем агрегатные функции на любом языке среды .NET, включая [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic и [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включает в себя предварительно установленную платформу .NET Framework (версия 4).  
  
 Далее перечислены основные преимущества этой интеграции.  
  
-   **Улучшенная модель программирования.** Языки платформы .NET Framework во многих отношениях богаче языка Transact-SQL. Они предлагают конструкции и возможности, ранее не доступные разработчикам программ для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Разработчики могут также использовать всю мощь библиотеки платформы .NET Framework (.NET Framework Library), предоставляющей обширный набор классов, которые позволяют быстро и эффективно решать возникающие при разработке проблемы.   
  
-   **Улучшенная надежность и безопасность.** Управляемый код выполняется в среде CLR, размещаемой в компоненте Database Engine. В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таким образом обеспечивается более безопасная и надежная альтернатива расширенным хранимым процедурам, доступным в предыдущих версиях [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   **Возможность определять типы данных и агрегатные функции.** Определяемые пользователем типы данных и статистические функции — два новых вида объектов в базе данных, расширяющие возможности запросов и хранения данных СУБД [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   **Упрощение процесса разработки в результате стандартизации среды.** Разработка базы данных интегрирована в будущие версии среды разработки [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio .NET. Для разработки и отладки объектов и скриптов баз данных разработчики используют те же инструментальные средства, что и для разработки компонентов и служб платформы .NET Framework клиентского и среднего уровня.  
  
-   **Возможность повышения производительности и масштабируемости.** Во многих случаях средства компиляции и модели выполнения платформы .NET Framework предоставляют выигрыш в производительности по сравнению с Transact-SQL.  
  
 В следующей таблице перечислены подразделы этого раздела.  
  
 [Общие сведения об интеграции со средой CLR](clr-integration-overview.md)  
 Описание видов объектов, которые можно построить с помощью интеграции со средой CLR, и обзор требований к построению объектов баз данных с помощью интеграции со средой CLR.  
  
 [новые возможности в интеграции со средой CLR](clr-integration-what-s-new.md)  
 Описывает новые возможности в данном выпуске.  
  
 [Архитектура интеграции со средой CLR](../../database-engine/dev-guide/architecture-of-clr-integration.md)  
 Описание целей разработки интеграции со средой CLR.  
  
 [Включение интеграции со средой CLR](clr-integration-enabling.md)  
 Описание включения интеграции со средой CLR.  
  
## <a name="see-also"></a>См. также  
 [Установка .NET Framework](https://technet.microsoft.com/library/ms166014\(v=SQL.105\).aspx)   
 [Производительность интеграции со средой CLR](clr-integration-architecture-performance.md)  
  
  
