---
title: Загрузка преобразованных объектов базы данных, в SQL Server (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Loading Converted Database Objects
ms.assetid: 4c59256f-99a8-4351-9559-a455813dbd06
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 96e2bee47c97e85421b074e870c9dab1dd46220a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63245883"
---
# <a name="loading-converted-database-objects-into-sql-server-sybasetosql"></a>Загрузка преобразованных объектов базы данных в SQL Server (SybaseToSQL)
После преобразования объектов базы данных Sybase Adaptive Server Enterprise (ASE) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, можно загрузить результирующие объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Можно иметь SSMA создания объектов, или можно внести в скрипт объекты и запускать сценарии самостоятельно. Кроме того, SSMA позволяет обновлять целевые метаданные с фактическое содержимое [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Выбор между синхронизации и сценарии  
Если вы хотите загрузить объекты преобразованный базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure без изменений, у вас может быть SSMA непосредственного создания или повторного создания объектов базы данных. Этот метод выполняется быстро и просто, но не позволяет настраивать [!INCLUDE[tsql](../../includes/tsql-md.md)] код, который определяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или объекты SQL Azure, отличные от хранимых процедур.  
  
Если вы хотите изменить [!INCLUDE[tsql](../../includes/tsql-md.md)] , используемый для создания объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, или если вы хотите более гибко управлять как и когда объекты создаются в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, используйте SSMA для создания [!INCLUDE[tsql](../../includes/tsql-md.md)] сценариев. Можно затем изменить скрипты, создайте каждый объект по отдельности и даже использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или агента SQL Azure для планирования, создания этих объектов.  
  
## <a name="using-ssma-to-load-objects-into-sql-server-or-sql-azure"></a>С помощью SSMA для загрузки объектов в SQL Server или SQL Azure  
Создать с помощью SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или объекты базы данных SQL Azure, выберите объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или обозреватель метаданных SQL Azure и затем выполнить синхронизацию объектов с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, как показано в следующей процедуре. По умолчанию, если объект уже существует в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure и если метаданные SSMA имеет некоторые локальные изменения или обновления к определению этих очень объектов, то SSMA изменим определения объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Поведение по умолчанию можно изменить путем редактирования **параметры проекта**.  
  
> [!NOTE]  
> Можно выбрать имеющиеся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или объекты базы данных SQL Azure, которые не были преобразованы из ASE баз данных. Тем не менее эти объекты не будет повторно создан или изменен с SSMA.  
  
**Для синхронизации объектов с SQL Server или SQL Azure**  
  
1.  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или обозреватель метаданных SQL Azure, разверните верхней [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или узел SQL Azure, а затем разверните **баз данных**.  
  
2.  Выберите объекты для обработки:  
  
    -   Чтобы синхронизировать всей базы данных, установите флажок рядом с именем базы данных.  
  
    -   Для синхронизации или пропуск отдельных объектов или категории объектов, установите или снимите флажок рядом с объектом или папки.  
  
3.  После выбора объектов для обработки в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или обозреватель метаданных SQL Azure, щелкните правой кнопкой мыши **баз данных**, а затем нажмите кнопку **синхронизация с базой данных**.  
  
    Вы также можете синхронизировать отдельных объектов или категории объектов, щелкнув правой кнопкой мыши объект или ее родительскую папку и нажмите кнопку **синхронизация с базой данных**.  
  
    После этого отобразится SSMA **синхронизация с базой данных** диалоговое окно, где вы увидите две группы элементов. На левой стороне SSMA показаны объекты выбранной базы данных, представленных в дереве. В правой части вы увидите дерево, представляющее те же объекты в SSMA метаданных. Вы можете развернуть дерево, нажав кнопку справа или слева кнопку «+». Направление синхронизации отображается в столбце действий помещается между двух деревьев.  
  
    Знак действие может находиться в трех состояниях:  
  
    -   Стрелка влево означает, что содержимое метаданных будут сохранены в базе данных (по умолчанию).  
  
    -   Стрелка вправо означает, что содержимое базы данных будут перезаписаны метаданные SSMA.  
  
    -   Знак перекрестного означает, что будет выполнено никаких действий.  
  
Щелкните знак "действие" для изменения состояния. Реальная синхронизация выполняется при нажатии кнопки **ОК** кнопки **синхронизация с базой данных** диалоговое окно.  
  
## <a name="scripting-objects"></a>Создание скриптов для объектов  
Если вы хотите сохранить [!INCLUDE[tsql](../../includes/tsql-md.md)] определений объектов преобразованный базы данных, или вы хотите изменить определения объектов и выполнения сценариев самостоятельно, ее можно сохранить определения объектов, [!INCLUDE[tsql](../../includes/tsql-md.md)] сценариев.  
  
**Для сохранения объектов в виде скриптов**  
  
1.  После выбора объектов, чтобы сохранить сценарий, щелкните правой кнопкой мыши **баз данных**, а затем выберите **сохранить в виде скрипта**.  
  
    Можно также создать сценарий отдельных объектов или категории объектов, щелкнув правой кнопкой мыши объект или содержащей его папки, а затем выбрав **сохранить скрипт**.  
  
2.  В **Сохранить как** диалоговом окне перейдите в папку, где требуется сохранить скрипт, введите имя файла в **имя файла** , а затем щелкните **ОК**.  
  
    SSMA добавляет расширение имени файла .sql.  
  
### <a name="modifying-scripts"></a>Изменение скриптов  
После сохранения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или определения объектов SQL Azure как один или несколько сценариев, можно использовать [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для просмотра и изменения скриптов.  
  
**Изменение сценария**  
  
1.  На [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **файл** последовательно выберите пункты **откройте**, а затем нажмите кнопку **файл**.  
  
2.  В **откройте** диалоговом окне перейдите и выберите свой файл сценария и нажмите кнопку **ОК**.  
  
3.  Изменить и файла скрипта с помощью редактора запросов.  
  
    Дополнительные сведения о редакторе запросов, см. в разделе «Редактор удобных команд и компоненты» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
4.  Чтобы сохранить скрипт, в меню "файл", выберите **Сохранить**.  
  
### <a name="running-scripts"></a>Выполнение сценариев  
Вы можете запустить сценарий или отдельные инструкции в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
**Для выполнения скрипта**  
  
1.  На [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **файл** последовательно выберите пункты **откройте**, а затем нажмите кнопку **файл**.  
  
2.  В **откройте** диалоговом окне перейдите и выберите свой файл сценария и нажмите кнопку **ОК**.  
  
3.  Чтобы выполнить весь скрипт, нажмите клавишу **F5** ключ.  
  
4.  Чтобы выполнить набор инструкций, инструкции select в окно редактора запросов и нажмите клавишу **F5** ключ.  
  
Дополнительные сведения о том, как использовать редактор запросов для выполнения скриптов см. в разделе " [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
Можно также выполнять сценарии из командной строки с использованием **sqlcmd** служебной программы и из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента. Дополнительные сведения о **sqlcmd**, см. в разделе «программы sqlcmd» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online. Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента, см. в разделе «Автоматизация административных задач ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента) "в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
## <a name="securing-objects-in-sql-server"></a>Защита объектов в SQL Server  
После загрузки объекты преобразованный базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно предоставлять и запрещать разрешения для этих объектов. Рекомендуется сделать это перед миграцией данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о способах обеспечения безопасности объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе «Безопасность вопросы для баз данных и базы данных приложений» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг в процессе миграции является [миграция данных Sybase ASE в SQL Server / SQL Azure(SybaseToSQL)](https://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных Sybase ASE в SQL Server — база данных Azure SQL &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
