---
title: "Проекты и решения служб Integration Services (SSIS) | Документы Майкрософт"
ms.custom: 
ms.date: 08/24/2016
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ssis.importprojectwizard.f1
helpviewer_keywords:
- projects [Integration Services], creating
- folders [Integration Services], projects
- files [Integration Services], projects
- folders [Integration Services]
- projects [Integration Services], about projects
ms.assetid: 28ea8120-0a79-4029-93f0-07d521b32bee
caps.latest.revision: "63"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: c5231ce48a81595fe3523b490ca38ea056f0c9a3
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="integration-services-ssis-projects-and-solutions"></a>Проекты и решения служб Integration Services (SSIS)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] включает среду [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , предназначенную для разработки пакетов [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
Пакеты [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] находятся в проектах. Для создания проектов служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и работы с ними необходимо установить среду [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] . Дополнительные сведения см. в статье [Установка служб Integration Services](../integration-services/install-windows/install-integration-services.md).  
  
 При создании нового проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]отображается диалоговое окно **Создание проекта** с шаблоном **Проект служб Integration Services** . Этот шаблон позволяет создать проект, в котором содержится единственный пакет.  
  
## <a name="projects-and-solutions"></a>Проекты и решения  
 Проекты сохраняются в решениях. Можно сначала создать решение, затем добавить к решению проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Если не существует никаких решений, среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] автоматически создает для пользователя решение после того, как пользователь сначала создаст проект. Решение может содержать несколько проектов различного типа.  
  
> [!TIP]  
>  По умолчанию при создании проекта в [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] решение не отображается в области **Обозреватель решений**. Чтобы изменить это поведение по умолчанию, в меню **Сервис** выберите пункт **Параметры**. В диалоговом окне **Параметры** последовательно раскройте элементы **Проекты и решения**, а затем щелкните **Общие**. На странице **Общие** выберите **Всегда показывать решение**.  

## <a name="solutions-contain-projects"></a>Решения содержат проекты  
 Решение — это контейнер, который выполняет группирование проектов и управление проектами, которые используются при разработке комплексных бизнес-решений. Решение позволяет обрабатывать несколько проектов как один модуль и сводить воедино несколько связанных проектов, задействованных в бизнес-решении.  
  
 Решения могут содержать проекты различных типов. Если возникла необходимость в использовании конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] для создания пакета [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , то разработчик работает в проекте служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , входящем в решение в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 При создании нового решения среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] добавляет папку решений в обозреватель решений и создает файлы с расширениями SLN и SUO.  
  
-   SLN-файл содержит данные о конфигурации решения и список входящих в него проектов.  
  
-   SUO-файл содержит сведения о пользовательских настройках для работы с решением.  
  
 Среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] автоматически создает решение в момент создания пользователем нового проекта, однако пользователь может создать пустое решение, а затем добавить в него проекты позже.  
   
## <a name="integration-services-projects-contain-packages"></a>Проекты служб Integration Services содержат пакеты  
 Проект представляет собой контейнер, в котором создаются пакеты служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]в проекте служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] хранятся и группируются файлы, связанные с пакетом. Например, проект содержит файлы, необходимые для создания специального извлечения, преобразования и загрузки решения ETL.  
  
 Прежде чем приступать к созданию проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , необходимо ознакомиться c основным содержимым проекта этого типа. После знакомства с содержимым проекта можно приступать к созданию и работе с проектом служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
## <a name="folders-in-integration-services-projects"></a>Папки в проектах служб Integration Services  
 На следующей диаграмме показаны папки проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 ![Папки в проекте служб Integration Services](../integration-services/media/solutionexplorer.gif "Папки в проекте служб Integration Services")  
  
 В следующей таблице описаны папки, появляющиеся в проекте служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
|Папка|Description|  
|------------|-----------------|  
|[!INCLUDE[ssIS](../includes/ssis-md.md)] Пакеты|Содержит пакеты. Дополнительные сведения см. в разделе [Пакеты служб Integration Services (SSIS)](../integration-services/integration-services-ssis-packages.md).|  
|Разное|Содержит файлы, не являющиеся файлами пакетов.|  
  
## <a name="files-in-integration-services-projects"></a>Файлы в проектах служб Integration Services  
 При добавлении в решение нового или существующего проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] создает файлы проекта, имеющие расширения Dtproj, Dtproj.user и Database.  
  
-   Файл *.dtproj содержит данные о конфигурации проекта и таких элементах, как пакеты.  
  
-   Файл *.dtproj.user содержит данные о личных настройках работы с этим проектом.  
  
