---
title: Руководство по службам SSIS. Развертывание пакетов | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- deployment tutorial [Integration Services]
- deploying packages [Integration Services]
- SSIS, tutorials
- Integration Services, tutorials
- deploying packages [Integration Services], installing
- SQL Server Integration Services, tutorials
- walkthroughs [Integration Services]
- deployment utility [Integration Services]
- deploying packages [Integration Services], configurations
ms.assetid: de18468c-cff3-48f4-99ec-6863610e5886
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3752c7e0f99a62534a670743c0ee7deb3c2e07a8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899012"
---
# <a name="ssis-tutorial-deploying-packages"></a>Руководство по службам SSIS. Развертывание пакетов
  Службы[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] содержат средства, облегчающие развертывание пакетов на другом компьютере. Средства развертывания управляют любыми зависимостями, такими как конфигурации или требуемые пакету файлы. В данном учебнике демонстрируется, как с помощью этих средств устанавливать пакеты и их зависимости на целевом компьютере.  
  
 Сначала требуется выполнить задачи для подготовки к развертыванию. Необходимо создать новый проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] и добавить в проект существующие пакеты и файлы данных. Не нужно создавать никакие пакеты; вместо этого работа ведется только с завершенными пакетами, созданными при выполнении заданий этого учебника. Функциональность пакетов из данного учебника менять не придется, тем не менее, может оказаться полезным после добавления пакетов в проект открыть их в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] и просмотреть содержимое каждого пакета. Содержимое пакетов показывает их зависимости, такие как файлы журнала, а также другие интересные особенности пакетов.  
  
 При подготовке к развертыванию требуется обновить пакеты для использования конфигураций. Конфигурации позволяют свойствам и объектам пакетов получать обновления во время выполнения. В этом учебнике конфигурации используются для обновления строк соединения файлов журнала и текстовых файлов, а так же для обновления расположения XML- и XSD-файлов, используемых пакетом. Дополнительные сведения о см. в разделах [Конфигурации пакета](../../2014/integration-services/package-configurations.md) и [Создание конфигурации пакетов](../../2014/integration-services/create-package-configurations.md).  
  
 После проверки успешного выполнения пакетов в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]требуется создать комплект развертывания для установки пакетов. Комплект развертывания содержит файлы пакетов и другие элементы, добавленные в проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , зависимости пакетов, автоматически добавленные службами [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , а также созданную пользователем программу развертывания. Дополнительные сведения см. в статье [Create a Deployment Utility](../../2014/integration-services/create-a-deployment-utility.md).  
  
 После этого требуется скопировать комплект развертывания на целевой компьютер и запустить мастер установки пакета, чтобы установить пакеты и их зависимости. Пакеты устанавливаются в базе данных msdb SQL Server, а файлы поддержки и вспомогательные файлы — в файловой системе. Конфигурации, используемые развернутыми пакетами, необходимо обновить для использования новых значений, благодаря которым пакеты могут успешно выполняться в новой среде.  
  
 Наконец, требуется запустить пакеты в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] с помощью программы выполнения пакетов.  
  
 Целью данного учебника является демонстрация сложности некоторых вопросов развертывания, с которыми пользователю приходится сталкиваться при работе. Если по каким-либо причинам у пользователя нет возможности развернуть пакеты на другом компьютере, этот учебник можно выполнить, установив пакеты на локальном экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]в базе данных msdb и запустив их в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] на этом же экземпляре.  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
 Новые средства, элементы управления и возможности служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] лучше всего изучать на практике. С помощью данного учебника шаг за шагом создается проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , куда затем добавляются пакеты и другие необходимые файлы. Когда проект полностью завершен, пользователь создает комплект развертывания и копирует его на целевой компьютер, куда затем устанавливаются пакеты.  
  
## <a name="requirements"></a>Требования  
 Этот учебник предназначен для пользователей, знакомых с основными операциями файловой системы, но имеющих ограниченное представление о новых возможностях служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Для лучшего понимания основных [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] концепции, которыми знакомит данный учебник, вы может пригодиться предварительное изучение следующих [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] учебники: [Запуск SQL Server мастер импорта и экспорта](import-export-data/start-the-sql-server-import-and-export-wizard.md) и [учебник по службам SSIS: Создание простого ETL-пакета](../integration-services/ssis-how-to-create-an-etl-package.md).  
  
 **Компьютер-источник.** На компьютере, где создается пакет развертывания, должны быть установлены следующие компоненты:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с базой данных AdventureWorks. В целях повышения безопасности образцы баз данных по умолчанию не устанавливаются. Можно загрузить образец базы данных из [CodePlex](http://msftdbprodsamples.codeplex.com/releases/view/125550).  
  
-   Пользователь должен обладать разрешением на создание и удаление таблиц в базе данных AdventureWorks.  
  
-   Этот учебник также требует также образцов данных, завершенные пакеты, конфигурации и файл Readme. Файлы этих компонентов устанавливаются вместе с образцами. Если образцы данных не удается найти, следует вернуться к предыдущей процедуре и выполнить установку в соответствии с инструкциями.  
  
-   Среда разработки решений в области бизнес-аналитики [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 **Целевой компьютер.** На компьютере, где будут развернуты пакеты, должны быть установлены следующие компоненты:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с базой данных AdventureWorks.  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
-   Пользователь должен иметь разрешение на создание и удаление таблиц в базе данных AdventureWorks, а также на запуск пакетов в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
-   Необходимо иметь разрешение чтение и запись в таблице sysssispackages в базе данных msdb[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] системной базы данных.  
  
 Если развертывание пакетов предполагается на том же самом компьютере, где создается комплект развертывания, этот компьютер должен удовлетворять требованиям как компьютера-источника, так и целевого компьютера.  
  
 **Предполагаемое время для выполнения заданий данного учебника:** 2 часа  
  
## <a name="lessons-in-this-tutorial"></a>Занятия этого учебника  
 [Занятие 1. Подготовка к созданию пакета развертывания](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md)  
 На этом занятии требуется развернуть ETL-решение путем создания нового проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и добавления пакетов и других необходимых файлов.  
  
 [Занятие 2. Cоздание пакета развертывания](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)  
 На этом занятии требуется создать программу развертывания и убедиться, что в комплекте развертывания содержатся необходимые файлы.  
  
 [Занятие 3. Установка пакетов](../integration-services/lesson-3-install-ssis-package.md)  
 На этом занятии требуется скопировать пакет развертывания на целевой компьютер, установить пакеты и запустить их.  
  
![Значок служб Integration Services (маленький)](media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
  
