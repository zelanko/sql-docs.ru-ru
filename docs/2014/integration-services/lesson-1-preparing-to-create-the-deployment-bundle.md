---
title: Урок 1. Подготовка к созданию пакета развертывания | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b6fe283c-9856-4ba1-a497-e3912424fd18
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9e4695575aba2e43435c4e26d5a47ccb2cfa39d6
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58387782"
---
# <a name="lesson-1-preparing-to-create-the-deployment-bundle"></a>Урок 1. Подготовка к созданию пакета развертывания
  На этом занятии требуется создать рабочие папки и переменные среды, поддерживающие данный учебник, создать проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , добавить в него несколько пакетов и необходимых файлов поддержки, а также выполнить настройку пакетов.  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] развертывают пакеты на основе проектов; поэтому на первом этапе создания комплекта развертывания необходимо собрать все пакеты и зависимые от них модули в один проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Часто оказывается полезным включать в развернутые пакеты другие сведения: например, в проект можно добавить файл сведений, содержащий общую справку по данной группе пакетов.  
  
 После добавления пакетов и файлов необходимо добавить настройки в те пакеты, которые еще не были настроены. Благодаря настройкам свойства и объекты пакетов получают обновления во время выполнения. На одном из следующих занятий предстоит изменить значения этих настроек во время развертывания пакета в целях поддержки пакетов в целевой среде развертывания.  
  
 После добавления настроек пакеты следует открыть в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] — графическом приложении служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] для создания пакетов ETL — и изучить свойства, элементы и настройки пакетов, чтобы лучше понять проблемы, с которыми сталкивается процесс развертывания. Если, например, один из пакетов извлекает данные из текстовых файлов, то для успешного выполнения развернутых пакетов необходимо обновить информацию о расположении файлов данных.  
  
 **Предполагаемое время для выполнения этого занятия:** 1 час  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Создание рабочих папок и переменных среды](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
-   [Шаг 2. Создание проекта развертывания](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
-   [Шаг 3. Добавление пакетов и других файлов](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
-   [Шаг 4. Добавление конфигурации пакета](../integration-services/lesson-1-4-adding-package-configurations.md)  
  
-   [Шаг 5. Тестирование обновленных пакетов](../integration-services/lesson-1-5-testing-the-updated-packages.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
 [Шаг 1. Создание рабочих папок и переменных среды](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
![Значок служб Integration Services (маленький)](media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
  
