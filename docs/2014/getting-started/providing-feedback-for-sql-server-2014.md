---
title: Отзывы по SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- sending feedback to Microsoft
- errors [SQL Server], feedback reporting
- feedback [SQL Server]
- submitting feedback [SQL Server]
- bug reporting [SQL Server]
- reporting usage information to Microsoft
- reporting errors to Microsoft
- SQL Server, feedback reporting
- documentation feedback [SQL Server]
- usage information reporting [SQL Server]
- product feedback [SQL Server]
- automatic error or usage reporting
ms.assetid: 28f3ebf0-ad71-4816-86a6-18a46f023cfe
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10466721f50dd8b090b5d6b1a06b5bffd6e5289d
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53376746"
---
# <a name="providing-feedback-for-sql-server-2014"></a>Отзывы по SQL Server 2014
  Корпорация [!INCLUDE[msCoName](../includes/msconame-md.md)] ценит, что вы уделили часть своего времени, чтобы помочь в улучшении продуктов и документации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Можно предоставлять отчеты об ошибках и выдвигать предложения, касающиеся характеристик продуктов или пользовательского интерфейса, предоставлять отзывы о документации; кроме того, можно разрешить автоматическую отправку отчетов об ошибках и данных об использовании продуктов в [!INCLUDE[msCoName](../includes/msconame-md.md)] для дальнейшего анализа. Каждый из трех методов обратной связи описывается в этом разделе.  
  
## <a name="submitting-feedback-about-the-product"></a>Как представить отчеты и отзывы о продукте  
 Для отправки предложений и отчетов по сбоям [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] можно использовать страницу обратной связи [!INCLUDE[msCoName](../includes/msconame-md.md)] на веб-узле [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Connect. Это относится, в частности, к таким функциям и возможностям, как средства и служебные программы, языки и интерфейсы программирования.  
  
 Открыть страницу обратной связи [!INCLUDE[msCoName](../includes/msconame-md.md)] на веб-узле [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Connect можно одним из следующих способов.  
  
-   Перейдите на [веб-страницу](https://go.microsoft.com/fwlink/?linkid=34178) отзывов о [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в [!INCLUDE[msCoName](../includes/msconame-md.md)] Connect.  
  
-   Нажмите кнопку **Отправить отзыв** на панели инструментов "Справка" среды [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] или выберите в меню пункт **Сообщество/Отправить отзыв**.  
  
-   Нажмите кнопку **Отправить отзыв** на панели инструментов "Справка" среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
-   В верхней части любого раздела электронной документации по [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] нажмите кнопку **Отправить отзыв**.  
  
 Панель инструментов справки скрыта в средах [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] и [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] до тех пор, пока не будет сделано следующее:  
  
-   вызвана справка из программы;  
  
-   Выберите **помочь** флажок на **панелей инструментов** вкладке **Сервис/Настройка...**  команды.  
  
## <a name="automatic-error-and-usage-reporting"></a>Автоматические отчеты об ошибках и использовании  
 Можно включить автоматическую отправку отчетов об ошибках и сведений об использовании программного обеспечения и служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. В [!INCLUDE[msCoName](../includes/msconame-md.md)] эти сведения используются для улучшения [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Все данные являются конфиденциальными.  
  
### <a name="managing-automatic-usage-reporting"></a>Управление автоматическими отчетами об использовании  
 Автоматическая отчетность по использованию позволяет решить, следует ли собирать и отправлять данные в [!INCLUDE[msCoName](../includes/msconame-md.md)]. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использует два конвейера для отправки отчетов об использовании. По ним одновременно отправляются сходные данные, но для разных программ; при этом включение и отключение конвейеров производится раздельно. Включение или отключение конвейера любой из использующих его программ также включает или отключает сбор данных для других программ, которые используют этот конвейер совместно с данной программой.  
  
-   Один конвейер служит для данных отчетов об использовании для всех [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], за исключением электронной документации и некоторых элементов пользовательского интерфейса на основе [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio в средствах [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. После установки также можно выключить или включить этот конвейер. Чтобы сделать это, откройте в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] проект [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], а затем выберите в меню **Справка** пункт **Параметры отзывов пользователей**. Этот пункт меню не отображается, пока не открыт проект [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Другой конвейер используется электронной документацией по [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] элементами пользовательского интерфейса инструментальных средств [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], основанными на среде Visual Studio, и средой Visual Studio. После установки также можно выключить или включить этот конвейер. Чтобы сделать это, откройте в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] проект [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], а затем выберите в меню **Справка** пункт **Параметры отзывов пользователей**. Этот пункт меню не отображается, пока не открыт проект [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="helping-build-a-better-books-online"></a>Помощь в построении электронной документации  
 Включение отчетов об использовании электронной документации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поможет команде разработчиков усовершенствовать ее. Статистические данные, поступающие от клиентов, помогают понять их потребности. Становится понятнее, как они переходят по разделам, как часто они просматривают определенные разделы, а также какие из разделов они считают наиболее и наименее полезными.  
  
 Отзывы помогают понять, как используется документация. Это помогает сконцентрироваться на наиболее важных разделах при разработке будущей системы документации для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Эти данные об использовании электронной документации также позволяют выявить компоненты, по которым пользователи чаще всего вызывают справку. Это может быть признаком того, что следует повысить удобство их использования.  
  
  
