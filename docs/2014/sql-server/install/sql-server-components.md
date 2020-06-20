---
title: Компоненты SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Upgrade Advisor, components
- listing components to analyze
- Upgrade Advisor [SQL Server], components
- component analysis [Upgrade Advisor]
- finding components to analyze
- locating components to analyze
- detecting components to analyze
- server names [Upgrade Advisor]
- analyzing system [Upgrade Advisor], component list
- identifying components to analyze
ms.assetid: 539b9525-ce3f-4950-9146-5527a5a297ee
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 809705e50e9337a63bf33c2883a1e5d43197be09
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85036277"
---
# <a name="sql-server-components"></a>Компоненты SQL Server
  Мастер анализа помощника по обновлению можно запустить на локальном или удаленном компьютере, на котором [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] установлен,, [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] . Первый шаг анализа, предшествующего обновлению, — определение компьютера и компонентов, подлежащих анализу.  
  
## <a name="options"></a>Варианты  
 **Имя компьютера**  
 Задает имя компьютера для проведения анализа. Советник по переходу заполняет поле **имя сервера** именем локального компьютера. Для подключения к локальному компьютеру можно также использовать обозначения «.» и «localhost».  
  
 Для анализа другого компьютера используются следующие правила.  
  
-   Чтобы проверить некластеризованные экземпляры, введите имя компьютера.  
  
-   Чтобы просмотреть кластеризованные экземпляры, введите имя экземпляра отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Чтобы проверить некластеризованные компоненты, установленные на узле кластера, введите имя компьютера для узла отказоустойчивого кластера.  
  
    > [!IMPORTANT]  
    >  Не включайте в него имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Вместо имени компьютера можно указать его IP-адрес.  
  
 При просмотре служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] следует указать имя локального компьютера. Помощник по обновлению просматривает только локальные серверы отчетов.  
  
 **Detect**  
 Кнопка " **обнаружить** " обращается к указанному компьютеру и обнаруживает анализируемые компоненты:  
  
-   Если выполняется анализ экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на удаленном компьютере, на этом компьютере необходимо включить службы удаленного реестра.  
  
-   Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет обнаружен в том случае, если в реестре компьютера найден экземпляр [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
-   Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] обнаруживаются по наличию данных экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в реестре компьютера.  
  
-   Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] будут обнаружены, если в реестре компьютера найдены службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Однако помощник по обновлению просматривает только локальные серверы отчетов.  
  
 **Components**  
 Выберите компоненты, подлежащие анализу. Можно нажать кнопку **обнаружения** , чтобы выбрать все компоненты, установленные на компьютере. Рядом с компонентами, найденными на данном компьютере, будет установлен флажок. Можно также выбрать компоненты вручную, установив или сняв флажок рядом с каждым компонентом.  
  
## <a name="see-also"></a>См. также:  
 [Работа с советником по переходу](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Справочник по пользовательскому интерфейсу помощника по обновлению](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
