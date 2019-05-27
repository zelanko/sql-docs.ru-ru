---
title: Урок 1. Подготовка к созданию пакета развертывания | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: b6fe283c-9856-4ba1-a497-e3912424fd18
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 196647a2c4f6dc872ec1aba7bb91d24c8809113c
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65722682"
---
# <a name="lesson-1-preparing-to-create-the-deployment-bundle"></a>Урок 1. Подготовка к созданию пакета развертывания

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


На этом занятии требуется создать рабочие папки и переменные среды, поддерживающие данный учебник, создать проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , добавить в него несколько пакетов и необходимых файлов поддержки, а также выполнить настройку пакетов.  
  
[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] развертывают пакеты на основе проектов; поэтому на первом этапе создания комплекта развертывания необходимо собрать все пакеты и зависимые от них модули в один проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Часто оказывается полезным включать в развернутые пакеты другие сведения: например, в проект можно добавить файл сведений, содержащий общую справку по данной группе пакетов.  
  
После добавления пакетов и файлов необходимо добавить настройки в те пакеты, которые еще не были настроены. Благодаря настройкам свойства и объекты пакетов получают обновления во время выполнения. На одном из следующих занятий предстоит изменить значения этих настроек во время развертывания пакета в целях поддержки пакетов в целевой среде развертывания.  
  
После добавления настроек пакеты следует открыть в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] — графическом приложении служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] для создания пакетов ETL — и изучить свойства, элементы и настройки пакетов, чтобы лучше понять проблемы, с которыми сталкивается процесс развертывания. Если, например, один из пакетов извлекает данные из текстовых файлов, то для успешного выполнения развернутых пакетов необходимо обновить информацию о расположении файлов данных.  
  
**Предполагаемое время выполнения данного урока:** 1 час  
  
## <a name="lesson-tasks"></a>Задачи занятия  
Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Создание рабочих папок и переменных среды.](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
-   [Шаг 2. Создание проекта развертывания](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
-   [Шаг 3. Добавление пакетов и других файлов.](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
-   [Шаг 4. Добавление конфигурации пакета.](../integration-services/lesson-1-4-adding-package-configurations.md)  
  
-   [Шаг 5. Тестирование обновленных пакетов](../integration-services/lesson-1-5-testing-the-updated-packages.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
[Шаг 1. Создание рабочих папок и переменных среды.](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
  
  
