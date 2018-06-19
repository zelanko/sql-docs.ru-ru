---
title: 'Службы SSIS: создание пакета ETL | Документы Майкрософт'
ms.custom: ''
ms.date: 04/17/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- SSIS, tutorials
- packages [Integration Services], tutorials
- Integration Services, tutorials
- SQL Server Integration Services, tutorials
- logs [Integration Services], tutorials
- walkthroughs [Integration Services]
ms.assetid: d6d5bb1f-4cb1-4605-9cd6-f60b858382c4
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 234b5a72f611ab2ac85db862c04af7d749e089ab
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35411736"
---
# <a name="ssis-how-to-create-an-etl-package"></a>Службы SSIS: создание пакета ETL

 > Содержимое, связанное с предыдущими версиями SQL Server, см. в разделе [Учебник по службам SSIS. Создание простого ETL-пакета](https://msdn.microsoft.com/library/ms169917(SQL.120).aspx).

Из этого руководства вы узнаете, как использовать конструктор [!INCLUDE[ssIS](../includes/ssis-md.md)] для создания простого пакета служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Этот пакет получает данные из неструктурированного файла, преобразует их, а затем вставляет преобразованные данные в таблицу фактов. На следующих занятиях пакет будет расширен, чтобы продемонстрировать циклическую обработку, конфигурацию пакетов, ведение журнала и поток ошибок.  
  
При установке примера данных, используемых в этом руководстве, устанавливаются также полные версии пакетов, которые требуется создать на занятиях, описанных в этом руководстве. Используя завершенные пакеты, пользователь может при желании пропустить начало учебника и приступить к работе с более позднего занятия. Если вы впервые работаете с пакетами или новой средой разработки, мы рекомендуем начать с занятия 1.  

## <a name="what-is-sql-server-integration-services-ssis"></a>Что представляют собой службы SQL Server Integration Services (SSIS)?

[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) представляют собой платформу для создания высокопроизводительных решений интеграции данных, включая пакеты ETL для хранения данных. Службы SSIS содержат графические инструменты и мастера для построения и отладки пакетов; задачи для выполнения функций рабочего процесса, таких как операции FTP, выполнение инструкций SQL и отправка сообщений электронной почты; источники данных и назначения для извлечения и загрузки данных; преобразования для очистки, статистической обработки, слияния и копирования данных; службу управления, службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] для администрирования выполнения и хранения пакетов, а также API-интерфейсы для программирования объектной модели служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  

## <a name="what-you-learn"></a>Что вы узнаете  
Новые средства, элементы управления и возможности служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] лучше всего изучать на практике. В этом руководстве с помощью конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] вы создадите простой пакет ETL, который включает циклическую обработку, конфигурацию, логику потока ошибок и ведение журнала.  
  
## <a name="requirements"></a>Требования  
Этот учебник предназначен для пользователей, знакомых с основными операциями с базами данных, но имеющих ограниченное представление о новых функциях служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  

> [!IMPORTANT]
> Образцы файлов, необходимые для работы с этим учебником, были перенесены в новое место. Приносим извинения за причиненные неудобства. Мы опубликовали эти файлы в новом месте и обновили в этой статье ссылки для скачивания.

Для работы с этим учебником в системе должны быть установлены следующие компоненты:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с базой данных **AdventureWorksDW2012** . Чтобы скачать базу данных **AdventureWorksDW2012**, скачайте файл `AdventureWorksDW2012.bak` со страницы с [образцами баз данных AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) и выполните восстановление из резервной копии.  

-   Образцы данных. Образцы данных включаются в состав с пакетами занятий по службам [!INCLUDE[ssIS](../includes/ssis-md.md)] . Чтобы скачать образец данных и пакеты занятий в виде ZIP-файла, перейдите на страницу скачивания материалов к [учебнику по созданию простого пакета ETL в составе документации по SQL Server Integration Services](https://www.microsoft.com/download/details.aspx?id=56827).  

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
  
  
  
