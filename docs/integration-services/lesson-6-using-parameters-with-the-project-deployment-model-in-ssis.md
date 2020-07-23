---
title: 'Занятие 6: Использование параметров в модели развертывания проекта | Документация Майкрософт'
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 9216f18c-1762-4f2d-8c22-bd0ab7107555
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2e5bcf043f779660692b11cc6238b74d1b83d6af
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86922350"
---
# <a name="lesson-6-use-parameters-with-the-project-deployment-model-in-ssis"></a>Занятие 6: Использование параметров в модели развертывания проекта в службах SQL Server Integration Services

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



В SQL Server 2012 была добавлена новая модель развертывания, позволяющая развертывать проекты на сервере служб Integration Services. Сервер служб Integration Services позволяет управлять пакетами, запускать пакеты, а также настраивать значения времени выполнения для пакетов.  
  
На этом занятии пакет, созданный на [занятии 5: добавление конфигураций пакетов SSIS в модель развертывания пакетов](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md), будет изменен для использования модели развертывания пакета. Значение конфигурации будет заменено на параметр, чтобы указать местоположение образцов данных. Также можно скопировать пакет завершенного урока 5, который включен в учебник.  
  
С помощью мастера настройки проекта служб Integration Services проект преобразуется в модель развертывания проекта. Эта модель использует параметр, а не значение конфигурации для задания свойства "Каталог". На этом занятии частично рассматриваются шаги, необходимые для преобразования существующих пакетов служб SSIS в новую модель развертывания проекта.  
  
При повторном выполнении пакета сервер [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] использует параметр для заполнения значения переменной. Переменная в свою очередь обновляет свойство "Каталог". Пакет перебирает все файлы в папке данных, определенной новым параметром.  
  
> [!NOTE]
> Ознакомьтесь с [предварительными требованиями для урока 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites), если вы еще не сделали этого.
    
## <a name="lesson-tasks"></a>Задачи занятия  
Это занятие содержит следующие задачи.  
  
1.  [Шаг 1. Копирование пакета занятия 5](../integration-services/lesson-6-1-copying-the-lesson-5-package.md)  
  
2.  [Шаг 2. Преобразование проекта в модель развертывания проекта](../integration-services/lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
3.  [Шаг 3. Тестирование пакета занятия 6](../integration-services/lesson-6-3-testing-the-lesson-6-package.md)  
  
4.  [Шаг 4. Развертывание пакета занятия 6](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
[Шаг 1. Копирование пакета занятия 5](../integration-services/lesson-6-1-copying-the-lesson-5-package.md)  
  