-   Файл *.database содержит данные, необходимые среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] для открытия проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
## <a name="version-targeting-in-integration-services-projects"></a>Поддержка версий в проектах служб Integration Services  
 В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]можно создавать, обслуживать и выполнять пакеты, предназначенные для версий SQL Server 2016, SQL Server 2014 или SQL Server 2012.  
  
 В обозревателе решений щелкните правой кнопкой мыши проект служб Integration Services и выберите пункт **Свойства** , чтобы открыть страницу свойств проекта. На вкладке **Общие** окна **Свойства конфигурации**выберите свойство **TargetServerVersion** и затем SQL Server 2016, SQL Server 2014 или SQL Server 2012.  
  
 ![Свойство TargetServerVersion в диалоговом окне свойств проекта](../integration-services/media/targetserverversion2.png "Свойство TargetServerVersion в диалоговом окне свойств проекта")  
 
## <a name="create-a-new-integration-services-project"></a>Создание нового проекта служб Integration Services  
  
1.  Откройте среду [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  В меню **Файл** укажите **Создать**, затем нажмите **Проект**.  
  
3.  В диалоговом окне **Создание проекта** на панели **Шаблоны** выберите шаблон **Проект служб Integration Services** .  
  
     Шаблон **Проект служб Integration Services** создает проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий единственный пустой пакет.  
  
4.  (Необязательно) При необходимости измените имя и расположение проекта.  
  
     Имя решения автоматически обновляется для соответствия с именем проекта.  
  
5.  Чтобы создать отдельную папку для файла решения, выберите **Создать каталог для решения**. Это параметр по умолчанию.  
  
6.  Если на компьютере установлено программное обеспечение для системы управления версиями, выберите **Добавить в систему управления версиями**  , чтобы связать проект с этой системой управления версиями.  
  
7.  Если в качестве программного обеспечения для управления версиями используется [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, откроется диалоговое окно **Вход в Visual SourceSafe** . В окне **Вход в Visual SourceSafe**укажите имя пользователя, пароль и имя базы данных [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe. Нажмите кнопку **Обзор** , чтобы указать базу данных.  
  
    > **ПРИМЕЧАНИЕ.** Чтобы просмотреть и изменить выбранный встраиваемый модуль управления версиями, а также настроить среду управления версиями, выберите пункт **Параметры** в меню **Сервис**, а затем разверните узел **Управление версиями**.  
  
8.  Нажмите кнопку **ОК** , чтобы добавить решение в **обозреватель решений** , и добавьте проект в решение.  
  
## <a name="choose-the-target-version-of-a-project-and-its-packages"></a>Выбор целевой версии проекта и его пакетов  
  
1.  В обозревателе решений щелкните правой кнопкой мыши проект служб Integration Services и выберите пункт **Свойства** , чтобы открыть страницу свойств проекта.  
  
2.  На вкладке **Общие** окна **Свойства конфигурации**выберите свойство **TargetServerVersion** и затем SQL Server 2016, SQL Server 2014 или SQL Server 2012.  
  
     ![Свойство TargetServerVersion в диалоговом окне свойств проекта](../integration-services/media/targetserverversion2.png "Свойство TargetServerVersion в диалоговом окне свойств проекта")  
  
 Можно создавать, обслуживать и выполнять пакеты, предназначенные для версий SQL Server 2016, SQL Server 2014 или SQL Server 2012.  

## <a name="import-an-existing-project-with-the-import-project-wizard"></a>Импорт существующего проекта с помощью мастера импорта проектов
  
1.  В [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]выберите команду **Создать** > **Проект** в меню **Файл** .  
  
2.  В области **Установленные шаблоны** в окне **Создание проекта** разверните пункт **Бизнес-аналитика**и выберите **Службы Integration Services**.  
  
3.  Из списка типов проекта выберите **Мастер импорта проекта служб Integration Services** .  
  
4.  В текстовом поле **Имя** введите имя создаваемого проекта.  
  
5.  В текстовое поле **Расположение** введите путь или расположение проекта или нажмите кнопку **Обзор** , чтобы найти нужную папку.  
  
6.  В текстовом поле **Имя решения** введите имя решения.  
  
7.  Нажмите кнопку **OK** , чтобы открыть диалоговое окно **Мастер импорта проекта служб Integration Services** .  
  
8.  Нажмите кнопку **Далее** , чтобы перейти на страницу **Выбор источника данных** .  
  
9. При импортировании из файла с расширением **ISPAC** введите путь в текстовое поле **Путь** , включая имя файла. Нажмите кнопку **Обзор** , чтобы перейти к папке, где необходимо сохранить решение, введите имя файла в текстовое поле **Имя файла** и нажмите кнопку **Открыть**.  
  
     При импортировании из **Каталога служб Integration Services**введите имя экземпляра базы данных в текстовое поле **Имя сервера** или нажмите кнопку **Обзор** и выберите экземпляр базы данных, в котором содержится каталог.  
  
     Нажмите кнопку **Обзор** , которая находится рядом с текстовым полем **Путь** , раскройте папку в каталоге, выберите проект, который необходимо импортировать и нажмите **OK**.  
  
     Чтобы перейти к странице **Просмотр** , нажмите кнопку **Далее** .  
  
10. Изучите имеющиеся сведения и нажмите кнопку **Импорт** для создания проекта на основе существующего выбранного проекта.  
  
11. Необязательно. Нажмите кнопку **Сохранить отчет** , чтобы сохранить результаты в файл.  
  
12. Нажмите кнопку **Закрыть** , чтобы закрыть диалоговое окно **Мастер импорта проекта служб Integration Services** .  

## <a name="add-a-project-to-a-solution"></a>Добавление проекта к решению 
 При добавлении проекта можно создать новый пустой проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] или добавить проект, созданный для другого решения. Добавить проект к существующему решению можно, только если решение отображается в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
### <a name="add-a-new-project-to-a-solution"></a>Добавление нового проекта к решению  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте решение, к которому нужно добавить новый проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , и выполните одно из следующих действий:  
  
    -   Щелкните решение правой кнопкой, выберите пункт **Добавить**, а затем **Новый проект**.  
  
    -   В меню **Файл** выберите пункт **Добавить**, затем щелкните **Создание проекта**.  
  
2.  В диалоговом окне **Добавить новый проект** щелкните **Проект служб Integration Services** на панели **Шаблоны** .  
  
3.  Дополнительно можно изменить имя и расположение проекта.  
  
4.  Нажмите кнопку **ОК**.  
  
### <a name="add-an-existing-project-to-a-solution"></a>Добавление существующего проекта к решению  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте решение, к которому нужно добавить существующий проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , и выполните одно из следующих действий:  
  
    -   Щелкните решение правой кнопкой мыши, выберите **Добавить**, а затем щелкните **Существующий проект**.  
  
    -   В меню **Файл** выберите **Добавить**, а затем — **Существующий проект**.  
  
2.  В диалоговом окне **Добавление существующего проекта** выберите локальный проект, который нужно добавить, и щелкните **Открыть**.  
  
3.  Проект будет добавлен в папку решений **Обозревателя решений**.  
  
## <a name="remove-a-project-from-a-solution"></a>Удаление проекта из решения
 Удалить проект из решения можно, только если решение отображается в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. После отображения решения можно удалить все проекты, кроме одного. Когда остается только один проект, среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] больше не отображает папку решения и удалить последний проект становится невозможным.  
   
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]нужно открыть решение, из которого необходимо удалить проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
2.  В обозревателе решений щелкните правой кнопкой мыши проект и выберите команду **Выгрузить проект**.  
  
