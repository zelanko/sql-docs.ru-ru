---
title: Файлы для управления решениями и проектами | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], files
- .ssmssln files
- .ssmsmobileproj files
- .ssmsasproj files
- .ssmssqlproj files
- .sqlsuo files
- files [SQL Server Management Studio], projects
ms.assetid: e19d2859-0b97-4727-ac27-c4c226d86b2f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6e8481c1cce3e43287c04678ddae10ac1b0703af
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63044396"
---
# <a name="files-that-manage-solutions-and-projects"></a>Файлы для управления решениями и проектами
  В этом разделе описываются типы файлов, характерные для среды [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. По умолчанию все решения и их проекты создаются в папке \My Documents\SQL Server Management Studio Projects.  
  
## <a name="management-studio-solution-files"></a>Файлы решений среды Management Studio  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] использует типы файлов, отличные от тех, что используются в среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio. Это означает, что открыть решение среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] или Visual Studio нельзя. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] файлы решений позволяют обозревателю решений открывать графический интерфейс для управления файлами.  
  
|Расширение|Тип файла|Описание|Создан|  
|---------------|---------------|-----------------|----------------|  
|.ssmssln|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Объект решения|Предоставляет среду со ссылками на расположение проектов, элементов проекта и решения [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на диске.|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
  
## <a name="management-studio-project-files"></a>Файлы проектов среды Management Studio  
 Точно так же, как решения содержат файлы решений, управляющие объектами в решении, проекты содержат файлы проектов. Тип файла проекта, который среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] создает для проекта, зависит от шаблона, который использовался для создания этого проекта. В следующей таблице приводятся типы файлов, создаваемых для каждого проекта.  
  
|Расширение|Шаблон проекта|  
|---------------|----------------------|  
|.ssmssqlproj|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проект скриптов|  
|.ssmsasproj|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Проект скриптов|  
  
## <a name="location-of-solution-level-files"></a>Расположение файлов уровня решения  
 По умолчанию файлы уровня решения создаются в физическом каталоге первого проекта, созданного в этом решении. Каталог для решения можно определить, создав решение или указав каталог при создании нового проекта.  
  
 Если структура каталогов схожа с логической структурой, отображаемой в обозревателе решений, облегчается поиск файлов проектов и решений, а также предоставление доступа к ним для других разработчиков в команде.  
  
## <a name="see-also"></a>См. также  
 [Управление файлами с кодировкой](manage-files-with-encoding.md)   
 [Прочие файлы](miscellaneous-files.md)   
 [Обозреватель решений](solution-explorer.md)   
 [Решения &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md)   
 [Проекты &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md)   
 [Обозреватель решений системы управления версиями](../../database-engine/solution-explorer-source-control.md)  
  
  
