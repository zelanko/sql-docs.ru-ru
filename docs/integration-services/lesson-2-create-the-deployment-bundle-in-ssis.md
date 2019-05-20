---
title: Урок 2. Создание пакета развертывания в службах SSIS | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: ab17289d-c3d4-4a5e-b7f5-4fea8ae21707
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: cab62307fa880ff6ac4f1a948c3abfa138ca1377
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65722369"
---
# <a name="lesson-2-create-the-deployment-bundle-in-ssis"></a>Урок 2. Создание пакета развертывания в службах SSIS

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
  
  
  