3.  Чтобы подтвердить удаление, нажмите кнопку **ОК** .  

## <a name="add-an-item-to-a-project"></a>Добавление элемента в проект  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте решение с проектом служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , к которому требуется добавить элемент.  
  
2.  В обозревателе решений щелкните проект правой кнопкой мыши, укажите **Добавить**и выполните одно из следующих действий:  
  
    -   Щелкните **Новый элемент**, затем шаблон на панели **Шаблоны** в диалоговом окне **Добавить новый элемент** .  
  
    -   Щелкните **Существующий элемент**, в диалоговом окне **Добавить существующий элемент** перейдите к элементу, который необходимо добавить к проекту, и щелкните кнопку **Добавить**.  
  
3.  Новый элемент появляется в соответствующей папке в обозревателе решений.  

## <a name="copy-project-items"></a>Копирование элементов проекта  
Объекты можно копировать внутри проекта [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] или из одного проекта [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в другой. Также вы можете скопировать объекты между другими типами проектов [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] и [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Чтобы можно было выполнить копирование между проектами, они должны быть частью одного решения среды [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] .

1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] или решение, с которым собираетесь работать.  
  
2.  Разверните проект и папку, из которой будет выполняться копирование.  
  
3.  Щелкните правой кнопкой мыши элемент и выберите **Копировать**.  
  
4.  Щелкните правой кнопкой мыши проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], в который будет выполняться копирование, и выберите **Вставить**.  
  
     Элементы автоматически копируются в нужную папку. При копировании элементов в проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , которые не являются пакетами, элементы копируются в папку **Разное** .  
     
