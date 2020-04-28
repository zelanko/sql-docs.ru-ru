---
title: Загрузка преобразованных объектов базы данных в SQL Server (Акцесстоскл) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
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
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 7effaa973b7a39df6fc0b9385a5cfde4fdad18d4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67986319"
---
# <a name="loading-converted-database-objects-into-sql-server-accesstosql"></a>Загрузка преобразованных объектов базы данных в SQL Server (Акцесстоскл)
После преобразования объектов базы данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure можно загрузить результирующие объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Можно либо создать объекты SSMA, либо создавать сценарии для объектов и выполнять сценарии самостоятельно. Кроме того, SSMA позволяет обновлять целевые метаданные фактическим содержимым [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure базе данных.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Выбор между синхронизацией и скриптами  
Если вы хотите загрузить преобразованные объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure без изменений, можно создать или повторно создать объекты базы данных с помощью SSMA. Этот метод быстро и прост, но не позволяет настраивать [!INCLUDE[tsql](../../includes/tsql-md.md)] код, определяющий объекты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, за исключением хранимых процедур.  
  
Если требуется изменить объект [!INCLUDE[tsql](../../includes/tsql-md.md)] , который используется для создания объектов, или если требуется больший контроль над созданием объектов, используйте SSMA для создания скриптов. Затем можно изменить эти скрипты, создать каждый объект по отдельности и даже [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использовать агент для планирования создания этих объектов.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>Использование SSMA для синхронизации объектов с SQL Server  
Чтобы использовать SSMA для создания [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure объектов базы данных, необходимо выбрать объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure обозревателе метаданных, а затем синхронизировать объекты с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, как показано в следующей процедуре. По умолчанию, если объекты уже существуют в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure и метаданные SSMA имеют некоторые локальные изменения или обновления определения этих объектов, SSMA изменяет определения объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Поведение по умолчанию можно изменить, отредактировав **Параметры проекта**.  
  
> [!NOTE]  
> Можно выбрать существующие [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure объекты базы данных, которые не были преобразованы из баз данных Access. Однако SSMA не будет повторно создавать или изменять эти объекты.  
  
**Синхронизация объектов с SQL Server или SQL Azure**  
  
1.  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure обозревателе метаданных разверните узел верхнего [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, а затем разверните узел **базы данных**.  
  
2.  Выберите объекты для обработки:  
  
    -   Чтобы синхронизировать полную базу данных, установите флажок рядом с именем базы данных.  
  
    -   Чтобы синхронизировать или опустить отдельные объекты или категории объектов, установите или снимите флажок рядом с объектом или папкой.  
  
3.  Выбрав объекты для обработки в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure обозревателе метаданных, щелкните правой кнопкой мыши **базы данных**и выберите команду **синхронизировать с базой данных**.  
  
    Можно также синхронизировать отдельные объекты или категории объектов, щелкнув правой кнопкой мыши объект или его родительскую папку, а затем выбрав команду **синхронизировать с базой данных**.  
  
    После этого SSMA отобразит диалоговое окно **Синхронизация с базой данных** , в котором можно увидеть две группы элементов. В левой части SSMA показывает выбранные объекты базы данных, представленные в дереве. С правой стороны можно увидеть дерево, представляющее те же объекты в метаданных SSMA. Вы можете развернуть дерево, нажав правую кнопку "+" или находящуюся слева. Направление синхронизации отображается в столбце действие, размещенном между двумя деревьями.  
  
    Знак действия может находиться в трех состояниях:  
  
    -   Стрелка влево означает, что содержимое метаданных будет сохранено в базе данных (по умолчанию).  
  
    -   Стрелка вправо означает, что содержимое базы данных перезапишет метаданные SSMA.  
  
    -   Перекрестная подпись означает, что никакие действия не выполняются.  
  
    Щелкните знак действия, чтобы изменить состояние. Фактическая синхронизация будет выполнена при нажатии кнопки **ОК** диалогового окна **Синхронизация с базой данных** .  
  
## <a name="scripting-objects"></a>Создание скриптов для объектов  
Если необходимо сохранить [!INCLUDE[tsql](../../includes/tsql-md.md)] определения преобразованных объектов базы данных или необходимо изменить определения объектов и выполнить скрипты самостоятельно, можно сохранить преобразованные определения объектов базы данных в [!INCLUDE[tsql](../../includes/tsql-md.md)] скрипты.  
  
**Сохранение одного или нескольких объектов в скрипте**  
  
1.  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обозревателе метаданных разверните узел верхнего уровня (имя сервера), а затем узел **базы данных**.  
  
2.  Выполните одно из следующих действий.  
  
    -   Чтобы создать скрипт для полной базы данных, установите флажок рядом с именем базы данных.  
  
    -   Чтобы создать скрипт или пропустить отдельные представления, разверните базу данных, разверните узел **представления**, а затем установите или снимите флажок рядом с представлением.  
  
    -   Чтобы создать скрипт или опустить отдельные таблицы, разверните базу данных, разверните узел **таблицы**, а затем установите или снимите флажок рядом с таблицей.  
  
    -   Чтобы создать скрипт или опустить отдельные индексы для таблицы, разверните таблицу, разверните узел **индексы**, а затем выберите или очистите индекс.  
  
3.  Щелкните правой кнопкой мыши **базы данных** и выберите **Сохранить как скрипт**.  
  
    Можно также создать скрипты для отдельных объектов. Чтобы создать скрипт для объекта независимо от того, какие объекты выбраны, щелкните правой кнопкой мыши объект и выберите **Сохранить как скрипт**.  
  
4.  В диалоговом окне **Сохранить как** найдите папку, в которой нужно сохранить скрипт, введите имя файла в поле **имя файла** и нажмите кнопку **ОК**.  
  
    SSMA добавит расширение имени файла SQL.  
  
### <a name="modifying-scripts"></a>Изменение скриптов  
После сохранения определений объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure в виде скрипта можно использовать [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для изменения скрипта.  
  
**Изменение скрипта**  
  
1.  В меню [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Файл** наведите указатель мыши на пункт **Открыть**и выберите **Файл**.  
  
2.  В диалоговом окне **Открыть** найдите и выберите файл сценария, а затем нажмите кнопку **ОК**.  
  
3.  Измените файл скрипта с помощью редактора запросов.  
  
    Дополнительные сведения о редакторе запросов см. в разделе «удобные команды и возможности редактора» электронной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] документации по.  
  
4.  Чтобы сохранить скрипт, в меню Файл выберите команду **сохранить**.  
  
### <a name="running-scripts"></a>Выполнение скриптов  
Можно выполнить сценарий или отдельные инструкции в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
**Запуск сценария**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] В меню **файл** наведите указатель мыши на пункт **Открыть** и выберите пункт **файл**.  
  
2.  В диалоговом окне **Открыть** найдите и выберите файл сценария, а затем нажмите кнопку **ОК**.  
  
3.  Чтобы выполнить полный сценарий, нажмите клавишу **F5** .  
  
4.  Чтобы выполнить набор инструкций, выберите инструкции в окне редактора запросов и нажмите клавишу **F5** .  
  
Дополнительные сведения об использовании редактора запросов для выполнения скриптов см. в разделе « [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] запрос» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Скрипты также можно запускать из командной строки с помощью программы **sqlcmd** и из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента. Дополнительные сведения о программе **sqlcmd**см. в разделе «Программа sqlcmd [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] » электронной документации по. Дополнительные сведения об [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агенте см. в разделе «Автоматизация административных задач [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (агент)» [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации по.  
  
## <a name="securing-objects-in-sql-server"></a>Защита объектов в SQL Server  
После загрузки преобразованных объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]можно предоставлять и запрещать разрешения на эти объекты. Рекомендуется сделать это перед переносом данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о защите объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]см. в разделе «вопросы безопасности для баз данных и приложений баз данных» электронной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] документации по.  
  
## <a name="next-step"></a>Следующий шаг  
Следующий шаг процесса миграции — [Перенос данных в SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
