---
title: Указание целевого объекта установки | Документы Microsoft
ms.custom: ''
ms.date: 03/27/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining - "setup-install"
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- input files [Analysis Services]
- installation targets [Analysis Services]
- Analysis Services deployments, installation targets
- Analysis Services Deployment Wizard, installation targets
- deploying [Analysis Services], installation targets
- modifying installation targets
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
caps.latest.revision: ''
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c9977badf4e1e8e05cb35ed8828d4cc4ae12cfae
ms.sourcegitcommit: d6881107b51e1afe09c2d8b88b98d075589377de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="deployment-script-files---specifying-the-installation-target"></a>Файлы скриптов развертывания — Указание целевого объекта установки
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Мастер развертывания служб считывает сведения о целевом установки из \< *имя проекта*> .deploymenttargets файла. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]создает этот файл при построении [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] использует базу данных и сервер, указанные на **развертывания** страница  *\<имя проекта >* **страницы свойств** диалоговое окно «» для создания \< *имя проекта*> TARGETS-файл.  
  
## <a name="modifying-the-installation-target-for-deployment"></a>Измерение целевого объекта установки для развертывания  
 В некоторых ситуациях может быть необходимо развернуть проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в базу данных или экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , отличающийся от указанного на странице **Развертывание** . Например может быть необходимо развернуть проект на сервер для тестирования перед развертыванием, а затем развернуть его на производственный сервер после окончания тестирования. Может также быть необходимо развернуть завершенный и протестированный проект на несколько производственных серверов в кластере балансирования сетевой нагрузки, или на промежуточный сервер и производственный сервер.  
  
 Чтобы развернуть проект служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в другую базу данных или экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , можно изменить целевой объект установки во входном файле, используя один из методов, описанный в следующей процедуре.  
  
#### <a name="to-change-the-installation-target-after-the-input-files-have-been-generated"></a>Изменение целевого объекта установки после формирования входных файлов  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в интерактивном режиме. На странице **Целевой объект установки** укажите новое место назначения для экземпляра и базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
     —или—  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из командной строки и настройте его на работу в режиме файла ответов. Дополнительные сведения о режиме файла ответов см. в разделе [Запуск мастера развертывания служб Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).  
  
     —или—  
  
-   Изменить \< *имя проекта*> .deploymenttargets файл, используя любой текстовый редактор.  
  
## <a name="see-also"></a>См. также  
 [Указание параметров развертывания ролей и секций](../../analysis-services/multidimensional-models/deployment-script-files-partition-and-role-deployment-options.md)   
 [Задание параметров конфигурации для развертывания решения](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)   
 [Указание параметров обработки](../../analysis-services/multidimensional-models/deployment-script-files-specifying-processing-options.md)  
  
  
