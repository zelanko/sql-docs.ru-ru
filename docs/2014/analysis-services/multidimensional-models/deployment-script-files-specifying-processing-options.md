---
title: Указание параметров обработки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services deployments, processing options
- input files [Analysis Services]
- deploying [Analysis Services], processing options
- modifying processing options
- Analysis Services Deployment Wizard, processing options
ms.assetid: e9e50817-908e-4210-bc3d-8e2957568241
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c5f20e9061aae762eda6b773c7bdb345273fd1b5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37149105"
---
# <a name="specifying-processing-options"></a>Указание параметров обработки
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Мастер развертывания служб считывает параметры обработки из \< *имя_проекта*> .deploymentoptions файл. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] создает этот файл при построении проекта служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] использует параметры обработки, указанные на **развертывания** странице  *\<имя проекта >* **страницы свойств** диалоговое окно, чтобы создать \< *имя_проекта*> .deploymentoptions файл.  
  
## <a name="reviewing-the-processing-options-for-deployment"></a>Просмотр параметров обработки для развертывания  
 Настройки конфигурации, хранящиеся в \< *имя_проекта*> .deploymentoptions файла, следующим образом:  
  
-   **Метод обработки** Эта настройка контролирует, обрабатываются ли развернутые объекты после развертывания, а также тип обработки, который будет выполнен. Существуют три параметра обработки.  
  
    -   Обработка по умолчанию (по умолчанию).  
  
    -   Полная обработка.  
  
    -   None  
  
-   **Параметры таблицы обратной записи.** Если включена обратная запись для проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , то эта настройка определяет обработку обратной записи. Существуют три параметра таблицы обратной записи.  
  
    -   По умолчанию: если таблица обратной записи существует, то она будет использоваться. Если таблицы обратной записи не существует, то будет создана новая таблица обратной записи.  
  
    -   Если таблица обратной записи уже существует, то развертывание окончится сбоем. Если таблицы обратной записи не существует, то будет создана новая таблица обратной записи.  
  
    -   Вне зависимости от того, существует ли уже таблица обратной записи, будет создана новая таблица обратной записи. В этом случае мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] удалит существующую таблицу и заменит ее новой таблицей обратной записи.  
  
-   **Транзакционное развертывание** Эта настройка контролирует, обрабатываются ли изменения развертывания метаданных и команды обработки в одной транзакции или в отдельных транзакциях.  
  
    -   Если этот параметр имеет `True` (по умолчанию), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывают все изменения метаданных и все команды обработки в одной транзакции.  
  
    -   Если этот параметр имеет `False`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывают изменения метаданных в одной транзакции и развертывают каждую команду обработки в ее собственной транзакции.  
  
## <a name="modifying-the-processing-options-for-deployment"></a>Изменение параметров обработки для развертывания  
 Тем не менее, необходимо развернуть [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проект, используя параметры обработки, отличающиеся от тех, которые хранятся в \< *имя_проекта*> .deploymentoptions файл. Например может быть необходимо полностью обработать все объекты или обработать их с использованием параметра обработки по умолчанию, или не обрабатывать вообще. Если разрешена запись в кубы или измерения, то можно указать, будет ли использоваться новая или существующая таблица обратной записи.  
  
 Чтобы изменить параметры обработки во время развертывания, можно либо исправить и повторно собрать проект, либо изменить параметры обработки во входном файле, используя один из методов, описанных в следующей процедуре.  
  
#### <a name="to-change-processing-options-after-the-input-files-have-been-generated"></a>Изменение параметров обработки после формирования входных файлов  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в интерактивном режиме. На странице **Параметры обработки** укажите параметры обработки для развертываемого проекта.  
  
     —или—  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из командной строки и настройте его на работу в режиме файла ответов. Дополнительные сведения о режиме файла ответов см. в разделе [Запуск мастера развертывания служб Analysis Services](running-the-analysis-services-deployment-wizard.md).  
  
     —или—  
  
-   Изменить \< *имя_проекта*> .deploymentoptions файл, используя любой текстовый редактор.  
  
## <a name="see-also"></a>См. также  
 [Указание целевого объекта установки](deployment-script-files-specifying-the-installation-target.md)   
 [Указание секций и параметров развертывания ролей](deployment-script-files-partition-and-role-deployment-options.md)   
 [Указание настроек конфигурации для развертывания решения](deployment-script-files-solution-deployment-config-settings.md)  
  
  
