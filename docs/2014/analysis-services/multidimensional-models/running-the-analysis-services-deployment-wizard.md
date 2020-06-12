---
title: Запуск мастера развертывания Analysis Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard, running
ms.assetid: 3a38d489-4625-4878-bd18-c6f903be33df
author: minewiskan
ms.author: owend
ms.openlocfilehash: 03e142f00192e04d5b17bc2041563cea06199c8b
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545726"
---
# <a name="running-the-analysis-services-deployment-wizard"></a>Запуск мастера развертывания служб Analysis Services
  При использовании [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] мастера развертывания для развертывания [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта можно запустить мастер следующими способами.  
  
-   **Интерактивно.** При интерактивном запуске мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] формирует XML-скрипт развертывания на основе входных файлов в соответствии с изменениями, интерактивно вводимыми пользователем. Мастер применяет все пользовательские изменения только к скрипту развертывания. Мастер не изменяет входные файлы. Дополнительные сведения о настройках конфигурации см. в разделе [Understanding the Input Files Used to Create the Deployment Script](deployment-script-files-input-used-to-create-deployment-script.md)(Основные сведения о входных файлах, применяемых для создания скрипта развертывания).  
  
-   **Из командной строки** При запуске из командной строки [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Мастер развертывания создает XML для аналитики (XMLA) скрипт развертывания на основе параметров, используемых для запуска мастера. Мастер может работать одним из следующих способов: выдать приглашение для ввода данных и изменить входные файлы на основе этих данных, запустить автоматическое развертывание с использованием исходных входных файлов или создать скрипт развертывания, который можно использовать позже.  
  
## <a name="running-the-analysis-services-deployment-wizard-interactively"></a>Запуск мастера развертывания служб Analysis Services в интерактивном режиме  
 При интерактивном запуске мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] считывает значения их входных файлов и выводит эти данные. Вы можете изменить эти входные значения, такие как назначение развертывания, параметры конфигурации, параметры развертывания и пароли строк подключения, либо оставить их как есть. При изменении каких-либо входных значений мастер использует их при формировании XMLA-скрипта развертывания. Однако мастер не изменяет какие-либо значения во входном файле.  
  
> [!NOTE]  
>  При необходимости изменения мастером развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] входных значений запустите его из командной строки и настройте его на работу в режиме файла ответов.  
  
 После просмотра входных значений и внесения необходимых изменений мастер формирует XMLA-скрипт развертывания, который можно сразу запустить на целевом сервере или сохранить для использования в дальнейшем.  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-interactively"></a>Запуск мастера развертывания служб Analysis Services в интерактивном режиме  
  
-   В меню **Пуск**последовательно выберите **Все программы**, **Microsoft SQL Server**, **Службы Analysis Services**и щелкните пункт **Мастер развертывания**.  
  
     -или-  
  
-   В папке **проекты** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта дважды щелкните *\<project name>* файл asdatabase.  
  
    > [!NOTE]  
    >  Если файл asdatabase не найден *\<project name>* , попробуйте использовать поиск и укажите *. asdatabase.  
  
## <a name="running-the-analysis-services-deployment-wizard-at-the-command-prompt"></a>Запуск мастера развертывания служб Analysis Services из командной строки  
 Мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно также запускать из командной строки. При этом вводится полный путь к файлу .asdatabase и используется один из следующих режимов.  
  
 **Режим файла ответов**  
 В режиме файла ответов мастер позволяет интерактивно изменять входные файлы, созданные при сборке проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Перед тем как сформировать XMLA-скрипт развертывания, мастер сохраняет измененные входные файлы. Измененные входные файлы становятся новой отправной точкой при следующем запуске мастера.  
  
 Чтобы запустить мастер в режиме файла ответов, используйте параметр **/a** .  
  
 **Режим без вывода сообщений**  
 В режиме молчания мастер запускает автоматическое развертывание на основе данных, находящихся во входных файлах.  
  
 Чтобы запустить мастер в автоматическом режиме, используйте параметр **/s** . В этом режиме сообщения выводятся на консоль или в файл журнала, если таковой имеется.  
  
 **Режим вывода**  
 В режиме вывода мастер формирует XMLA-скрипт развертывания для выполнения в будущем на основе входных файлов.  
  
 Чтобы запустить мастер в режиме вывода, используйте параметр **/o** и укажите имя выходного файла.  
  
 Дополнительные сведения об этих параметрах командной строки см. в разделе [Развертывание решений моделей с использованием программы развертывания](deploy-model-solutions-with-the-deployment-utility.md).  
  
 В следующей процедуре описан запуск мастера развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из командной строки.  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-at-the-command-prompt"></a>Запуск мастера развертывания служб Analysis Services из командной строки  
  
1.  Откройте командную строку и перейдите в папку C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE.  
  
2.  Запустите **Microsoft.AnalysisServices.Deployment.exe** с ключом, определяющим режим запуска мастера.  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о скрипте развертывания Analysis Services](understanding-the-analysis-services-deployment-script.md)   
 [Развертывание решений модели с использованием мастера развертывания](deploy-model-solutions-using-the-deployment-wizard.md)  
  
  
