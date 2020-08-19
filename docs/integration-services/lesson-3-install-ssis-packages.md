---
description: Занятие 3. Установка пакетов SSIS
title: Занятие 3. Установка пакетов SSIS | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 87bc4d82-39d8-424f-886f-98cf1e4bb07a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a56687640190b5f129071c6ad2836b3013ae2ac0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449724"
---
# <a name="lesson-3-install-ssis-packages"></a>Занятие 3. Установка пакетов SSIS

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]


На [занятии 2: создание пакета развертывания в службах SSIS](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)вы создали программу развертывания и пакет развертывания, содержащий элементы, которые говорят о том, что нужно установить пакеты на другой компьютер. Вы также проверили список файлов в пакете развертывания и изучили содержимое файла манифеста, который был создан при сборке программы развертывания.  
  
На этом занятии вы скопируете пакет развертывания на другой компьютер и запустите мастер установки пакета, чтобы установить пакеты, зависимости пакетов и вспомогательные файлы. Пакеты будут установлены в базу данных **msdb**[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , а остальные элементы будут установлены в файловую систему. После установки пакета вы проверите развертывание, выполнив пакеты из среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] при помощи программы выполнения пакетов.  
  
**Предполагаемое время выполнения данного урока:** 30 минут  
  
## <a name="lesson-tasks"></a>Задачи занятия  
Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Копирование пакета развертывания](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
-   [Шаг 2. Запуск мастера установки пакета](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
-   [Шаг 3. Тестирование развернутых пакетов](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
[Шаг 1. Копирование пакета развертывания](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
  
  
