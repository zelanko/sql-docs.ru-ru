---
title: "Возможности среды SQL Server Management Studio | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], about SQL Server Management Studio
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: e75504b9-7968-4e3b-8411-fd79fe09021e
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 82a8f1c09d51ad35b9d61e68b6878dc90b7d617c
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="features-in-sql-server-management-studio"></a>Возможности среды SQL Server Management Studio
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] обеспечивает следующие основные возможности:  
  
-   поддерживает большинство административных задач для [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)];  
  
-   Единая интегрированная среда для управления [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)] и разработки.  
  
-   Диалоговые окна для управления объектами в компоненте [!INCLUDE[ssDEnoversion](../includes/ssdenoversion_md.md)], службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)]и службах [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion_md.md)], позволяющие выполнять действия немедленно, направлять их в редактор кода или включать эти действия в скрипт для последующего выполнения.  
  
-   немодальные диалоговые окна с настройкой размеров, позволяющие при открытом диалоговом окне получать доступ к нескольким средствам;  
  
-   общее диалоговое окно планирования, позволяющее выполнять действия управляющих диалоговых окон в заданное время;  
  
-   экспорт и импорт регистрации сервера среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] из одной среды [!INCLUDE[ssManStudio](../includes/ssmanstudio_md.md)] в другую;  
  
-   сохранение и печать XML-файлов плана выполнения и взаимоблокировок, созданных приложением SQL Server Profiler, просмотр их в любое время и отправка для анализа администратору;  
  
-   новые окна сообщений об ошибках и информационных сообщений, предоставляющие гораздо больше сведений и позволяющие отправлять в [!INCLUDE[msCoName](../includes/msconame_md.md)] комментарии о сообщениях, копировать сообщения в буфер обмена и отправлять их по электронной почте в службу поддержки;  
  
-   встроенный веб-браузер для быстрого обращения к библиотеке MSDN или получения справки в Интернете;  
  
-   встроенная справка от сообществ в Интернете;  
  
-   Учебник по среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] , облегчающий освоение многих новых возможностей и помогающий сразу правильно и продуктивно их использовать.  
  
-   новый монитор активности с фильтрацией и автоматическим обновлением;  
  
-   встроенные интерфейсы компонента Database Mail.  
  
## <a name="new-scripting-capabilities"></a>Новые возможности создания скриптов  
Компонент среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] «Редактор кода» содержит встроенные редакторы скриптов для пользовательской разработки скриптов [!INCLUDE[tsql](../includes/tsql_md.md)], многомерных выражений, расширений интеллектуального анализа данных и XML для аналитики. Поддерживаются следующие возможности:  
  
-   динамическая справка для немедленного доступа к соответствующим данным во время работы;  
  
-   богатый набор шаблонов с возможностью создания пользовательских шаблонов;  
  
-   поддержка написания и изменения запросов и скриптов без подключения к серверу;  
  
-   поддержка запросов и скриптов SQLCMD;  
  
-   новый интерфейс для просмотра результатов XML;  
  
-   встроенная система управления версиями для проектов решений и скриптов, поддерживающая хранение и обслуживание копий скриптов по мере их разработки;  
  
-   [!INCLUDE[msCoName](../includes/msconame_md.md)] поддержка технологии IntelliSense для инструкций многомерных выражений.  
  
## <a name="object-explorer-features"></a>Возможности обозревателя объектов  
Компонент «Обозреватель объектов» среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] представляет собой встроенное средство просмотра и управления объектами на всех типах серверов. Поддерживаются следующие возможности:  
  
-   фильтрация по полному имени, его части, по схеме или дате;  
  
-   асинхронное заполнение объектов с возможностью фильтровать объекты по их метаданным;  
  
-   доступ к агентам [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] на серверах репликации в целях администрирования.  
  
Дополнительные сведения см. в статье [Семантический поиск](../ssms/object/object-explorer.md).  
  
## <a name="extensibility"></a>Расширяемость  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] построена на основе среды Visual Studio Isolated Shell, которая по определению поддерживает расширяемость (надстройки и подключаемые модули). Можно подключиться к службам расширяемости Visual Studio для выявления пользовательских возможностей в [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)], но подобная расширяемость не поддерживается.  
  
Некоторые пользователи и сторонние производители разработали расширения для [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)]. Мы не препятствуем этому, но следует помнить, что подобная расширяемость не поддерживается и могут возникнуть проблемы с обратной или прямой совместимостью. Корпорация Майкрософт не публикует документацию для расширения [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)]. Тем не менее существуют блоги сообществ и примеры кода, которые вы можете использовать.  
  
Корпорация Майкрософт не поддерживает установки [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] с присутствующими расширениями [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] , и в случае установки расширений [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] их может потребоваться удалить перед обращением в службу поддержки пользователей корпорации Майкрософт о неполадке в [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] .  
  
## <a name="see-also"></a>См. также:  
[Использование среды SQL Server Management Studio](../ssms/use-sql-server-management-studio.md)  
  

