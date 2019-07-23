---
title: Урок 3. Установка пакетов SSIS | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 87bc4d82-39d8-424f-886f-98cf1e4bb07a
author: janinezhang
ms.author: janinez
ms.openlocfilehash: b6d5e59c07874ead6eeba97cc2aeaaa240464c21
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68055926"
---
# <a name="lesson-3-install-ssis-packages"></a>Урок 3. Установка пакетов SSIS

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


В [уроке 2 о создании пакета развертывания в службах SSIS](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md) вы создали программу развертывания и пакет развертывания, содержащий элементы, которые необходимо установить на другом компьютере. Вы также проверили список файлов в пакете развертывания и изучили содержимое файла манифеста, который был создан при сборке программы развертывания.  
  
На этом занятии вы скопируете пакет развертывания на другой компьютер и запустите мастер установки пакета, чтобы установить пакеты, зависимости пакетов и вспомогательные файлы. Пакеты будут установлены в базу данных **msdb**[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , а остальные элементы будут установлены в файловую систему. После установки пакета вы проверите развертывание, выполнив пакеты из среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] при помощи программы выполнения пакетов.  
  
**Предполагаемое время выполнения данного урока:** 30 минут  
  
## <a name="lesson-tasks"></a>Задачи занятия  
Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Копирование пакета развертывания.](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
-   [Шаг 2. Запуск мастера установки пакета.](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
-   [Шаг 3. Тестирование развернутых пакетов.](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
[Шаг 1. Копирование пакета развертывания.](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
  
  
