---
title: Задание параметров обработки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services deployments, processing options
- input files [Analysis Services]
- deploying [Analysis Services], processing options
- modifying processing options
- Analysis Services Deployment Wizard, processing options
ms.assetid: e9e50817-908e-4210-bc3d-8e2957568241
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ea766d26034b9ee0d1fcefbd215f41c19da1f9ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075226"
---
# <a name="specifying-processing-options"></a>Указание параметров обработки
  Мастер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывания считывает параметры обработки из файла с \< *именем проекта*>. deploymentoptions. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]создает этот файл при сборке [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]использует параметры обработки, указанные на странице **развертывание** диалогового окна свойства * \<имя проекта>* диалоговом окне **страницы свойств** , чтобы создать \< *имя проекта*> файл. deploymentoptions.  
  
## <a name="reviewing-the-processing-options-for-deployment"></a>Просмотр параметров обработки для развертывания  
 Параметры конфигурации, хранящиеся в \<файле с *именем проекта*>. deploymentoptions, выглядят следующим образом:  
  
-   **Метод обработки** Этот параметр определяет, обрабатываются ли развернутые объекты после развертывания, и тип обработки, которая будет выполнена. Существуют три параметра обработки.  
  
    -   Обработка по умолчанию (по умолчанию).  
  
    -   Полная обработка.  
  
    -   None  
  
-   **Параметры таблицы обратной записи** Если в [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекте включена обратная запись, этот параметр определяет, как обрабатывается обратная запись. Существуют три параметра таблицы обратной записи.  
  
    -   По умолчанию: если таблица обратной записи существует, то она будет использоваться. Если таблицы обратной записи не существует, то будет создана новая таблица обратной записи.  
  
    -   Если таблица обратной записи уже существует, то развертывание окончится сбоем. Если таблицы обратной записи не существует, то будет создана новая таблица обратной записи.  
  
    -   Вне зависимости от того, существует ли уже таблица обратной записи, будет создана новая таблица обратной записи. В этом случае мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] удалит существующую таблицу и заменит ее новой таблицей обратной записи.  
  
-   **Транзакционное развертывание** Этот параметр определяет, выполняется ли развертывание изменений метаданных и команд обработки в одной транзакции или в отдельных транзакциях.  
  
    -   Если значение этого параметра установлено равным `True` (по умолчанию), то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывают все изменения метаданных и все команды обработки в одной транзакции.  
  
    -   Если значение этого параметра установлено равным `False`, то службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывают изменения метаданных в одной транзакции и развертывают каждую команду обработки в ее собственной транзакции.  
  
## <a name="modifying-the-processing-options-for-deployment"></a>Изменение параметров обработки для развертывания  
 Однако может потребоваться развернуть проект, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используя параметры обработки, отличные от параметров, \<хранящихся в файле *Project Name*>. deploymentoptions. Например может быть необходимо полностью обработать все объекты или обработать их с использованием параметра обработки по умолчанию, или не обрабатывать вообще. Если разрешена запись в кубы или измерения, то можно указать, будет ли использоваться новая или существующая таблица обратной записи.  
  
 Чтобы изменить параметры обработки во время развертывания, можно либо исправить и повторно собрать проект, либо изменить параметры обработки во входном файле, используя один из методов, описанных в следующей процедуре.  
  
#### <a name="to-change-processing-options-after-the-input-files-have-been-generated"></a>Изменение параметров обработки после формирования входных файлов  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в интерактивном режиме. На странице **Параметры обработки** укажите параметры обработки для развертываемого проекта.  
  
     -или-  
  
-   Запустите мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из командной строки и настройте его на работу в режиме файла ответов. Дополнительные сведения о режиме файла ответов см. в разделе [Запуск мастера развертывания служб Analysis Services](running-the-analysis-services-deployment-wizard.md).  
  
     -или-  
  
-   \<Измените *имя проекта*>. deploymentoptions с помощью любого текстового редактора.  
  
## <a name="see-also"></a>См. также:  
 [Указание целевого объекта установки](deployment-script-files-specifying-the-installation-target.md)   
 [Указание параметров развертывания секций и ролей](deployment-script-files-partition-and-role-deployment-options.md)   
 [Указание настроек конфигурации для развертывания решения](deployment-script-files-solution-deployment-config-settings.md)  
  
  
