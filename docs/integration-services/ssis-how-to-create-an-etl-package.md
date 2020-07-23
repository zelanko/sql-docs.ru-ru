---
title: 'Службы SSIS: создание пакета ETL | Документы Майкрософт'
ms.custom: ''
ms.date: 08/20/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: quickstart
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
ms.openlocfilehash: d0365939d33b1ef6e0a4c179cdedddb4c3981763
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86921968"
---
# <a name="ssis-how-to-create-an-etl-package"></a>Службы SSIS: создание пакета ETL

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



Из этого руководства вы узнаете, как использовать конструктор [!INCLUDE[ssIS](../includes/ssis-md.md)] для создания простого пакета служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Этот пакет получает данные из неструктурированного файла, преобразует их, а затем вставляет преобразованные данные в таблицу фактов. На следующих занятиях пакет будет расширен, чтобы продемонстрировать циклическую обработку, конфигурацию пакетов, ведение журнала и поток ошибок.  
  
При установке примера данных, используемых в этом руководстве, устанавливаются также полные версии пакетов, которые требуется создать на занятиях, описанных в этом руководстве. Используя завершенные пакеты, пользователь может при желании пропустить начало учебника и приступить к работе с более позднего занятия. Если вы впервые работаете с пакетами или новой средой разработки, мы рекомендуем начать с занятия 1.  

## <a name="what-is-sql-server-integration-services-ssis"></a>Что представляют собой службы SQL Server Integration Services (SSIS)?

Службы [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) представляют собой платформу для создания высокопроизводительных решений интеграции данных, включая пакеты ETL для хранения данных. Службы SSIS содержат графические инструменты и мастера для построения и отладки пакетов; задачи для выполнения функций рабочего процесса, таких как операции FTP, выполнение инструкций SQL и отправка сообщений электронной почты; источники данных и назначения для извлечения и загрузки данных; преобразования для очистки, статистической обработки, слияния и копирования данных; базу данных управления, `SSISDB` для администрирования выполнения и хранения пакетов, а также API для программирования объектной модели [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  

## <a name="what-you-learn"></a>Что вы узнаете  
Новые средства, элементы управления и возможности служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] лучше всего изучать на практике. В этом руководстве с помощью конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] вы создадите простой пакет ETL, который включает циклическую обработку, конфигурацию, логику потока ошибок и ведение журнала.  
  
## <a name="prerequisites"></a>предварительные требования  
Этот учебник предназначен для пользователей, знакомых с основными операциями с базами данных, но имеющих ограниченное представление о новых функциях служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  

Для работы с этим руководством проверьте установку следующих компонентов:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Чтобы установить SQL Server и служб SSIS, см. руководство по [установке Integration Services](install-windows/install-integration-services.md).

-   Пример базы данных **AdventureWorksDW2012**. Чтобы скачать базу данных **AdventureWorksDW2012**, скачайте файл `AdventureWorksDW2012.bak` со страницы с [образцами баз данных AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) и выполните восстановление из резервной копии.  

-   Файлы с **примерами данных**. Образцы данных включаются в состав с пакетами занятий по службам [!INCLUDE[ssIS](../includes/ssis-md.md)] . Чтобы скачать образец данных и пакеты занятий в виде ZIP-файла, перейдите к файлам [учебника в составе документации по SQL Server Integration Services](https://www.microsoft.com/download/details.aspx?id=56827).

    - Большая часть файлов в ZIP-файле доступна только для чтения во избежание непреднамеренных изменений. Для записи выходных данных в файл или его изменении может потребоваться отключить атрибут "только для чтения" в свойствах файла.
    - При использовании пакетов примеров предполагается, что файлы данных находятся в папке `C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Creating a Simple ETL Package`. Если распаковать скачанные файлы в другое расположение, может потребоваться обновить путь к файлу в нескольких местах в пакетах с примерами.

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
  
  
  
