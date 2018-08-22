---
title: Загрузка преобразованных объектов базы данных, в SQL Server (AccessToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Access databases, loading converted objects into SQL Azure
- Access databases, loading converted objects into SQL Server
- data, securing
- loading objects into SQL Azure
- loading objects into SQL Server
- migrating objects into SQL Azure
- migrating objects into SQL Server
- moving objects into SQL Azure
- moving objects into SQL Server
- schemas, loading into SQL Azure
- schemas, loading into SQL Server
- scripting converted objects
- securing data
- SQL Azure, loading objects into
- SQL Server, loading objects into
- synchronizing metadata with SQL Azure
- synchronizing metadata with SQL Server
- uploading objects into SQL Azure
- uploading objects into SQL Server
ms.assetid: 4e854eee-b10c-4f0b-9d9e-d92416e6f2ba
caps.latest.revision: 16
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 56c600b88c9c1b3237a92887d68cb338ae17058d
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393088"
---
# <a name="loading-converted-database-objects-into-sql-server-accesstosql"></a>Загрузка преобразованных объектов базы данных, в SQL Server (AccessToSQL)
После преобразования объектов базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, можно загрузить результирующие объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Можно иметь SSMA создания объектов, или можно внести в скрипт объекты и запускать сценарии самостоятельно. Кроме того, SSMA позволяет обновлять целевые метаданные с фактическое содержимое [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Выбор между синхронизации и сценарии  
Если вы хотите загрузить объекты преобразованный базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure без изменений, у вас может быть SSMA непосредственного создания или повторного создания объектов базы данных. Этот метод выполняется быстро и просто, но не позволяет настраивать [!INCLUDE[tsql](../../includes/tsql-md.md)] код, который определяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или объекты SQL Azure, отличные от хранимых процедур.  
  
Если вы хотите изменить [!INCLUDE[tsql](../../includes/tsql-md.md)] , используемый для создания объектов, или если требуется больший контроль над создания объектов, используйте SSMA для создания скриптов. Можно затем изменить скрипты, создайте каждый объект по отдельности и даже использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента для планирования, создания этих объектов.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>С помощью SSMA для синхронизации объектов с SQL Server  
Создать с помощью SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или объекты базы данных SQL Azure, выберите объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или обозреватель метаданных SQL Azure и затем выполнить синхронизацию объектов с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, как показано в следующей процедуре. По умолчанию, если объект уже существует в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure и если метаданные SSMA имеет некоторые локальные изменения или обновления к определению этих очень объектов, то SSMA изменим определения объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Поведение по умолчанию можно изменить путем редактирования **параметры проекта**.  
  
> [!NOTE]  
> Можно выбрать имеющиеся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или объекты базы данных SQL Azure, которые не были преобразованы из базы данных Access. Тем не менее SSMA не будет повторно создать или изменить эти объекты.  
  
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
  
**Чтобы сохранить один или несколько объектов в сценарий**  
  
1.  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозреватель метаданных, разверните верхний узел (имя сервера), а затем разверните **баз данных**.  
  
2.  Выполните одно или несколько из следующих:  
  
    -   Чтобы создать скрипт всей базы данных, установите флажок рядом с именем базы данных.  
  
    -   Для скрипта или опустить отдельных представлений, разверните базу данных, разверните **представления**, а затем установите или снимите флажок рядом с представления.  
  
    -   Для скриптов или пропустите отдельных таблиц, разверните базу данных, разверните **таблиц**, а затем установите или снимите флажок рядом с таблицей.  
  
    -   Для скриптов или пропустите отдельных индексов для таблицы, разверните таблицу, разверните **индексы**, а затем установите или снимите индекс.  
  
3.  Щелкните правой кнопкой мыши **баз данных** и выберите **сохранить в виде скрипта**.  
  
    Можно также создать скрипт для отдельных объектов. Создание скрипта для объекта, независимо от выбранных объектов, щелкните правой кнопкой мыши объект и выберите **сохранить в виде скрипта**.  
  
4.  В **Сохранить как** диалоговом окне перейдите в папку, где требуется сохранить скрипт, введите имя файла в **имя файла** , а затем щелкните **ОК**.  
  
    SSMA добавляет расширение имени файла .sql.  
  
### <a name="modifying-scripts"></a>Изменение скриптов  
После сохранения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или определения объектов SQL Azure, как сценарий, можно использовать [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для изменения сценария.  
  
**Изменение сценария**  
  
1.  На [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **файл** последовательно выберите пункты **откройте**, а затем нажмите кнопку **файл**.  
  
2.  В **откройте** диалоговом окне найдите и выберите свой файл сценария и нажмите кнопку **ОК**.  
  
3.  Измените файл скрипта с помощью редактора запросов.  
  
    Дополнительные сведения о редакторе запросов, см. в разделе «Редактор удобных команд и компоненты» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
4.  Чтобы сохранить скрипт, в меню "файл", выберите **Сохранить**.  
  
### <a name="running-scripts"></a>Выполнение сценариев  
Вы можете запустить сценарий или отдельные инструкции в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
**Для выполнения скрипта**  
  
1.  На [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **файл** последовательно выберите пункты **откройте** и нажмите кнопку **файл**.  
  
2.  В **откройте** диалоговом окне найдите и выберите свой файл сценария и нажмите кнопку **ОК**.  
  
3.  Чтобы выполнить весь скрипт, нажмите клавишу **F5** ключ.  
  
4.  Чтобы выполнить набор инструкций, инструкции select в окно редактора запросов и нажмите клавишу **F5** ключ.  
  
Дополнительные сведения о том, как использовать редактор запросов для выполнения скриптов см. в разделе "[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] запроса» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
Можно также выполнять сценарии из командной строки с использованием **sqlcmd** служебной программы и из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента. Дополнительные сведения о **sqlcmd**, см. в разделе «программы sqlcmd» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online. Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента, см. в разделе «Автоматизация административных задач ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента)» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
## <a name="securing-objects-in-sql-server"></a>Защита объектов в SQL Server  
После загрузки объекты преобразованный базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно предоставлять и запрещать разрешения для этих объектов. Рекомендуется сделать это перед миграцией данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о способах обеспечения безопасности объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе «Безопасность вопросы для баз данных и базы данных приложений» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.  
  
## <a name="next-step"></a>Следующий шаг  
Следующим шагом в процессе миграции является [переноса данных в SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
