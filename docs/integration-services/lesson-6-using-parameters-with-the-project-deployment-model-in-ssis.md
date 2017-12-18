---
title: "Занятие 6. Использование параметров в модели развертывания проекта в службах SSIS | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 9216f18c-1762-4f2d-8c22-bd0ab7107555
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 7f44e93c4fa879a8717b0af33e6071fcc0d53368
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2017
---
# <a name="lesson-6-using-parameters-with-the-project-deployment-model-in-ssis"></a>Занятие 6. Использование параметров в модели развертывания проекта в службах SSIS
В SQL Server 2012 была добавлена новая модель развертывания, позволяющая развертывать проекты на сервере служб Integration Services. Сервер служб Integration Services позволяет управлять пакетами, запускать пакеты, а также настраивать значения времени выполнения для пакетов.  
  
На этом занятии требуется изменить пакет, созданный на [занятии 5: добавление конфигураций пакетов SSIS в модель развертывания пакетов](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md) , чтобы использовать модель развертывания пакетов. Значение конфигурации будет заменено на параметр, чтобы указать местоположение образцов данных. Также можно скопировать пакет завершенного урока 5, который включен в учебник.  
  
С использованием мастера настройки проекта служб Integration Services будет выполнено преобразование проекта для использования модели развертывания проектов, а также использования параметра, а не значения конфигурации для задания свойства каталога. На этом занятии частично рассматриваются шаги, необходимые для преобразования существующих пакетов служб SSIS в новую модель развертывания проекта.  
  
При повторном выполнении пакета служба Integration Services использует параметр для заполнения значения переменной, а переменная в свою очередь обновит свойство "Каталог". В итоге пакет последовательно проходит все файлы в новой папке данных, определенной значением параметра, а не в папке, заданной в файле конфигурации пакета.  
  
> [!IMPORTANT]  
> Для выполнения упражнений этого учебника потребуется образец базы данных **AdventureWorksDW2012** . Дополнительные сведения об установке и развертывании образца базы данных **AdventureWorksDW2012** см. в разделе [Вопросы установки образцов кода и образцов баз данных SQL Server](http://technet.microsoft.com/library/ms161556%28v=sql.105%29).  
  
## <a name="lesson-tasks"></a>Задачи занятия  
Это занятие содержит следующие задачи.  
  
1.  [Шаг 1. Копирование пакета занятия 5](../integration-services/lesson-6-1-copying-the-lesson-5-package.md)  
  
2.  [Этап 2. Преобразование проекта в модель развертывания проекта](../integration-services/lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
3.  [Шаг 3. Проверка пакета, созданного на занятии 6](../integration-services/lesson-6-3-testing-the-lesson-6-package.md)  
  
4.  [Шаг 4. Развертывание пакета, созданного на занятии 6](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
[Шаг 1. Копирование пакета занятия 5](../integration-services/lesson-6-1-copying-the-lesson-5-package.md)  
  
