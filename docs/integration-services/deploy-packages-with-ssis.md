---
title: "Развертывание пакетов с помощью служб SSIS | Документы Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
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
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 939f988b8d91e93aa8f1cc4ef4b555af7b26cf67
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="deploy-packages-with-ssis"></a>Развертывание пакетов с помощью служб SSIS
Службы [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] содержат средства, облегчающие развертывание пакетов на другом компьютере. Средства развертывания управляют любыми зависимостями, такими как конфигурации или требуемые пакету файлы. В данном учебнике демонстрируется, как с помощью этих средств устанавливать пакеты и их зависимости на целевом компьютере.    
    
Сначала требуется выполнить задачи для подготовки к развертыванию. Необходимо создать новый проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] и добавить в проект существующие пакеты и файлы данных. Не нужно создавать никакие пакеты; вместо этого работа ведется только с завершенными пакетами, созданными при выполнении заданий этого учебника. Функциональность пакетов из данного учебника менять не придется, тем не менее, может оказаться полезным после добавления пакетов в проект открыть их в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] и просмотреть содержимое каждого пакета. Содержимое пакетов показывает их зависимости, такие как файлы журнала, а также другие интересные особенности пакетов.    
    
При подготовке к развертыванию требуется обновить пакеты для использования конфигураций. Конфигурации позволяют свойствам и объектам пакетов получать обновления во время выполнения. В этом учебнике конфигурации используются для обновления строк соединения файлов журнала и текстовых файлов, а так же для обновления расположения XML- и XSD-файлов, используемых пакетом. Дополнительные сведения о см. в разделах [Конфигурации пакета](../integration-services/packages/package-configurations.md) и [Создание конфигурации пакетов](../integration-services/packages/create-package-configurations.md).    
    
После проверки успешного выполнения пакетов в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]требуется создать комплект развертывания для установки пакетов. Комплект развертывания содержит файлы пакетов и другие элементы, добавленные в проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , зависимости пакетов, автоматически добавленные службами [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , а также созданную пользователем программу развертывания. Дополнительные сведения см. в статье [Create a Deployment Utility](../integration-services/packages/create-a-deployment-utility.md).    
    
После этого требуется скопировать комплект развертывания на целевой компьютер и запустить мастер установки пакета, чтобы установить пакеты и их зависимости. Пакеты устанавливаются в базе данных msdb SQL Server, а файлы поддержки и вспомогательные файлы — в файловой системе. Конфигурации, используемые развернутыми пакетами, необходимо обновить для использования новых значений, благодаря которым пакеты могут успешно выполняться в новой среде.    
    
Наконец, требуется запустить пакеты в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] с помощью программы выполнения пакетов.    
    
Целью данного учебника является демонстрация сложности некоторых вопросов развертывания, с которыми пользователю приходится сталкиваться при работе. Если по каким-либо причинам у пользователя нет возможности развернуть пакеты на другом компьютере, этот учебник можно выполнить, установив пакеты на локальном экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]в базе данных msdb и запустив их в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] на этом же экземпляре.    
    
## <a name="what-you-will-learn"></a>Обзор учебника    
Новые средства, элементы управления и возможности служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] лучше всего изучать на практике. С помощью данного учебника шаг за шагом создается проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , куда затем добавляются пакеты и другие необходимые файлы. Когда проект полностью завершен, пользователь создает комплект развертывания и копирует его на целевой компьютер, куда затем устанавливаются пакеты.    
    
## <a name="requirements"></a>Требования    
Этот учебник предназначен для пользователей, знакомых с основными операциями файловой системы, но имеющих ограниченное представление о новых возможностях служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Для лучшего понимания основных понятий служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , с которыми знакомит этот учебник, может пригодиться предварительное изучение следующего учебника по использованию служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] : [Службы SSIS: создание пакета ETL](../integration-services/ssis-how-to-create-an-etl-package.md).    
    
**Компьютер-источник.** На компьютере, где создается пакет развертывания, **должны быть установлены следующие компоненты.**
- SQL Server  
- Образцы данных, завершенные пакеты, конфигурации и файл сведений. Эти файлы устанавливаются вместе при скачивании [примеров баз данных Adventure Works 2014](https://msftdbprodsamples.codeplex.com/releases/view/125550).     
> **Примечание.** Пользователь должен иметь разрешение на создание и удаление таблиц в базе данных AdventureWorks, а также других используемых данных.         
    
-   [SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).    
    
**Целевой компьютер.** На компьютере, где будут развернуты пакеты, **должны быть установлены следующие компоненты.**    
    
- SQL Server
- Образцы данных, завершенные пакеты, конфигурации и файл сведений. Эти файлы устанавливаются вместе при скачивании [примеров баз данных Adventure Works 2014](https://msftdbprodsamples.codeplex.com/releases/view/125550). 
    
- [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx).    
    
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].    
    
-   Пользователь должен иметь разрешение на создание и удаление таблиц в базе данных AdventureWorks, а также на запуск пакетов в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].    
    
-   Пользователь должен иметь разрешение на чтение и запись в таблицу sysssispackages в системной базе данных msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .    
    
Если развертывание пакетов предполагается на том же самом компьютере, где создается комплект развертывания, этот компьютер должен удовлетворять требованиям как компьютера-источника, так и целевого компьютера.    
    
**Предполагаемое время для выполнения заданий этого учебника:** 2 часа    
    
## <a name="lessons-in-this-tutorial"></a>Занятия этого учебника    
[Занятие 1. Подготовка к созданию пакета развертывания](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md)    
На этом занятии требуется развернуть ETL-решение путем создания нового проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и добавления пакетов и других необходимых файлов.    
    
[Занятие 2. Создание пакета развертывания в службах SSIS](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)    
На этом занятии требуется создать программу развертывания и убедиться, что в комплекте развертывания содержатся необходимые файлы.    
    
[Занятие 3. Установка пакетов SSIS](../integration-services/lesson-3-install-ssis-packages.md)    
На этом занятии требуется скопировать пакет развертывания на целевой компьютер, установить пакеты и запустить их.    
    


