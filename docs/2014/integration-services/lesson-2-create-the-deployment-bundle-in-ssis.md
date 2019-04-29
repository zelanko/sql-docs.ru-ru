---
title: Урок 2. Cоздание пакета развертывания | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ab17289d-c3d4-4a5e-b7f5-4fea8ae21707
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8ec7519a4ea203693e6520eee569639a3259215f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62767516"
---
# <a name="lesson-2-creating-the-deployment-bundle"></a>Урок 2. Cоздание пакета развертывания
  В разделе [Занятие 1. Подготовка к созданию пакета развертывания](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md) вы создали проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] с именем "Учебник по развертыванию", добавили к нему пакеты и вспомогательные файлы, а также настроили пакеты.  
  
 На этом занятии создается пакет развертывания, представляющий собой папку, в которой содержатся все элементы, необходимые для установки пакетов на другом компьютере. В пакет развертывания необходимо включить манифест развертывания, копии пакетов и копии файлов поддержки из проекта «Учебник по развертыванию». В манифесте развертывания перечисляются пакеты, различные файлы и настройки из пакета развертывания.  
  
 Помимо этого будет проверен список файлов в пакете развертывания и содержимое манифеста.  
  
 **Предполагаемое время выполнения данного урока:** 30 минут  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Сборка программы развертывания.](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
-   [Шаг 2. Проверка пакета развертывания.](../integration-services/lesson-2-2-verifying-the-deployment-bundle.md)  
  
## <a name="start-the-lesson"></a>Начало занятия  
 [Шаг 1. Сборка программы развертывания.](../integration-services/lesson-2-1-building-the-deployment-utility.md)  
  
![Значок служб Integration Services (маленький)](media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
  
