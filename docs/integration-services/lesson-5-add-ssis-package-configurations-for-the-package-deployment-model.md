---
title: 'Занятие 5.: Добавление конфигураций пакетов SQL Server Integration Services в модель развертывания пакета | Документация Майкрософт'
ms.custom: ''
ms.date: 01/08/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 1c10dd54-67cb-4b63-9e4d-aa6ff0452ecb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6246183a4a928e1813125676753c827bf20cf8c5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65721147"
---
# <a name="lesson-5-add-ssis-package-configurations-for-the-package-deployment-model"></a>Занятие 5.: Добавление конфигураций пакетов SQL Server Integration Services в модель развертывания пакета

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



С помощью конфигураций пакетов можно задавать свойства и переменные времени выполнения вне среды разработки. Конфигурации дают возможность разрабатывать пакеты, обладающие гибкостью и простотой распространения и развертывания. [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] предусмотрены следующие типы конфигурации:  
  
-   XML-файл конфигурации  
  
-   Переменная среды  
  
-   Параметр реестра  
  
-   Переменная родительского пакета  
  
-   Таблица [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
На этом занятии пакет [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], созданный на [занятии 4: добавление перенаправления потока ошибок с помощью служб SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md), будет изменен для использования модели развертывания пакета, что позволит получить преимущества конфигураций пакетов. Вы также можете скопировать готовый пакет занятия 4, который включен в учебник. 

В мастере настройки пакета предстоит создать XML-конфигурацию, которая обновляет свойство **Каталог** контейнера "Цикл ForEach". Будет использоваться переменная уровня пакета, сопоставленная со свойством **Каталог**. После создания файла конфигурации следует изменить значение переменной вне среды разработки на путь к новой папке с образцами данных. При повторном выполнении пакета файл конфигурации заполняет значение переменной, которая, в свою очередь, обновляет свойство **Directory** . Затем пакет перебирает все файлы в новой, а не исходной, жестко заданной папке данных.  
  
> [!NOTE]
> Ознакомьтесь с [предварительными требованиями для урока 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites), если вы еще не сделали этого.
  
## <a name="lesson-tasks"></a>Задачи занятия  
Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Копирование пакета занятия 4](../integration-services/lesson-5-1-copying-the-lesson-4-package.md)  
  
-   [Шаг 2. Активация и настройка конфигураций пакетов](../integration-services/lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
-   [Шаг 3. Изменение значения конфигурации свойства "Каталог"](../integration-services/lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
-   [Шаг 4. Тестирование пакета занятия 5](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
  
-   [Шаг 1. Копирование пакета занятия 4](../integration-services/lesson-5-1-copying-the-lesson-4-package.md)  
  
  
  
