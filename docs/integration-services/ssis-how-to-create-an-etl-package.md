---
title: "Службы SSIS: создание пакета ETL | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
helpviewer_keywords:
- SSIS, tutorials
- packages [Integration Services], tutorials
- Integration Services, tutorials
- SQL Server Integration Services, tutorials
- logs [Integration Services], tutorials
- walkthroughs [Integration Services]
ms.assetid: d6d5bb1f-4cb1-4605-9cd6-f60b858382c4
caps.latest.revision: "38"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 1196fdf3fe4e37faa0da98a0cd44c3de3e0d46e7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="ssis-how-to-create-an-etl-package"></a>Службы SSIS: создание пакета ETL

 > Содержимое, связанное с предыдущими версиями SQL Server, см. в разделе [Учебник по службам SSIS. Создание простого ETL-пакета](https://msdn.microsoft.com/library/ms169917(SQL.120).aspx).

[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) представляют собой платформу для создания высокопроизводительных решений интеграции данных, включая пакеты ETL для хранения данных. Службы SSIS содержат графические инструменты и мастера для построения и отладки пакетов; задачи для выполнения функций рабочего процесса, таких как операции FTP, выполнение инструкций SQL и отправка сообщений электронной почты; источники данных и назначения для извлечения и загрузки данных; преобразования для очистки, статистической обработки, слияния и копирования данных; службу управления, службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] для администрирования выполнения и хранения пакетов, а также API-интерфейсы для программирования объектной модели служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
Из этого руководства вы узнаете, как использовать конструктор [!INCLUDE[ssIS](../includes/ssis-md.md)] для создания простого пакета служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Этот пакет получает данные из неструктурированного файла, преобразует их, а затем вставляет преобразованные данные в таблицу фактов. На следующих занятиях пакет будет расширен, чтобы продемонстрировать циклическую обработку, конфигурацию пакетов, ведение журнала и поток ошибок.  
  
При установке примера данных, используемых в этом руководстве, устанавливаются также полные версии пакетов, которые требуется создать на занятиях, описанных в этом руководстве. Используя завершенные пакеты, пользователь может при желании пропустить начало учебника и приступить к работе с более позднего занятия. Если вы впервые работаете с пакетами или новой средой разработки, мы рекомендуем начать с занятия 1.  
  
## <a name="what-you-learn"></a>Что вы узнаете  
Новые средства, элементы управления и возможности служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] лучше всего изучать на практике. В этом руководстве с помощью конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] вы создадите простой пакет ETL, который включает циклическую обработку, конфигурацию, логику потока ошибок и ведение журнала.  
  
## <a name="requirements"></a>Требования  
Этот учебник предназначен для пользователей, знакомых с основными операциями с базами данных, но имеющих ограниченное представление о новых функциях служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
Для работы с этим учебником в системе должны быть установлены следующие компоненты:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с базой данных **AdventureWorksDW2012** . В целях повышения безопасности образцы баз данных по умолчанию не устанавливаются. Для загрузки базы данных **AdventureWorksDW2012** перейдите по ссылке [Adventure Works для SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=275026).  
  
    > [!IMPORTANT]  
    > При присоединении базы данных (файл \*.mdf) по умолчанию среда [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] выполняет поиск LDF-файла. Удалите LDF-файл вручную, прежде чем нажать кнопку "ОК" в диалоговом окне **Присоединение баз данных**.  
    >   
    > Дополнительные сведения о присоединении баз данных см. в разделе [Attach a Database](../relational-databases/databases/attach-a-database.md).  
  
-   Образцы данных. Образцы данных включаются в состав с пакетами занятий по службам [!INCLUDE[ssIS](../includes/ssis-md.md)] . Чтобы скачать пример данных и пакеты занятий, сделайте следующее:  
  
    1.  Перейдите к [образцам продуктов служб Integration Services](http://go.microsoft.com/fwlink/?LinkId=275027).  
  
    2.  Перейдите на вкладку **DOWNLOADS** .  
  
    3.  Щелкните файл SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
## <a name="lessons-in-this-tutorial"></a>Занятия этого учебника  
[Занятие 1. Создание проекта и основного пакета с помощью служб SSIS](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md)  
На этом занятии вы создадите простой пакет ETL, который получает данные из неструктурированного файла, преобразует их с использованием преобразования "Уточняющий запрос" и загружает результат в целевую таблицу фактов.  
  
[Занятие 2. Добавление циклов с помощью служб SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md)  
На этом занятии будет расширен пакет, созданный на занятии 1, чтобы использовать новые возможности циклической обработки для извлечения нескольких неструктурированных файлов в едином процессе потока данных.  
  
[Занятие 3. Добавление журналов с помощью служб SSIS](../integration-services/lesson-3-add-logging-with-ssis.md)  
На этом занятии вы расширите пакет, созданный на занятии 2, чтобы использовать новые возможности ведения журнала.  
  
[Занятие 4. Добавление перенаправления потока ошибок с помощью служб SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
На этом занятии вы расширите пакет, созданный на занятии 3, чтобы использовать новые конфигурации вывода ошибок.  
  
[Занятие 5. Добавление конфигураций пакетов SSIS в модель развертывания пакетов](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
На этом занятии вы расширите пакет, созданный на занятии 4, чтобы использовать новые параметры конфигурации пакета.  
  
[Занятие 6. Использование параметров в модели развертывания проекта в службах SSIS](../integration-services/lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
На этом занятии вы расширите пакет, созданный на занятии 5, чтобы воспользоваться преимуществами новых параметров в модели развертывания проекта.  
  
  
  
