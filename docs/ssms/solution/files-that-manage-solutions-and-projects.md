---
title: "Файлы для управления решениями и проектами | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [SQL Server Management Studio], files
- .ssmssln files
- .ssmsmobileproj files
- .ssmsasproj files
- .ssmssqlproj files
- .sqlsuo files
- files [SQL Server Management Studio], projects
ms.assetid: e19d2859-0b97-4727-ac27-c4c226d86b2f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 13c811a0c616a9ef859e86c688804c829ec0d9f0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/27/2017

---
# <a name="files-that-manage-solutions-and-projects"></a>Файлы для управления решениями и проектами
 <a name="-this-topic-describes-the-file-types-that-are-specific-to-includemsconameincludesmsconamemdmd-includessmanstudiofullincludesssmanstudiofullmdmd-by-default-all-solutions-and-their-projects-are-created-in-my-documentssql-server-management-studio-projects"></a>— Этот раздел описывает типы файлов, характерные для среды [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. По умолчанию все решения и их проекты создаются в папке \My Documents\SQL Server Management Studio Projects.  
 -  
 — ## Файлы решений среды Management Studio  
 -[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] использует типы файлов, отличные от тех, что используются в среде [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull_md.md)] или [!INCLUDE[msCoName](../../includes/msconame_md.md)] Visual Studio. Это означает, что открыть решение среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull_md.md)] или Visual Studio нельзя. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] файлы решений позволяют обозревателю решений открывать графический интерфейс для управления файлами.  
 -  
 -|Расширение|Тип файла|Description|Создан|  
 -|-------------|-------------|---------------|--------------|  
 -|.ssmssln|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] Объект решения|Предоставляет среду со ссылками на расположение проектов, элементов проекта и решения [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] на диске.|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]|  
 -  
 — ## Файлы проектов среды Management Studio  
 — Точно так же, как решения содержат файлы решений, управляющие объектами в решении, проекты содержат файлы проектов. Тип файла проекта, который среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] создает для проекта, зависит от шаблона, который использовался для создания этого проекта. В следующей таблице приводятся типы файлов, создаваемых для каждого проекта.  
 -  
 -|Расширение|Шаблон проекта|  
 -|-------------|--------------------|  
 -|.ssmssqlproj|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Проект скриптов|  
 -|.ssmsasproj|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)] Проект скриптов|  
 -  
 — ## Расположение файлов уровня решения  
 — По умолчанию файлы уровня решения создаются в физическом каталоге первого проекта, созданного в этом решении. Каталог для решения можно определить, создав решение или указав каталог при создании нового проекта.  
 -  
 — Если структура каталогов схожа с логической структурой, отображаемой в обозревателе решений, облегчается поиск файлов проектов и решений, а также предоставление доступа к ним для других разработчиков в команде.  
 -  
 -## См. также  
 -[Управление файлами с помощью кодировок](../../ssms/solution/manage-files-with-encoding.md)  
 -[Прочие файлы](../../ssms/solution/miscellaneous-files.md)  
 -[Обозреватель решений](../../ssms/solution/solution-explorer.md)  
 -[Решения (среда SQL Server Management Studio)](../../ssms/solution/solutions-sql-server-management-studio.md)  
 -[Проекты (SQL Server Management Studio)](../../ssms/solution/projects-sql-server-management-studio.md)  
 -[Обозреватель решений для системы управления версиями](https://msdn.microsoft.com/en-us/library/ms173879.aspx)  
  
