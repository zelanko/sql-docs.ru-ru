---
title: Занятие 5. Добавление конфигураций пакетов в модель развертывания пакетов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c10dd54-67cb-4b63-9e4d-aa6ff0452ecb
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2e2d995b06d30157ae46669696e9f8d4095a4646
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53362206"
---
# <a name="lesson-5-adding-package-configurations-for-the-package-deployment-model"></a>Занятие 5. Добавление конфигураций пакетов в модель развертывания пакета
  С помощью конфигураций пакета можно задавать исполняемые свойства и переменные вне среды разработки. Конфигурации дают возможность разрабатывать пакеты, обладающие гибкостью и простотой распространения и развертывания. [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] предусмотрены следующие типы конфигурации:  
  
-   XML-файл конфигурации  
  
-   Переменная среды  
  
-   Параметр реестра  
  
-   Переменная родительского пакета  
  
-   Таблица [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
 На этом занятии будет изменить простой [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] пакета, созданного в [занятия 4: Добавление перенаправления потока ошибок](lesson-4-add-error-flow-redirection-with-ssis.md) для использования модели развертывания пакетов и воспользоваться преимуществами конфигураций пакетов. Также можно скопировать пакет из завершенного урока 4, который включен в учебник. В мастере настройки пакета предстоит создать XML-конфигурацию, которая обновляет свойство `Directory` контейнера «цикл по каждому элементу» с помощью переменной уровня пакета, сопоставленной свойству «Каталог». После создания файла конфигурации следует изменить значение переменной вне среды разработки и создать в измененном свойстве ссылку на новую папку с образцами данных. При повторном выполнении пакета, файл конфигурации заполняет значение переменной и переменной в свою очередь, обновляет `Directory` свойство. В итоге пакет последовательно проходит все файлы в новой, а не исходной папке данных, жестко закодированной в пакете.  
  
> [!IMPORTANT]  
>  Для выполнения упражнений этого учебника потребуется образец базы данных **AdventureWorksDW2012** . Дополнительные сведения об установке и развертывании **AdventureWorksDW2012**см. в разделе [Проект образцов продуктов службы Reporting Services на сайте CodePlex](https://go.microsoft.com/fwlink/?LinkID=526910).  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Копирование пакета занятия 4](lesson-5-1-copying-the-lesson-4-package.md)  
  
-   [Шаг 2. Включение и настройка конфигурации пакетов](lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
-   [Шаг 3. Изменение значения конфигурации свойства Directory](lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
-   [Шаг 4. Проверка учебного пакета занятия 5](lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
  
-   [Шаг 1. Копирование пакета занятия 4](lesson-5-1-copying-the-lesson-4-package.md)  
  
  
