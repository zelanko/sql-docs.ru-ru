---
title: "Указание целевого объекта установки | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "входные файлы [службы Analysis Services]"
  - "целевые объекты установки [службы Analysis Services]"
  - "развертывания служб Analysis Services, целевые объекты установки"
  - "мастер развертывания служб Analysis Services, целевые объекты установки"
  - "развертывание [службы Analysis Services], целевые объекты установки"
  - "изменение целевых объектов установки"
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
caps.latest.revision: 35
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Указание целевого объекта установки
  Мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] считывает данные о целевом объекте установки из файла \<*имя проекта*>.deploymenttargets. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] создает этот файл при построении проекта служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] использует базу данных и сервер, указанные на странице **Развертывание** диалогового окна *Страницы свойств* **\<имя проекта>**, для создания файла \<*имя проекта*>.targets.  
  
## Измерение целевого объекта установки для развертывания  
 В некоторых ситуациях может быть необходимо развернуть проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в базу данных или экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , отличающийся от указанного на странице **Развертывание** . Например может быть необходимо развернуть проект на сервер для тестирования перед развертыванием, а затем развернуть его на производственный сервер после окончания тестирования. Может также быть необходимо развернуть завершенный и протестированный проект на несколько производственных серверов в кластере балансирования сетевой нагрузки, или на промежуточный сервер и производственный сервер.  
  
 Чтобы развернуть проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в другую базу данных или экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , можно изменить целевой объект установки во входном файле, используя один из методов, описанный в следующей процедуре.  
  
#### Изменение целевого объекта установки после формирования входных файлов  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в интерактивном режиме. На странице **Целевой объект установки** укажите новое место назначения для экземпляра и базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
     —или—  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из командной строки и настройте его на работу в режиме файла ответов. Дополнительные сведения о режиме файла ответов см. в разделе [Запуск мастера развертывания служб Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).  
  
     —или—  
  
-   Измените файл \<*имя проекта*>.deploymenttargets, используя любой текстовый редактор.  
  
## См. также  
 [Указание параметров развертывания секций и ролей](../../analysis-services/multidimensional-models/specifying-partition-and-role-deployment-options.md)   
 [Указание настроек конфигурации для развертывания решения](../../analysis-services/multidimensional-models/specifying-configuration-settings-for-solution-deployment.md)   
 [Указание параметров обработки](../../analysis-services/multidimensional-models/specifying-processing-options.md)  
  
  