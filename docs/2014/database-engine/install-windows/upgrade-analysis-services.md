---
title: Обновление служб Analysis Services | Документы Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- upgrading databases
- databases [Analysis Services], upgrading
- installing Analysis Services, side-by-side installations
- Analysis Services upgrades
- Analysis Services upgrades, about upgrading Analysis Services
- SSAS, database migration
- upgrading Analysis Services
- installing Analysis Services, upgrading
- SSAS, upgrading
ms.assetid: a131d329-386e-4470-aaa9-ffcde4e5ec0c
author: Minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cdd9e34e57694efc1234a2f0245833596644cb73
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68889186"
---
# <a name="upgrade-analysis-services"></a>Обновление служб Analysis Services
  Используйте пакет установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для обновления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения об обновлении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режиме интеграции с SharePoint см. в разделе [Upgrade PowerPivot для SharePoint](upgrade-power-pivot-for-sharepoint.md). Дополнительные сведения об обновлении существующего экземпляра SQL Server см. в статье [обновление до SQL Server 2014 с помощью мастера установки &#40;&#41;установки ](upgrade-sql-server-using-the-installation-wizard-setup.md).  
  
## <a name="known-upgrade-issues"></a>Известные проблемы при обновлении  
 Перед обновлением до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]просмотрите следующие источники:  
  
-   [Заметки о Выпуске SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=296445).  
  
-   Чтобы узнать, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] какие функции и функции были прекращены, устарели или изменены, см. [Analysis Services обратная совместимость](https://docs.microsoft.com/analysis-services/analysis-services-backward-compatibility).  
  
## <a name="pre-upgrade-checklist"></a>Контрольный список действий перед обновлением  
 Перед обновлением просмотрите следующую информацию:  
  
-   [Поддерживаемые обновления версий и выпусков](supported-version-and-edition-upgrades.md)  
  
-   [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [Параметры для средства проверки конфигурации системы](check-parameters-for-the-system-configuration-checker.md)  
  
-   [Вопросы безопасности при установке SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
-   [Создание и восстановление резервных копий баз данных служб Analysis Services](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases)  
  
-   [Использование помощника по обновлению для подготовки к обновлениям](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
## <a name="upgrading-analysis-services"></a>Обновление служб Analysis Services  
 Можно выбрать один из нескольких способов обновления сервера и данных.  
  
-   **При обновлении на месте** существующие программные файлы заменяются [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] программами. Базы данных остаются в том же расположении. Программные папки обновляются с целью отражения нового имени.  
  
-   **Параллельное обновление** — это новая установка [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] на том же компьютере, на котором имеется экземпляр Analysis Services. Можно перенести базы данных на новый экземпляр на этом же компьютере и затем удалить старую версию, если она больше не используется.  
  
-   Можно также установить службы Analysis Services на новом оборудовании, а затем осуществить миграцию существующих баз данных на этот сервер.  
  
## <a name="in-place-upgrade"></a>Обновление на месте  
 Можно обновить существующий экземпляр [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и, как часть процесса обновления, автоматически перенести существующие базы данных из старого экземпляра в новый экземпляр. Поскольку метаданные и двоичные данные между двумя версиями совместимы, после обновления данные сохраняются и их не нужно переносить вручную.  
  
 Чтобы обновить существующий экземпляр, запустите программу установки и укажите имя существующего экземпляра в качестве имени нового экземпляра.  
  
## <a name="upgrading-databases"></a>Обновление баз данных  
 Базы данных, созданные в предыдущих версиях служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , на обновленном сервере работают со старым значением уровня совместимости. Базы данных, созданные в следующих версиях, имеют уровень совместимости баз данных 105. Если необходимо использовать функции, требующие нового уровня совместимости базы данных, уровень совместимости можно изменить. В противном случае базы данных можно запустить на обновленном сервере, используя исходные параметры. Дополнительные сведения см. [в разделе Установка уровня совместимости многомерной базы данных &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services).  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Функции, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Основные сведения об архитектуре Microsoft OLAP](https://docs.microsoft.com/analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture)   
 [PowerPivot для SharePoint обновления](upgrade-power-pivot-for-sharepoint.md)   
 [Установка Analysis Services в многомерном режиме и модели интеллектуального анализа данных](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md)   
 [Установка PowerPivot для SharePoint 2010](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
