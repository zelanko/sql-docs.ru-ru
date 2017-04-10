---
title: "Занятие&#160;2. Создание пакета развертывания в службах SSIS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: ab17289d-c3d4-4a5e-b7f5-4fea8ae21707
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# Занятие&#160;2. Создание пакета развертывания в службах SSIS
На [занятии 1: подготовка к созданию пакета развертывания](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md) был создан проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], названный "Учебник по развертыванию", к нему были добавлены пакеты и вспомогательные файлы, а также выполнена настройка пакетов.  
  
На этом занятии создается пакет развертывания, представляющий собой папку, в которой содержатся все элементы, необходимые для установки пакетов на другом компьютере. В пакет развертывания необходимо включить манифест развертывания, копии пакетов и копии файлов поддержки из проекта «Учебник по развертыванию». В манифесте развертывания перечисляются пакеты, различные файлы и настройки из пакета развертывания.  
  
Помимо этого будет проверен список файлов в пакете развертывания и содержимое манифеста.  
  
**Предполагаемое время выполнения данного занятия:** 30 минут  
  
## Задачи занятия  
Это занятие содержит следующие задачи.  
  
-   [Шаг 1. Построение программы развертывания](../integration-services/step-1-building-the-deployment-utility.md)  
  
-   [Этап 2. Проверка пакета развертывания](../integration-services/step-2-verifying-the-deployment-bundle.md)  
  
## Начало занятия  
[Шаг 1. Построение программы развертывания](../integration-services/step-1-building-the-deployment-utility.md)  
  
  
  
