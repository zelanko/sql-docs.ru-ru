---
title: Задание и получение сведений о версии | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- historical information [SQL Server]
- source controls [SQL Server Management Studio], version information
- retrieving version information
- current file version information
- version control services [SQL Server], retrieving version information
- version control services [SQL Server], setting version information
- status information [SQL Server], source control files
- historical information [SQL Server], source control files
ms.assetid: c3f253c4-4e3d-48e8-8d90-bd6ee899faf7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 68113c6de003aea94924f6e220373664212becf1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62843487"
---
# <a name="set-and-retrieve-version-information"></a>Задание и получение сведений о версии
  Сведения о версии содержат журнал изменений и текущее состояние файла в системе управления версиями. Для каждого файла, контролируемого системой управления версиями, [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe создает исчерпывающий журнал, с помощью которого с течением времени можно проследить развитие одного или нескольких файлов. Эти сведения можно также использовать для получения локальной копии версии файла или сравнения двух любых версий файла.  
  
 Журнал файла содержит:  
  
-   номер версии, определяющий его место в последовательности других версий данного файла;  
  
-   выполненные операции; отслеживаются операции создания, возврата и удаления файла;  
  
-   имя пользователя, выполнявшего операции с использованием файла;  
  
-   дату и время выполнения операции.  
  
 Приложение Visual SourceSafe также сохраняет сведения о состоянии загруженного в данный момент решения. Эти сведения обеспечивают создание моментального снимка текущего состояния файла, включая:  
  
-   удостоверение пользователя, извлекшего файл;  
  
-   номер последней версии выбранного файла;  
  
-   дату создания версии;  
  
-   примечание пользователя, связанное с версией;  
  
-   пути проектов, имеющих общий доступ к этому файлу.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Просмотр журнал файла](../../2014/database-engine/view-file-history.md)  
  
-   [Просмотр журнала проекта](../../2014/database-engine/view-project-history.md)  
  
-   [Просмотр состояния файла](../../2014/database-engine/view-file-status.md)  
  
-   [Получение файлов](../../2014/database-engine/retrieve-files.md)  
  
-   [Указание версии в качестве последней](../../2014/database-engine/specify-a-version-as-the-latest-version.md)  
  
-   [Сравнение файлов](../../2014/database-engine/compare-files.md)  
  
-   [Открытие файлов для общего доступа](../../2014/database-engine/share-files.md)  
  
-   [Создание журналов и отчетов состояния](../../2014/database-engine/create-history-and-status-reports.md)  
  
## <a name="see-also"></a>См. также:  
 [Основы системы управления версиями](../../2014/database-engine/source-control-basics.md)  
  
  
