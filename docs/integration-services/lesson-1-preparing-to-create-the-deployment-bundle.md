---
title: "Занятие 1. Подготовка к созданию пакета развертывания | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: b6fe283c-9856-4ba1-a497-e3912424fd18
caps.latest.revision: "21"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2134bb32596c241c0ff79c732a3f08f7da1e41ba
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="lesson-1-preparing-to-create-the-deployment-bundle"></a>Урок 1. Подготовка к созданию пакета развертывания
На этом занятии требуется создать рабочие папки и переменные среды, поддерживающие данный учебник, создать проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , добавить в него несколько пакетов и необходимых файлов поддержки, а также выполнить настройку пакетов.  
  
[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] развертывают пакеты на основе проектов; поэтому на первом этапе создания комплекта развертывания необходимо собрать все пакеты и зависимые от них модули в один проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Часто оказывается полезным включать в развернутые пакеты другие сведения: например, в проект можно добавить файл сведений, содержащий общую справку по данной группе пакетов.  
  
После добавления пакетов и файлов необходимо добавить настройки в те пакеты, которые еще не были настроены. Благодаря настройкам свойства и объекты пакетов получают обновления во время выполнения. На одном из следующих занятий предстоит изменить значения этих настроек во время развертывания пакета в целях поддержки пакетов в целевой среде развертывания.  
  
После добавления настроек пакеты следует открыть в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] — графическом приложении служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] для создания пакетов ETL — и изучить свойства, элементы и настройки пакетов, чтобы лучше понять проблемы, с которыми сталкивается процесс развертывания. Если, например, один из пакетов извлекает данные из текстовых файлов, то для успешного выполнения развернутых пакетов необходимо обновить информацию о расположении файлов данных.  
  
**Предполагаемое время выполнения данного занятия:** 1 час  
  
## <a name="lesson-tasks"></a>Задачи занятия  
Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Создание рабочих папок и переменных среды](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
-   [Шаг 2. Создание проекта развертывания](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
-   [Шаг 3. Добавление пакетов и других файлов](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
-   [Шаг 4. Добавление конфигурации пакета](../integration-services/lesson-1-4-adding-package-configurations.md)  
  
-   [Шаг 5. Тестирование обновленных пакетов](../integration-services/lesson-1-5-testing-the-updated-packages.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
[Шаг 1. Создание рабочих папок и переменных среды](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
  
  
