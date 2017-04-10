---
title: "Проекты и решения служб Integration Services (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "08/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.importprojectwizard.f1"
helpviewer_keywords: 
  - "проекты [Integration Services], создание"
  - "папки [Integration Services], проекты"
  - "файлы [Integration Services], проекты"
  - "папки [службы Integration Services]"
  - "проекты [Integration Services], информация о проектах"
ms.assetid: 28ea8120-0a79-4029-93f0-07d521b32bee
caps.latest.revision: 63
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 62
---
# Проекты и решения служб Integration Services (SSIS)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] включает среду [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], предназначенную для разработки пакетов [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 При развертывании пакетов в базу данных [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или хранилище пакетов [!INCLUDE[ssIS](../includes/ssis-md.md)] для управления пакетами используются службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] доступна только в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Дополнительные сведения о службе см. в разделе [Службы Integration Services (SSIS)](../integration-services/service/integration-services-service-ssis-service.md). Дополнительные сведения о развертывании пакетов см. в разделе [Устаревшее развертывание пакетов (службы SSIS)](../integration-services/packages/legacy-package-deployment-ssis.md).  
  
 При развертывании проектов служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на сервер [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] для управления проектами используются представления и хранимые процедуры Transact-SQL в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Дополнительные сведения о развертывании проектов см. в разделе [Развертывание проектов и пакетов](https://msdn.microsoft.com/library/hh213290.aspx). Дополнительные сведения о сервере [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] см. в разделе [Службы Integration Services (SSIS)](https://msdn.microsoft.com/library/ms137731.aspx).  
  
 Общие сведения о [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] и [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] см. в разделе [Службы Integration Services &#40;SSIS&#41; и средства управления](https://msdn.microsoft.com/library/ms140028.aspx)%20and%20Studio%20Environments.md).  
  
## Проекты служб Integration Services содержат пакеты  
 Проект представляет собой контейнер, в котором создаются пакеты служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] в проекте служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] хранятся и группируются файлы, связанные с пакетом. Например, проект содержит файлы, необходимые для создания специального извлечения, преобразования и загрузки решения ETL.  
  
 Прежде чем приступать к созданию проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], необходимо ознакомиться c основным содержимым проекта этого типа. После знакомства с содержимым проекта можно приступать к созданию и работе с проектом служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## Папки в проектах служб Integration Services  
 На следующей диаграмме показаны папки проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 ![Папки в проекте служб Integration Services](../integration-services/media/solutionexplorer.gif "Папки в проекте служб Integration Services")  
  
 В следующей таблице описаны папки, появляющиеся в проекте служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
|Папка|Description|  
|------------|-----------------|  
|[!INCLUDE[ssIS](../includes/ssis-md.md)] Пакеты|Содержит пакеты. Дополнительные сведения см. в разделе [Пакеты служб Integration Services (SSIS)](../integration-services/integration-services-ssis-packages.md).|  
|Разное|Содержит файлы, не являющиеся файлами пакетов.|  
  
## Файлы в проектах служб Integration Services  
 При добавлении в решение нового или существующего проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] создает файлы проекта, имеющие расширения Dtproj, Dtproj.user и Database.  
  
-   Файл *.dtproj содержит данные о конфигурации проекта и таких элементах, как пакеты.  
  
-   Файл *.dtproj.user содержит данные о личных настройках работы с этим проектом.  
  
-   Файл *.database содержит данные, необходимые среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] для открытия проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## Поддержка версий в проектах служб Integration Services  
 В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] можно создавать, обслуживать и выполнять пакеты, предназначенные для версий SQL Server 2016, SQL Server 2014 или SQL Server 2012.  
  
 В обозревателе решений щелкните правой кнопкой мыши проект служб Integration Services и выберите пункт **Свойства**, чтобы открыть страницу свойств проекта. На вкладке **Общие** окна **Свойства конфигурации**выберите свойство **TargetServerVersion** и затем SQL Server 2016, SQL Server 2014 или SQL Server 2012.  
  
 ![TargetServerVersion property in project properties dialog box](../integration-services/media/targetserverversion2.png "TargetServerVersion property in project properties dialog box")  
  
## Решения содержат проекты  
 Решение — это контейнер, который выполняет группирование проектов и управление проектами, которые используются при разработке комплексных бизнес-решений. Решение позволяет обрабатывать несколько проектов как один модуль и сводить воедино несколько связанных проектов, задействованных в бизнес-решении.  
  
 Решения могут содержать проекты различных типов. Если возникла необходимость в использовании конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] для создания пакета [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], то разработчик работает в проекте служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], входящем в решение в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 При создании нового решения среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] добавляет папку решений в обозреватель решений и создает файлы с расширениями SLN и SUO.  
  
-   SLN-файл содержит данные о конфигурации решения и список входящих в него проектов.  
  
-   SUO-файл содержит сведения о пользовательских настройках для работы с решением.  
  
 Среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] автоматически создает решение в момент создания пользователем нового проекта, однако пользователь может создать пустое решение, а затем добавить в него проекты позже.  
  
> **ПРИМЕЧАНИЕ.** По умолчанию при создании нового проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] решение не отображается в панели **Обозреватель решений**. Чтобы изменить это поведение по умолчанию, в меню **Сервис** выберите пункт **Параметры**. В диалоговом окне **Параметры** последовательно раскройте элементы **Проекты и решения**, а затем щелкните **Общие**. На странице **Общие** выберите **Всегда показывать решение**.  
  
## Связанные задачи  
 [Добавление или удаление проектом служб Integration Services из решения](../Topic/Add%20or%20Remove%20an%20Integration%20Services%20Project%20in%20a%20Solution.md)  
  
 [Создание нового проекта служб Integration Services](../Topic/Create%20a%20New%20Integration%20Services%20Project.md)  
  
 [Добавление элемента к проекту служб Integration Services](../Topic/Add%20an%20Item%20to%20an%20Integration%20Services%20Project.md)  
  
 [Копирование элементов проекта](../Topic/Copy%20Project%20Items.md)  
  
## См. также  
 [Разработка проекта служб Integration Services](../Topic/Development%20of%20an%20Integration%20Services%20Project.md)  
  
  