---
title: Развертывание пакетов с помощью служб SSIS | Документы Майкрософт
ms.custom: ''
ms.date: 08/20/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: quickstart
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
ms.openlocfilehash: e421382b578d8494f7311414f93fec458014d552
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057706"
---
# <a name="deploy-packages-with-ssis"></a>Развертывание пакетов с помощью служб SSIS

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Службы[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] содержат средства, облегчающие развертывание пакетов на другом компьютере. Средства развертывания управляют любыми зависимостями, такими как конфигурации или требуемые пакету файлы. В данном учебнике демонстрируется, как с помощью этих средств устанавливать пакеты и их зависимости на целевом компьютере.    
    
Сначала требуется выполнить задачи для подготовки к развертыванию. Необходимо создать новый проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] и добавить в проект существующие пакеты и файлы данных. Не нужно создавать никакие пакеты; вместо этого работа ведется только с завершенными пакетами, созданными при выполнении заданий этого учебника. Функциональность пакетов из данного учебника менять не придется, тем не менее, может оказаться полезным после добавления пакетов в проект открыть их в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] и просмотреть содержимое каждого пакета. Содержимое пакетов показывает их зависимости, такие как файлы журнала, а также другие интересные особенности пакетов.    
    
При подготовке к развертыванию требуется обновить пакеты для использования конфигураций. Конфигурации позволяют свойствам и объектам пакетов получать обновления во время выполнения. В этом учебнике конфигурации используются для обновления строк соединения файлов журнала и текстовых файлов, а так же для обновления расположения XML- и XSD-файлов, используемых пакетом. Дополнительные сведения о см. в разделах [Конфигурации пакета](../integration-services/packages/package-configurations.md) и [Создание конфигурации пакетов](../integration-services/packages/create-package-configurations.md).    
    
После проверки успешного выполнения пакетов в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]требуется создать комплект развертывания для установки пакетов. Комплект развертывания содержит файлы пакетов и другие элементы, добавленные в проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , зависимости пакетов, автоматически добавленные службами [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , а также созданную пользователем программу развертывания. Дополнительные сведения см. в статье [Create a Deployment Utility](../integration-services/packages/create-a-deployment-utility.md).    
    
После этого требуется скопировать комплект развертывания на целевой компьютер и запустить мастер установки пакета, чтобы установить пакеты и их зависимости. Пакеты устанавливаются в базе данных msdb SQL Server, а файлы поддержки и вспомогательные файлы — в файловой системе. Конфигурации, используемые развернутыми пакетами, необходимо обновить для использования новых значений, благодаря которым пакеты могут успешно выполняться в новой среде.    
    
Наконец, требуется запустить пакеты в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] с помощью программы выполнения пакетов.    
    
Целью данного учебника является демонстрация сложности некоторых вопросов развертывания, с которыми пользователю приходится сталкиваться при работе. Если по каким-либо причинам у пользователя нет возможности развернуть пакеты на другом компьютере, этот учебник можно выполнить, установив пакеты на локальном экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]в базе данных msdb и запустив их в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] на этом же экземпляре.    

**Предполагаемое время для выполнения заданий данного учебника:** 2 часа

## <a name="what-you-learn"></a>Что вы узнаете    
Новые средства, элементы управления и возможности служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] лучше всего изучать на практике. С помощью данного учебника шаг за шагом создается проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , куда затем добавляются пакеты и другие необходимые файлы. Когда проект полностью завершен, пользователь создает комплект развертывания и копирует его на целевой компьютер, куда затем устанавливаются пакеты.    
    
## <a name="prerequisites"></a>предварительные требования    
Этот учебник предназначен для пользователей, знакомых с основными операциями файловой системы, но имеющих ограниченное представление о новых возможностях служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Для лучшего понимания основных понятий служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], с которыми знакомит данный учебник, может пригодиться предварительное изучение следующего учебника по использованию служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]: [Службы SSIS: создание пакета ETL](../integration-services/ssis-how-to-create-an-etl-package.md).    
    
### <a name="on-the-source-computer"></a>Исходный компьютер

На компьютере, где создается пакет развертывания, **должны быть установлены следующие компоненты**:

- SQL Server. (Скачать бесплатный выпуск SQL Server Evaluation или Developer из [скачиваемых файлов SQL Server](https://www.microsoft.com/sql-server/sql-server-downloads).)

- Образцы данных, завершенные пакеты, конфигурации и файл сведений. Чтобы скачать образец данных и пакеты занятий в виде ZIP-файла, перейдите к файлам [учебника в составе документации по SQL Server Integration Services](https://www.microsoft.com/download/details.aspx?id=56827). Большая часть файлов в ZIP-файле доступна только для чтения во избежание непреднамеренных изменений. Для записи выходных данных в файл или его изменении может потребоваться отключить атрибут "только для чтения" в свойствах файла.

-   Образец базы данных **AdventureWorks2014**. Чтобы скачать базу данных **AdventureWorks2014**, скачайте файл `AdventureWorks2014.bak` со страницы с [образцами баз данных AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) и выполните восстановление из резервной копии.  

-   Нужно разрешение на создание и удаление таблиц в базе данных AdventureWorks.
    
-   [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md).    
    
### <a name="on-the-destination-computer"></a>Целевой компьютер

На компьютере, где будут развернуты пакеты, **должны быть установлены следующие компоненты.**    
    
- SQL Server. (Скачать бесплатный выпуск SQL Server Evaluation или Developer из [скачиваемых файлов SQL Server](https://www.microsoft.com/sql-server/sql-server-downloads).)

- Образцы данных, завершенные пакеты, конфигурации и файл сведений. Чтобы скачать образец данных и пакеты занятий в виде ZIP-файла, перейдите к файлам [учебника в составе документации по SQL Server Integration Services](https://www.microsoft.com/download/details.aspx?id=56827). Большая часть файлов в ZIP-файле доступна только для чтения во избежание непреднамеренных изменений. Для записи выходных данных в файл или его изменении может потребоваться отключить атрибут "только для чтения" в свойствах файла.

-   Образец базы данных **AdventureWorks2014**. Чтобы скачать базу данных **AdventureWorks2014**, скачайте файл `AdventureWorks2014.bak` со страницы с [образцами баз данных AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) и выполните восстановление из резервной копии.  
    
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md).    
    
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Чтобы установить службы SSIS, см. руководство по [установке Integration Services](install-windows/install-integration-services.md).
    
-   Нужно разрешение на создание и удаление таблиц в базе данных AdventureWorks и запуск пакетов SSIS в [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].    
    
-   Пользователь должен иметь разрешение на чтение и запись в таблицу `sysssispackages` в системной базе данных `msdb` [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].    
    
Если развертывание пакетов предполагается на том же самом компьютере, где создается комплект развертывания, этот компьютер должен удовлетворять требованиям как компьютера-источника, так и целевого компьютера.    
        
## <a name="lessons-in-this-tutorial"></a>Занятия этого учебника    
[Занятие 1. Подготовка к созданию пакета развертывания](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md)  .  
На этом занятии требуется развернуть ETL-решение путем создания нового проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и добавления пакетов и других необходимых файлов.    
    
[Занятие 2. Создание пакета развертывания в службах SSIS](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)    
На этом занятии требуется создать программу развертывания и убедиться, что в комплекте развертывания содержатся необходимые файлы.    
    
[Занятие 3. Установка пакетов SSIS](../integration-services/lesson-3-install-ssis-packages.md)    
На этом занятии требуется скопировать пакет развертывания на целевой компьютер, установить пакеты и запустить их.    
    

