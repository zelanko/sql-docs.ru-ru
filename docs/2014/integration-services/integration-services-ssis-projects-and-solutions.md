---
title: (SSIS) проекты служб Integration Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Integration Services], creating
- folders [Integration Services], projects
- files [Integration Services], projects
- folders [Integration Services]
- projects [Integration Services], about projects
ms.assetid: 28ea8120-0a79-4029-93f0-07d521b32bee
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c3ea3adf8d22cb65127fca6e187bf4887051fff2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48110214"
---
# <a name="integration-services-ssis-projects"></a>Проекты служб Integration Services (SSIS)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] включает среду [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , предназначенную для разработки пакетов [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 При развертывании пакетов в базу данных [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или хранилище пакетов [!INCLUDE[ssIS](../includes/ssis-md.md)] для управления пакетами используются службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] доступна только в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Дополнительные сведения о службе см. в разделе [Службы Integration Services (SSIS)](service/integration-services-service-ssis-service.md). Дополнительные сведения о развертывании пакетов см. в разделе [развертывания пакета &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md).  
  
 При развертывании проектов служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на сервер [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] для управления проектами используются представления и хранимые процедуры Transact-SQL в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Дополнительные сведения о развертывании проектов см. в разделе [Развертывание проектов и пакетов](packages/deploy-integration-services-ssis-projects-and-packages.md). Дополнительные сведения о сервере [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] см. в разделе [Службы Integration Services (SSIS)](catalog/integration-services-ssis-server-and-catalog.md).  
  
 Общие сведения о [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] и [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] см. в разделе [Службы Integration Services (SSIS) и среды Studio](integration-services-ssis-development-and-management-tools.md).  
  
## <a name="understanding-integration-services-projects"></a>Основные сведения о проектах служб Integration Services  
 Проект представляет собой контейнер, в котором создаются пакеты служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]в проекте служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] хранятся и группируются файлы, связанные с пакетом. Например, проект содержит файлы, необходимые для создания специального извлечения, преобразования и загрузки решения ETL.  
  
 Прежде чем приступать к созданию проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , необходимо ознакомиться c основным содержимым проекта этого типа. После знакомства с содержимым проекта можно приступать к созданию и работе с проектом служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
### <a name="folders-in-integration-services-projects"></a>Папки в проектах служб Integration Services  
 На следующей диаграмме показаны папки проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 ![Папки в проекте служб Integration Services](media/solutionexplorer.gif "Папки в проекте служб Integration Services")  
  
 В следующей таблице описаны папки, появляющиеся в проекте служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
|Папка|Описание|  
|------------|-----------------|  
|[!INCLUDE[ssIS](../includes/ssis-md.md)] Пакеты|Содержит пакеты. Дополнительные сведения см. в разделе [Пакеты служб Integration Services (SSIS)](../../2014/integration-services/integration-services-ssis-packages.md).|  
|Разное|Содержит файлы, не являющиеся файлами пакетов.|  
  
### <a name="files-in-integration-services-projects"></a>Файлы в проектах служб Integration Services  
 При добавлении в решение нового или существующего проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] создает файлы проекта, имеющие расширения Dtproj, Dtproj.user и Database.  
  
-   Файл *.dtproj содержит данные о конфигурации проекта и таких элементах, как пакеты.  
  
-   Файл *.dtproj.user содержит данные о личных настройках работы с этим проектом.  
  
-   Файл *.database содержит данные, необходимые среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] для открытия проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
## <a name="understanding-solutions"></a>Основные сведения о решениях  
 Решение — это контейнер, который выполняет группирование проектов и управление проектами, которые используются при разработке комплексных бизнес-решений. Решение позволяет обрабатывать несколько проектов как один модуль и сводить воедино несколько связанных проектов, задействованных в бизнес-решении.  
  
 Решения могут содержать проекты различных типов. Если возникла необходимость в использовании конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] для создания пакета [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , то разработчик работает в проекте служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , входящем в решение в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 При создании нового решения среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] добавляет папку решений в обозреватель решений и создает файлы с расширениями SLN и SUO.  
  
-   SLN-файл содержит данные о конфигурации решения и список входящих в него проектов.  
  
-   SUO-файл содержит сведения о пользовательских настройках для работы с решением.  
  
 Среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] автоматически создает решение в момент создания пользователем нового проекта, однако пользователь может создать пустое решение, а затем добавить в него проекты позже.  
  
> [!NOTE]  
>  По умолчанию при создании нового проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] решение не отображается в панели **Обозреватель решений**. Чтобы изменить это поведение по умолчанию, в меню **Сервис** выберите пункт **Параметры**. В диалоговом окне **Параметры** последовательно раскройте элементы **Проекты и решения**, а затем щелкните **Общие**. На странице **Общие** выберите **Всегда показывать решение**.  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Добавление или удаление проектом служб Integration Services из решения](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)  
  
 [Создание нового проекта служб Integration Services](../../2014/integration-services/create-a-new-integration-services-project.md)  
  
 [Добавление элемента к проекту служб Integration Services](../../2014/integration-services/add-an-item-to-an-integration-services-project.md)  
  
 [Копирование элементов проекта](../../2014/integration-services/copy-project-items.md)  
  
## <a name="related-content"></a>См. также  
 [Разработка проекта служб Integration Services](../../2014/integration-services/development-of-an-integration-services-project.md)  
  
  
