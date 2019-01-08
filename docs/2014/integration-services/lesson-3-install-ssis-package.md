---
title: Урок 3. Установка пакетов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 87bc4d82-39d8-424f-886f-98cf1e4bb07a
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e9b1bc021ba009ffe00805c0479a6fa9d91416d2
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53361796"
---
# <a name="lesson-3-installing-packages"></a>Урок 3. Установка пакетов
  В [Урок 2: Cоздание пакета развертывания](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)вы создали программу развертывания и создания пакета развертывания, содержащий элементы, необходимо установить пакеты на другом компьютере. Вы также проверили список файлов в пакете развертывания и изучили содержимое файла манифеста, который был создан при сборке программы развертывания.  
  
 На этом занятии вы скопируете пакет развертывания на другой компьютер и запустите мастер установки пакета, чтобы установить пакеты, зависимости пакетов и вспомогательные файлы. Пакеты будут установлены в базу данных **msdb**[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , а остальные элементы будут установлены в файловую систему. После установки пакета вы проверите развертывание, выполнив пакеты из среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] при помощи программы выполнения пакетов.  
  
 **Предполагаемое время для выполнения этого занятия:** 30 минут  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Копирование пакета развертывания](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
-   [Шаг 2. Запуск мастера установки пакета](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
-   [Шаг 3. Тестирование развернутых пакетов](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
 [Шаг 1. Копирование пакета развертывания](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
![Значок служб Integration Services (маленький)](media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
  
