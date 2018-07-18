---
title: Запуск помощника по обновлению (пользовательский интерфейс) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Report Viewer
- Upgrade Advisor [SQL Server], running
- launching Upgrade Advisor
- Upgrade Advisor Analysis Wizard
- starting Upgrade Advisor
- SQL Server Upgrade Advisor, running
ms.assetid: 7f47c9b3-88d3-43d6-837e-f157b49a55ac
caps.latest.revision: 40
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2bc1151b2df35b7912d03519cdf7f659ba96af16
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37216594"
---
# <a name="running-upgrade-advisor-user-interface"></a>Запуск помощника по обновлению (пользовательский интерфейс)
  Советник по переходу может быть запущен для анализа локальных или удаленных компонентов в процессе планирования обновления. Для каждого проанализированного компонента и экземпляра помощник по обновлению создает отчет.  
  
> [!IMPORTANT]  
>  Помощник по обновлению не анализирует удаленные экземпляры служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Чтобы выполнить анализ экземпляра служб [!INCLUDE[ssRS](../../includes/ssrs-md.md)], необходимо установить помощник по обновлению на компьютере, где установлены службы [!INCLUDE[ssRS](../../includes/ssrs-md.md)].  
>   
>  Для анализа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы Integration Services, необходимо иметь [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] установлен и [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] установлен на том же компьютере.  
  
## <a name="running-the-upgrade-advisor-analysis-wizard"></a>Мастер анализа помощника по обновлению  
 Работа мастера анализа помощника по обновлению включает шесть этапов.  
  
1.  Запустите мастер с начальной страницы помощника по обновлению.  
  
2.  Определите анализируемый сервер и компоненты.  
  
3.  Соберите сведения для проверки подлинности.  
  
4.  Определите дополнительные параметры в зависимости от типа компонентов.  
  
5.  Выполните анализ выбранных компонентов.  
  
6.  Создайте отчет о выявленных проблемах обновления.  
  
 Дополнительные сведения о мастера анализа помощника по обновлению см. в разделе [как: запустить мастер анализа помощника по обновлению](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md).  
  
 Дополнительные сведения, необходимые для каждого шага, см. в разделе [Справочник по интерфейсу пользователя помощника по обновлению](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md).  
  
## <a name="running-the-upgrade-advisor-report-viewer"></a>Средство просмотра отчетов помощника по обновлению  
 Средство просмотра отчетов помощника по обновлению используется для просмотра отчетов, созданных мастером анализа помощника по обновлению. После загрузки отчета его компоненты можно отфильтровать по следующим параметрам:  
  
-   все проблемы;  
  
-   все проблемы, связанные с обновлением;  
  
-   проблемы, связанные с подготовкой к обновлению;  
  
-   все проблемы, связанные с миграцией;  
  
-   устраненные проблемы.  
  
-   Неустраненные проблемы  
  
 Пошаговые инструкции по использованию средства просмотра отчетов см. в следующих разделах.  
  
-   [Просмотр отчета помощника по обновлению](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)  
  
-   [Фильтрация отчетов](../../../2014/sql-server/install/how-to-filter-reports.md)  
  
-   [Экспорт отчетов](../../../2014/sql-server/install/how-to-export-reports.md)  
  
## <a name="see-also"></a>См. также  
 [Практическое: запустить мастер анализа помощника по обновлению](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [Справочник по пользовательскому интерфейсу помощника по обновлению](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)   
 [Разрешение проблем при обновлении](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
