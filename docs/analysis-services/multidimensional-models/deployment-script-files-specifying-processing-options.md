---
title: "Указание параметров обработки | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Analysis Services deployments, processing options
- input files [Analysis Services]
- deploying [Analysis Services], processing options
- modifying processing options
- Analysis Services Deployment Wizard, processing options
ms.assetid: e9e50817-908e-4210-bc3d-8e2957568241
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 37535b41f5ae5e7c68a47d18a4b91253c7f54d81
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="deployment-script-files---specifying-processing-options"></a>Файлы скриптов развертывания — Указание параметров обработки
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Мастер развертывания служб считывает параметры обработки из \< *имя проекта*> .deploymentoptions файла. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]создает этот файл при построении [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] использует параметры обработки, указанные на **развертывания** страница  *\<имя проекта >* **страницы свойств** диалоговое окно «», чтобы создать \< *имя проекта*> .deploymentoptions файла.  
  
## <a name="reviewing-the-processing-options-for-deployment"></a>Просмотр параметров обработки для развертывания  
 Параметры конфигурации, хранящиеся в \< *имя проекта*> .deploymentoptions файла, следующим образом:  
  
-   **Метод обработки** Эта настройка контролирует, обрабатываются ли развернутые объекты после развертывания, а также тип обработки, который будет выполнен. Существуют три параметра обработки.  
  
    -   Обработка по умолчанию (по умолчанию).  
  
    -   Полная обработка.  
  
    -   Нет  
  
-   **Параметры таблицы обратной записи.** Если включена обратная запись для проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , то эта настройка определяет обработку обратной записи. Существуют три параметра таблицы обратной записи.  
  
    -   По умолчанию: если таблица обратной записи существует, то она будет использоваться. Если таблицы обратной записи не существует, то будет создана новая таблица обратной записи.  
  
    -   Если таблица обратной записи уже существует, то развертывание окончится сбоем. Если таблицы обратной записи не существует, то будет создана новая таблица обратной записи.  
  
    -   Вне зависимости от того, существует ли уже таблица обратной записи, будет создана новая таблица обратной записи. В этом случае мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] удалит существующую таблицу и заменит ее новой таблицей обратной записи.  
  
-   **Транзакционное развертывание** Эта настройка контролирует, обрабатываются ли изменения развертывания метаданных и команды обработки в одной транзакции или в отдельных транзакциях.  
  
    -   Если значение этого параметра установлено равным **True** (по умолчанию), то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывают все изменения метаданных и все команды обработки в одной транзакции.  
  
    -   Если значение этого параметра установлено равным **False**, то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывают изменения метаданных в одной транзакции и развертывают каждую команду обработки в ее собственной транзакции.  
  
## <a name="modifying-the-processing-options-for-deployment"></a>Изменение параметров обработки для развертывания  
 Тем не менее, может потребоваться развернуть [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта, используя параметры обработки, отличающиеся от хранящихся в \< *имя проекта*> .deploymentoptions файла. Например может быть необходимо полностью обработать все объекты или обработать их с использованием параметра обработки по умолчанию, или не обрабатывать вообще. Если разрешена запись в кубы или измерения, то можно указать, будет ли использоваться новая или существующая таблица обратной записи.  
  
 Чтобы изменить параметры обработки во время развертывания, можно либо исправить и повторно собрать проект, либо изменить параметры обработки во входном файле, используя один из методов, описанных в следующей процедуре.  
  
#### <a name="to-change-processing-options-after-the-input-files-have-been-generated"></a>Изменение параметров обработки после формирования входных файлов  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в интерактивном режиме. На странице **Параметры обработки** укажите параметры обработки для развертываемого проекта.  
  
     —или—  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из командной строки и настройте его на работу в режиме файла ответов. Дополнительные сведения о режиме файла ответов см. в разделе [Запуск мастера развертывания служб Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).  
  
     —или—  
  
-   Изменить \< *имя проекта*> .deploymentoptions файл, используя любой текстовый редактор.  
  
## <a name="see-also"></a>См. также  
 [Указание целевого объекта установки](../../analysis-services/multidimensional-models/deployment-script-files-specifying-the-installation-target.md)   
 [Указание параметров развертывания ролей и секций](../../analysis-services/multidimensional-models/deployment-script-files-partition-and-role-deployment-options.md)   
 [Задание параметров конфигурации для развертывания решения](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
  
