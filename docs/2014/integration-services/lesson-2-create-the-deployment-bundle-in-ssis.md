---
title: Занятие 2. Создание пакета развертывания | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ab17289d-c3d4-4a5e-b7f5-4fea8ae21707
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aaa0bbb2ad5c7c70b8da899c885368ab0e8c391f
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440551"
---
# <a name="lesson-2-creating-the-deployment-bundle"></a>Занятие 2. Cоздание пакета развертывания
  На [занятии 1: подготовка к созданию пакета развертывания](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md)был создан проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , названный "Учебник по развертыванию", к нему были добавлены пакеты и вспомогательные файлы, а также выполнена настройка пакетов.  
  
 На этом занятии создается пакет развертывания, представляющий собой папку, в которой содержатся все элементы, необходимые для установки пакетов на другом компьютере. В пакет развертывания необходимо включить манифест развертывания, копии пакетов и копии файлов поддержки из проекта «Учебник по развертыванию». В манифесте развертывания перечисляются пакеты, различные файлы и настройки из пакета развертывания.  
  
 Помимо этого будет проверен список файлов в пакете развертывания и содержимое манифеста.  
  
 **Предполагаемое время выполнения данного занятия:** 30 минут  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Построение программы развертывания](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
-   [Шаг 2. Проверка пакета развертывания](../integration-services/lesson-2-2-verifying-the-deployment-bundle.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
 [Шаг 1. Построение программы развертывания](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
![Значок Integration Services (маленький)](media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
  
