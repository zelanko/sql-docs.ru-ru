---
title: Построение проектов служб Analysis Services (SSDT) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 18c906c7dea3b57b2760a7bb5f44e69834906e6a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34022999"
---
# <a name="build-analysis-services-projects-ssdt"></a>Построение проектов служб Analysis Services (среда SSDT)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Построение проекта служб [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]в среде [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] похоже на создание программного проекта в среде Visual Studio. При создании проекта, в выходном каталоге создается набор XML-файлов. Эти XML-файлы используют язык сценария служб анализа данных (ASSL), который представляет собой XML-диалект клиентских приложений, включающий использование [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] для взаимодействия с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в целях создания или изменения объектов служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Эти XML-файлы используются для развертывания определений объекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в проекте служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] на конкретном экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
## <a name="building-a-project"></a>Построение проекта  
 При построении проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] создаст в выходном каталоге полный набор XML-файлов, который содержит все необходимые команды ASSL, требуемые для построения всех объектов базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в проекте. Если проект был предварительно построен, а для активной конфигурации было задано добавочное развертывание, среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] также создаст XML-файл, содержащий команды языка ASSL для выполнения добавочных обновлений разворачиваемых объектов. Этот XML-файл будет помещен в папку ..\obj\\<активная конфигурация\> проекта. Добавочные построения могут сэкономить время при развертывании и обработке очень больших объемов данных.  
  
> [!NOTE]  
>  Чтобы игнорировать настройку добавочного развертывания, можно использовать команду «Перестроить все».  
  
 При построении проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в проекте выполняется проверка определений объектов. Эта проверка затрагивает любые связанные сборки. Ошибки построения появляются в окне списка задач, вместе с текстом ошибок AMO. Щелкнув ошибку, можно открыть конструктор, требуемый для исправления этой ошибки.  
  
 Успешная проверка не гарантирует того, что в процессе развертывания объекты будут созданы на целевом сервере, или того, что они будут успешно работать после развертывания. Следующие проблемы могут препятствовать успешному развертыванию, или успешной работе после развертывания:  
  
-   Для сервера не выполняются проверки безопасности, поэтому блокировки могут препятствовать развертыванию.  
  
-   На сервере не проверяется физическое размещение.  
  
-   Не проверяются подробности представлений источников данных в отношении к источнику данных на целевом сервере.  
  
 Если проверка прошла успешно, среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] создает XML-файлы. После построения выходная папка будет содержать файлы, описанные в следующей таблице.  
  
|Файлы (в папке «bin»)|Описание|  
|-----------------------------|-----------------|  
|*Projectname*.asdatabase|Содержит элементы языка ASSL, которые определяют метаданные для объектов проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в файле скрипта развертывания. Этот файл используется ядром развертывания, чтобы развернуть объекты в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|*Projectname*.configsettings|Содержит настройки конфигурации, используемые во время развертывания, которые можно изменить непосредственно или в мастере развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (например, строка подключения для источников данных).|  
|*Projectname*.deploymenttargets|Содержит целевые настройки, используемые во время развертывания, которые можно изменить непосредственно или в мастере развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , например имена сервера и базы данных.|  
|*Projectname*.deploymentoptions|Содержит различные настройки параметров, используемые во время развертывания, которые можно изменить непосредственно или в мастере развертывания служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , например место хранения.|  
|*Assemblyname*/*dllname.* dll|Отдельные папки для каждой связанной сборки. Каждая папка содержит библиотеку DLL для сборки, любые связанные сборки и любые связанные PDB-файлы для выходных отладочных данных.|  
  
|Файлы (в папке «obj»)|Описание|  
|-----------------------------|-----------------|  
|\<Имя конфигурации > \LastBuilt.xml|Содержит временную метку и хэш-код, идентифицирующие время последней сборки проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
  
 Эти XML-файлы не содержат \<Create > и \<Alter > тегов, которые создаются во время развертывания.  
  
 Связанные сборки (за исключением стандартной системной сборки и сборки служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ) также копируются в выходной каталог. При наличии связей с другими проектами решения, эти проекты сначала собираются, используя соответствующую конфигурацию проекта и зависимости построения, заданные связями проекта, а затем копируются в выходную папку проекта.  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку ASSL (ASSL для XMLA)](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [Развертывание проектов служб Analysis Services & #40; SSDT & #41;](../../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
  
