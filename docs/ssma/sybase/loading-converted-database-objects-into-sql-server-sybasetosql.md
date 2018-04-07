---
title: Загрузка преобразованных объектов базы данных, в SQL Server (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Loading Converted Database Objects
ms.assetid: 4c59256f-99a8-4351-9559-a455813dbd06
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f57bd83c71660e4268758bcf47cd30c2b9b3e1c8
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="loading-converted-database-objects-into-sql-server-sybasetosql"></a>Загрузка преобразованных объектов базы данных, в SQL Server (SybaseToSQL)
После преобразования объектов базы данных Sybase адаптивной Server Enterprise (ASE) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, вы можете загрузить полученные объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. Можно иметь SSMA создания объектов, или можно внести в скрипт объекты и запускать скрипты самостоятельно. Кроме того, SSMA позволяет заменить метаданные целевой фактическое содержимое [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Выбор между синхронизации и сценарии  
Если вы хотите загрузить объекты преобразованную базу данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure без изменений, может иметь SSMA непосредственного создания или повторного создания объектов базы данных. Этот метод выполняется быстро и просто, но не разрешает настройку [!INCLUDE[tsql](../../includes/tsql_md.md)] код, который определяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или объектов, SQL Azure, отличных от хранимых процедур.  
  
Если вы хотите изменить [!INCLUDE[tsql](../../includes/tsql_md.md)] , используемый для создания объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, или если вы хотите более полно контролировать время и способ создания объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, используйте SSMA для создания [!INCLUDE[tsql](../../includes/tsql_md.md)] сценариев. Можно изменить эти сценарии, создайте каждый объект отдельно и даже использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или агент SQL Azure, чтобы запланировать создание этих объектов.  
  
## <a name="using-ssma-to-load-objects-into-sql-server-or-sql-azure"></a>С помощью SSMA для загрузки объектов в SQL Server или SQL Azure  
Использование SSMA для создания [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или объекты базы данных SQL Azure, выберите объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или обозреватель метаданных SQL Azure, а затем синхронизировать объекты с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, как показано в следующей процедуре. По умолчанию, если объекты, уже существующие в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure и если SSMA метаданных имеет некоторые локальные изменения или обновления определения этих объектов очень, то SSMA приведут к изменению определения объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. Поведение по умолчанию можно изменить путем редактирования **параметры проекта**.  
  
> [!NOTE]  
> Можно выбрать существующий [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или объекты базы данных SQL Azure, которые не были преобразованы из ASE баз данных. Тем не менее эти объекты не будет повторно создан или изменен с SSMA.  
  
**Для синхронизации объектов с SQL Server или SQL Azure**  
  
1.  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или обозреватель метаданных SQL Azure, разверните в верхней [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или узел SQL Azure, а затем разверните **баз данных**.  
  
2.  Выберите объекты для обработки:  
  
    -   Чтобы синхронизировать всей базы данных, установите флажок рядом с именем базы данных.  
  
    -   Чтобы синхронизировать или исключить отдельные объекты или категории объектов, установите или снимите флажок рядом с объекту или папке.  
  
3.  После выбора объектов для обработки в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или обозреватель метаданных SQL Azure, щелкните правой кнопкой мыши **баз данных**, а затем нажмите кнопку **синхронизации с базой данных**.  
  
    Вы также можете синхронизировать отдельных объектов и категории объектов, щелкните правой кнопкой мыши объект или ее родительскую папку, выберите команду **синхронизации с базой данных**.  
  
    После этого будет отображаться SSMA **синхронизации с базой данных** диалоговое окно, в котором имеются две группы элементов. На левой стороне SSMA показывает выбранные объекты базы данных представлены в дереве. С правой стороны появится дерево, представляющее те же объекты в метаданных SSMA. Вы можете разверните дерево, щелкнув вправо или влево кнопку «+». Направление синхронизации отображается в столбце действий, который располагается между двумя деревьев.  
  
    Знак действие может находиться в трех состояниях:  
  
    -   Стрелка влево означает, что содержимое метаданные сохраняются в базе данных (по умолчанию).  
  
    -   Стрелка вправо означает, что содержимое базы данных перезапишет SSMA метаданных.  
  
    -   Знак перекрестного означает, что будет выполнено никаких действий.  
  
Щелкните знак «действие» для изменения состояния. Фактический синхронизация будет выполняться при нажатии кнопки **ОК** кнопки **синхронизации с базой данных** диалогового окна.  
  
## <a name="scripting-objects"></a>Создание скриптов для объектов  
Если вы хотите сохранить [!INCLUDE[tsql](../../includes/tsql_md.md)] определений объектов преобразованную базу данных, или необходимо изменить определения объектов и выполнения скриптов самостоятельно, ее можно сохранить определения объектов, [!INCLUDE[tsql](../../includes/tsql_md.md)] сценариев.  
  
**Для сохранения объектов в виде скриптов**  
  
1.  После выбора объектов для сохранения скрипта, щелкните правой кнопкой мыши **баз данных**, а затем выберите **Сохранение скрипта**.  
  
    Можно также создать скрипт отдельных объектов и категории объектов, щелкните правой кнопкой мыши объект или содержащую его папку, а затем выбрав **сохранить скрипт**.  
  
2.  В **Сохранить как** диалогового окна поле, перейдите в папку, в которой вы хотите сохранить скрипт, введите имя файла в **имя файла** , а затем щелкните **ОК**.  
  
    SSMA добавит .sql расширение имени файла.  
  
### <a name="modifying-scripts"></a>Изменение скриптов  
После сохранения [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или определения объектов SQL Azure как один или несколько сценариев, можно использовать [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] для просмотра и изменения скриптов.  
  
**Изменение сценария**  
  
1.  На [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] **файл** последовательно выберите пункты **откройте**, а затем нажмите кнопку **файл**.  
  
2.  В **откройте** диалоговое окно, перейдите и выберите файл сценария и нажмите кнопку **ОК**.  
  
3.  Изменить и файл скрипта с помощью редактора запросов.  
  
    Дополнительные сведения о редакторе запросов см. в разделе «Редактор удобных команд и компоненты» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации.  
  
4.  Чтобы сохранить скрипт, в меню файл, выберите **Сохранить**.  
  
### <a name="running-scripts"></a>Выполнение сценариев  
Можно запустить сценарий или отдельные инструкции в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
**Для выполнения сценария**  
  
1.  На [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] **файл** последовательно выберите пункты **откройте**, а затем нажмите кнопку **файл**.  
  
2.  В **откройте** диалоговое окно, перейдите и выберите файл сценария и нажмите кнопку **ОК**.  
  
3.  Чтобы выполнить полный сценарий, нажмите клавишу **F5** ключа.  
  
4.  Чтобы выполнить набор инструкций, инструкции select, в окне редактора запросов и нажмите клавишу **F5** ключа.  
  
Дополнительные сведения о том, как использовать редактор запросов для выполнения скриптов см. в разделе «[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] [!INCLUDE[tsql](../../includes/tsql_md.md)] запрос» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации.  
  
Можно также выполнять скрипты из командной строки с помощью **sqlcmd** программы и от [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] агента. Дополнительные сведения о **sqlcmd**, содержатся в разделе «программа sqlcmd» [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации. Дополнительные сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] агента, в разделе «Автоматизация административных задач ([!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] агента)» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации по.  
  
## <a name="securing-objects-in-sql-server"></a>Защита объектов в SQL Server  
После загрузки объектов преобразованную базу данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], можно предоставлять и отменить разрешения на доступ к объектам. Рекомендуется сделать это перед переносом данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Для получения сведений о способах обеспечения безопасности объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], в разделе «Безопасность вопросы для баз данных и базы данных приложений» в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="next-step"></a>Следующий шаг  
Следующим шагом в процессе миграции должно [переноса данных Sybase ASE в SQL Server / SQL Azure(SybaseToSQL)](http://msdn.microsoft.com/en-us/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных Sybase ASE в SQL Server — Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
