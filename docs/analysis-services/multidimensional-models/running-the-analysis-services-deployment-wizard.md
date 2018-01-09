---
title: "Запуск анализа служб мастер развертывания | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Analysis Services Deployment Wizard, running
ms.assetid: 3a38d489-4625-4878-bd18-c6f903be33df
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 2d6a1102ed83493e25e3e73a0b77d035c2e299d9
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="running-the-analysis-services-deployment-wizard"></a>Запуск мастера развертывания служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]При использовании [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] мастер развертывания для развертывания [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проект, мастер можно запустить одним из следующих способов:  
  
-   **Интерактивно** при интерактивном запуске [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] мастер развертывания формируется скрипт развертывания на основе входных файлов, как изменениями, интерактивно вводимыми пользователем. Мастер применяет все пользовательские изменения только к скрипту развертывания. Мастер не изменяет входные файлы. Дополнительные сведения о настройках конфигурации см. в разделе [Understanding the Input Files Used to Create the Deployment Script](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)(Основные сведения о входных файлах, применяемых для создания скрипта развертывания).  
  
-   **В командной строке** при запуске в командной строке [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] развертывания мастер создает скрипт развертывания на основе коммутаторы, которые можно использовать для запуска мастера. Мастер может работать одним из следующих способов: выдать приглашение для ввода данных и изменить входные файлы на основе этих данных, запустить автоматическое развертывание с использованием исходных входных файлов или создать скрипт развертывания, который можно использовать позже.  
  
## <a name="running-the-analysis-services-deployment-wizard-interactively"></a>Запуск мастера развертывания служб Analysis Services в интерактивном режиме  
 При интерактивном запуске мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] считывает значения их входных файлов и выводит эти данные. При этом можно изменить входные значения, например назначение развертывания, настройки конфигурации, параметры развертывания и пароли строк соединения, или оставить их оригинальные значения. При изменении любого входных значений мастер использует их при формировании скрипта развертывания. Однако мастер не изменяет какие-либо значения во входном файле.  
  
> [!NOTE]  
>  При необходимости изменения мастером развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] входных значений запустите его из командной строки и настройте его на работу в режиме файла ответов.  
  
 После просмотра входных значений и внесения необходимых изменений мастер формирует скрипт развертывания. который можно сразу запустить на целевом сервере или сохранить для использования в дальнейшем.  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-interactively"></a>Запуск мастера развертывания служб Analysis Services в интерактивном режиме  
  
-   В меню **Пуск**последовательно выберите **Все программы**, **Microsoft SQL Server**, **Службы Analysis Services**и щелкните пункт **Мастер развертывания**.  
  
     —или—  
  
-   В **проекты** папки [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] проекта, дважды щелкните \<имя проекта > файл с расширением asdatabase.
    > [!NOTE]  
    >  При невозможности нахождения файла .asdatabase попробуйте использовать функцию «Поиск», задав строку «*.asdatabase». Или может потребоваться для построения проекта в SSDT.  
  
## <a name="running-the-analysis-services-deployment-wizard-at-the-command-prompt"></a>Запуск мастера развертывания служб Analysis Services из командной строки  
 Мастер развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] можно также запускать из командной строки. При этом вводится полный путь к файлу .asdatabase и используется один из следующих режимов.  
  
 **Режим файла ответов**  
 В режиме файла ответов мастер позволяет интерактивно изменять входные файлы, созданные при сборке проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Перед тем, как сформировать скрипт развертывания, мастер сохраняет измененные входные файлы. Измененные входные файлы становятся новой отправной точкой при следующем запуске мастера.  
  
 Чтобы запустить мастер в режиме файла ответов, используйте **/a** переключения.  
  
 **Режим без вывода сообщений**  
 В режиме молчания мастер запускает автоматическое развертывание на основе данных, находящихся во входных файлах.  
  
 Чтобы запустить мастер в автоматическом режиме, используйте **/s** переключения. В этом режиме сообщения выводятся на консоль или в файл журнала, если таковой имеется.  
  
 **Режим вывода**  
 В режиме вывода мастер формирует скрипт развертывания для выполнения в будущем на основе входных файлов.  
  
 Чтобы запустить мастер в режиме вывода, используйте **/o** и имя выходного файла.  
  
 Дополнительные сведения об этих параметрах командной строки см. в разделе [Развертывание решений моделей с использованием программы развертывания](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md).  
  
 В следующей процедуре описан запуск мастера развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] из командной строки.  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-at-the-command-prompt"></a>Запуск мастера развертывания служб Analysis Services из командной строки  
  
1.  Откройте командную строку и перейдите в папку C:\Program Files (x86)\Microsoft SQL Server\120\Tools\Binn\ManagementStudio.  
  
2.  Запустите **Microsoft.AnalysisServices.Deployment.exe** с ключом, определяющим режим запуска мастера.  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о скрипте развертывания служб Analysis Services](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)   
 [Развертывание решений модели с использованием мастера развертывания](../../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)  
  
  
