---
title: "Занятие 5: Добавление конфигураций пакетов служб SSIS в модель развертывания пакета | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 1c10dd54-67cb-4b63-9e4d-aa6ff0452ecb
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1a16217f90b9120993663d9046c8178e62451111
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="lesson-5-add-ssis-package-configurations-for-the-package-deployment-model"></a>Занятие 5. Добавление конфигураций пакетов SSIS в модель развертывания пакетов
С помощью конфигураций пакета можно задавать исполняемые свойства и переменные вне среды разработки. Конфигурации дают возможность разрабатывать пакеты, обладающие гибкостью и простотой распространения и развертывания. [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] предлагает следующие типы конфигурации:  
  
-   XML-файл конфигурации  
  
-   Переменная среды  
  
-   Параметр реестра  
  
-   Переменная родительского пакета  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table  
  
На этом занятии требуется изменить простой пакет [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , созданный на [занятии 4: добавление перенаправления потока ошибок с помощью служб SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md) , чтобы использовать модель развертывания пакетов и воспользоваться преимуществами конфигураций пакетов. Также можно скопировать пакет из завершенного урока 4, который включен в учебник. В мастере настройки пакета предстоит создать XML-конфигурацию, которая обновляет свойство **Directory** контейнера "цикл по каждому элементу" с помощью переменной уровня пакета, сопоставленной со свойством Directory. После создания файла конфигурации следует изменить значение переменной вне среды разработки и создать в измененном свойстве ссылку на новую папку с образцами данных. При повторном выполнении пакета файл конфигурации заполняет значение переменной, которая, в свою очередь, обновляет свойство **Directory**. В итоге пакет последовательно проходит все файлы в новой, а не исходной папке данных, жестко закодированной в пакете.  
  
> [!IMPORTANT]  
> Для выполнения упражнений этого учебника потребуется образец базы данных **AdventureWorksDW2012** . Дополнительные сведения об установке и развертывании **AdventureWorksDW2012**см. в разделе [Проект образцов продуктов службы Reporting Services на сайте CodePlex](http://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## <a name="lesson-tasks"></a>Задачи занятия  
Это занятие содержит следующие задачи.  
  
-   [Шаг 1: Копирование пакета занятия 4](../integration-services/lesson-5-1-copying-the-lesson-4-package.md)  
  
-   [Шаг 2: Включение и настройка конфигурации пакетов](../integration-services/lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
-   [Шаг 3: Изменение значения конфигурации свойства Directory](../integration-services/lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
-   [Шаг 4: Проверка учебного пакета занятия 5](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
  
-   [Шаг 1: Копирование пакета занятия 4](../integration-services/lesson-5-1-copying-the-lesson-4-package.md)  
  
  
  

