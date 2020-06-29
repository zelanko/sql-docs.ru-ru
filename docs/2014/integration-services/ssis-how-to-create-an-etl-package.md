---
title: 'Учебник по службам SSIS: создание простого ETL-пакета | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS, tutorials
- packages [Integration Services], tutorials
- Integration Services, tutorials
- SQL Server Integration Services, tutorials
- logs [Integration Services], tutorials
- walkthroughs [Integration Services]
ms.assetid: d6d5bb1f-4cb1-4605-9cd6-f60b858382c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a515ed058f35fe3a6d7e042c61b23bbda7429b3d
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85421131"
---
# <a name="ssis-tutorial-creating-a-simple-etl-package"></a>Учебник по службам SSIS. Создание простого ETL-пакета
  [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) — это платформа для создания высокопроизводительных решений по интеграции данных, включая пакеты извлечения, преобразования и загрузки (ETL) для хранения данных. Службы SSIS содержат графические инструменты и мастера для построения и отладки пакетов; задачи для выполнения функций рабочего процесса, таких как операции FTP, выполнение инструкций SQL и отправка сообщений электронной почты; источники данных и назначения для извлечения и загрузки данных; преобразования для очистки, статистической обработки, слияния и копирования данных; службу управления, службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] для администрирования выполнения и хранения пакетов, а также API-интерфейсы для программирования объектной модели служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 В этом руководстве вы узнаете, как использовать [!INCLUDE[ssIS](../includes/ssis-md.md)] конструктор для создания простого [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] пакета. Этот пакет получает данные из неструктурированного файла, преобразует их, а затем вставляет преобразованные данные в таблицу фактов. На следующих занятиях пакет будет расширен, чтобы продемонстрировать циклическую обработку, конфигурацию пакетов, ведение журнала и поток ошибок.  
  
 При установке данных образца, используемых в данном учебнике, устанавливаются также полные версии пакетов, которые требуется создать на занятиях данного учебника. Используя завершенные пакеты, пользователь может при желании пропустить начало учебника и приступить к работе с более позднего занятия. В случае первого знакомства с пакетами или новой средой разработки рекомендуется начинать с занятия 1.  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
 Лучшим способом знакомства с новыми инструментами, элементами управления и функциями, доступными в, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] является их использование. В этом учебнике с помощью конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] будет создан простой пакет ETL, который включает циклическую обработку, конфигурацию, логику потока ошибок и ведение журнала.  
  
## <a name="requirements"></a>Требования  
 Этот учебник предназначен для пользователей, знакомых с основными операциями с базами данных, но имеющих ограниченный доступ к новым функциям, доступным в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
 Для работы с этим учебником в системе должны быть установлены следующие компоненты:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с базой данных **AdventureWorksDW2012** . В целях повышения безопасности образцы баз данных по умолчанию не устанавливаются. Для загрузки базы данных **AdventureWorksDW2012** перейдите по ссылке [Adventure Works для SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=275026).  
  
    > [!IMPORTANT]  
    >  При присоединении базы данных (файл\*.mdf) по умолчанию среда [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] выполняет поиск LDF-файла. Необходимо вручную удалить LDF-файл перед тем, как нажать кнопку «ОК» в диалоговом окне **Присоединение баз данных** .  
    >   
    >  Дополнительные сведения о присоединении баз данных см. в разделе [Attach a Database](../relational-databases/databases/attach-a-database.md).  
  
-   Образцы данных. Образцы данных включаются в состав с пакетами занятий по службам [!INCLUDE[ssIS](../includes/ssis-md.md)] . Чтобы загрузить образцы данных и пакеты занятий выполните следующие действия.  
  
    1.  Перейдите к [образцам продуктов служб Integration Services](https://go.microsoft.com/fwlink/?LinkId=275027).  
  
    2.  Перейдите на вкладку **Downloads (загрузки** ).  
  
    3.  Щелкните файл SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip.  
  
## <a name="lessons-in-this-tutorial"></a>Занятия этого учебника  
 [Урок 1. Создание проекта и основного пакета](lesson-1-create-a-project-and-basic-package-with-ssis.md)  
 На этом занятии будет создан простой пакет ETL, который получает данные из неструктурированного файла, преобразует их с использованием преобразования «Уточняющий запрос» и загружает результат в целевую таблицу фактов.  
  
 [Занятие 2. Добавление циклов](lesson-2-adding-looping-with-ssis.md)  
 На этом занятии будет расширен пакет, созданный на занятии 1, что позволит использовать новые возможности циклической обработки для извлечения нескольких неструктурированных файлов в едином процессе потока данных.  
  
 [Урок 3. Добавление журнала](lesson-3-add-logging-with-ssis.md)  
 На этом занятии созданный на занятии 2 пакет будет расширен, чтобы использовать новые возможности ведения журнала.  
  
 [Урок 4. Добавление перенаправления потока ошибок](lesson-4-add-error-flow-redirection-with-ssis.md)  
 На этом занятии созданный на занятии 3 пакет будет расширен, что позволит использовать новые конфигурации вывода ошибок.  
  
 [Урок 5. Добавление конфигураций пакетов в модель развертывания пакета](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
 На этом занятии созданный на занятии 4 пакет будет расширен, что позволит использовать новые параметры конфигурации пакета.  
  
 [Занятие 6: Использование параметров в модели развертывания проекта](lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
 На этом занятии будет расширен пакет, созданный на занятии 5, чтобы воспользоваться преимуществами новых параметров в модели развертывания проекта.  
  
  
