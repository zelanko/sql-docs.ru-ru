---
title: Построение проектов служб Analysis Services (SSDT) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Analysis Services], building
- Business Intelligence Development Studio, project building [Analysis Services]
ms.assetid: caac03cb-b2b4-4652-8913-3dd39c4b0127
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97e32b80d19675b3763101d1c226529a48e23e68
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66076771"
---
# <a name="build-analysis-services-projects-ssdt"></a>Построение проектов служб Analysis Services (среда SSDT)
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
  
 Эти XML-файлы не содержат \<Create > и \<Alter > теги, которые формируются при развертывании.  
  
 Связанные сборки (за исключением стандартной системной сборки и сборки служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ) также копируются в выходной каталог. При наличии связей с другими проектами решения, эти проекты сначала собираются, используя соответствующую конфигурацию проекта и зависимости построения, заданные связями проекта, а затем копируются в выходную папку проекта.  
  
## <a name="see-also"></a>См. также  
 [Язык сценариев Analysis Services &#40;ASSL&#41; ссылки](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)   
 [Развертывание проектов служб Analysis Services (среда SSDT)](deploy-analysis-services-projects-ssdt.md)  
  
  
