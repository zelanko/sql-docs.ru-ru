---
title: Указание целевого объекта установки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- installation targets [Analysis Services]
- Analysis Services deployments, installation targets
- Analysis Services Deployment Wizard, installation targets
- deploying [Analysis Services], installation targets
- modifying installation targets
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
author: minewiskan
ms.author: owend
ms.openlocfilehash: e830fc353898e3ec835b338e84765a0cad0de43f
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546832"
---
# <a name="specifying-the-installation-target"></a>Указание целевого объекта установки
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]Мастер развертывания считывает сведения о целевом объекте установки из \<*project name*> файла deploymenttargets. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]создает этот файл при сборке [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]использует базу данных и сервер, указанные на странице **развертывание** *\<project name>* диалогового окна **страницы свойств** , для создания \<*project name*> файла TARGETS.  
  
## <a name="modifying-the-installation-target-for-deployment"></a>Измерение целевого объекта установки для развертывания  
 В некоторых ситуациях может быть необходимо развернуть проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в базу данных или экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , отличающийся от указанного на странице **Развертывание** . Например может быть необходимо развернуть проект на сервер для тестирования перед развертыванием, а затем развернуть его на производственный сервер после окончания тестирования. Может также быть необходимо развернуть завершенный и протестированный проект на несколько производственных серверов в кластере балансирования сетевой нагрузки, или на промежуточный сервер и производственный сервер.  
  
 Чтобы развернуть проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в другую базу данных или экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , можно изменить целевой объект установки во входном файле, используя один из методов, описанный в следующей процедуре.  
  
#### <a name="to-change-the-installation-target-after-the-input-files-have-been-generated"></a>Изменение целевого объекта установки после формирования входных файлов  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в интерактивном режиме. На странице **Целевой объект установки** укажите новое место назначения для экземпляра и базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
     -или-  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из командной строки и настройте его на работу в режиме файла ответов. Дополнительные сведения о режиме файла ответов см. в разделе [Запуск мастера развертывания служб Analysis Services](running-the-analysis-services-deployment-wizard.md).  
  
     -или-  
  
-   Измените \<*project name*> файл deploymenttargets с помощью любого текстового редактора.  
  
## <a name="see-also"></a>См. также:  
 [Указание параметров развертывания секций и ролей](deployment-script-files-partition-and-role-deployment-options.md)   
 [Указание параметров конфигурации для развертывания решения](deployment-script-files-solution-deployment-config-settings.md)   
 [Указание параметров обработки](deployment-script-files-specifying-processing-options.md)  
  
  
