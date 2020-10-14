---
description: Загрузка преобразованных объектов базы данных в SQL Server (SybaseToSQL)
title: Загрузка преобразованных объектов базы данных в SQL Server (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Loading Converted Database Objects
ms.assetid: 4c59256f-99a8-4351-9559-a455813dbd06
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 6b7f9a9a69fd1f5ac685550fb91ab93ad2220f49
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92038267"
---
# <a name="loading-converted-database-objects-into-sql-server-sybasetosql"></a>Загрузка преобразованных объектов базы данных в SQL Server (SybaseToSQL)
После преобразования объектов базы данных «адаптивный сервер предприятия» (ASE) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure можно загрузить результирующие объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Можно либо создать объекты SSMA, либо создавать сценарии для объектов и выполнять сценарии самостоятельно. Кроме того, SSMA позволяет обновлять целевые метаданные фактическим содержимым [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базой данных SQL Azure.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Выбор между синхронизацией и скриптами  
Если вы хотите загрузить преобразованные объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure без изменений, можно создать или повторно создать объекты базы данных с помощью SSMA. Этот метод быстро и прост, но не позволяет настраивать [!INCLUDE[tsql](../../includes/tsql-md.md)] код, определяющий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объекты или SQL Azure, кроме хранимых процедур.  
  
Если необходимо изменить объект [!INCLUDE[tsql](../../includes/tsql-md.md)] , который используется для создания объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure или требуется больший контроль над временем и способом создания объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, используйте SSMA для создания [!INCLUDE[tsql](../../includes/tsql-md.md)] скриптов. Затем можно изменить эти скрипты, создать каждый объект по отдельности и даже использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure агент, чтобы запланировать создание этих объектов.  
  
## <a name="using-ssma-to-load-objects-into-sql-server-or-sql-azure"></a>Использование SSMA для загрузки объектов в SQL Server или SQL Azure  
Чтобы использовать SSMA для создания [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объектов или базы данных SQL Azure, выберите объекты в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure обозревателе метаданных, а затем синхронизируйте объекты с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, как показано в следующей процедуре. По умолчанию, если объекты уже существуют в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure и метаданные SSMA имеют некоторые локальные изменения или обновления определения этих объектов, SSMA изменяет определения объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Поведение по умолчанию можно изменить, отредактировав **Параметры проекта**.  
  
> [!NOTE]  
> Можно выбрать существующие [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объекты или базы данных SQL Azure, которые не были преобразованы из баз данных ASE. Однако эти объекты не будут созданы повторно или изменены с помощью SSMA.  
  
**Синхронизация объектов с SQL Server или SQL Azure**  
  
1.  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure обозревателе метаданных разверните узел верхнего [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, а затем разверните узел **базы данных**.  
  
2.  Выберите объекты для обработки:  
  
    -   Чтобы синхронизировать полную базу данных, установите флажок рядом с именем базы данных.  
  
    -   Чтобы синхронизировать или опустить отдельные объекты или категории объектов, установите или снимите флажок рядом с объектом или папкой.  
  
3.  Выбрав объекты для обработки в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure обозревателе метаданных, щелкните правой кнопкой мыши **базы данных**и выберите команду **синхронизировать с базой данных**.  
  
    Можно также синхронизировать отдельные объекты или категории объектов, щелкнув правой кнопкой мыши объект или его родительскую папку, а затем выбрав команду  **синхронизировать с базой данных**.  
  
    После этого SSMA отобразит диалоговое окно **Синхронизация с базой данных** , в котором можно увидеть две группы элементов. В левой части SSMA показывает выбранные объекты базы данных, представленные в дереве. С правой стороны можно увидеть дерево, представляющее те же объекты в метаданных SSMA. Вы можете развернуть дерево, нажав правую кнопку "+" или находящуюся слева. Направление синхронизации отображается в столбце действие, размещенном между двумя деревьями.  
  
    Знак действия может находиться в трех состояниях:  
  
    -   Стрелка влево означает, что содержимое метаданных будет сохранено в базе данных (по умолчанию).  
  
    -   Стрелка вправо означает, что содержимое базы данных перезапишет метаданные SSMA.  
  
    -   Перекрестная подпись означает, что никакие действия не выполняются.  
  
Щелкните знак действия, чтобы изменить состояние. Фактическая синхронизация будет выполнена при нажатии кнопки **ОК** диалогового окна **Синхронизация с базой данных** .  
  
## <a name="scripting-objects"></a>Создание скриптов для объектов  
Если необходимо сохранить [!INCLUDE[tsql](../../includes/tsql-md.md)] определения преобразованных объектов базы данных или необходимо изменить определения объектов и выполнить скрипты самостоятельно, можно сохранить преобразованные определения объектов базы данных в [!INCLUDE[tsql](../../includes/tsql-md.md)] скрипты.  
  
**Сохранение объектов в виде скриптов**  
  
1.  Выбрав объекты для сохранения в скрипт, щелкните правой кнопкой мыши **базы данных**и выберите **Сохранить как скрипт**.  
  
    Можно также создать скрипты для отдельных объектов или категорий объектов, щелкнув правой кнопкой мыши объект или содержащую его папку, а затем выбрав команду **Сохранить скрипт**.  
  
2.  В диалоговом окне **Сохранить как** найдите папку, в которой нужно сохранить скрипт, введите имя файла в поле **имя файла** и нажмите кнопку **ОК**.  
  
    SSMA добавит расширение имени файла SQL.  
  
### <a name="modifying-scripts"></a>Изменение скриптов  
После сохранения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определений объектов или SQL Azure в виде одного или нескольких скриптов можно использовать [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для просмотра и изменения скриптов.  
  
**Изменение скрипта**  
  
1.  В меню [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Файл** наведите указатель мыши на пункт **Открыть**и выберите **Файл**.  
  
2.  В диалоговом окне **Открыть** перейдите к и выберите файл сценария, а затем нажмите кнопку **ОК**.  
  
3.  Измените и файл скрипта с помощью редактора запросов.  
  
    Дополнительные сведения о редакторе запросов см. в разделе «удобные команды и возможности редактора» [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации по.  
  
4.  Чтобы сохранить скрипт, в меню Файл выберите команду **сохранить**.  
  
### <a name="running-scripts"></a>Выполнение скриптов  
Можно выполнить сценарий или отдельные инструкции в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
**Запуск сценария**  
  
1.  В меню [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Файл** наведите указатель мыши на пункт **Открыть**и выберите **Файл**.  
  
2.  В диалоговом окне **Открыть** перейдите к и выберите файл сценария, а затем нажмите кнопку **ОК**.  
  
3.  Чтобы выполнить полный сценарий, нажмите клавишу **F5** .  
  
4.  Чтобы выполнить набор инструкций, выберите инструкции в окне редактора запросов и нажмите клавишу **F5** .  
  
Дополнительные сведения об использовании редактора запросов для выполнения скриптов см [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] . в разделе «запрос» [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации по.  
  
Скрипты также можно запускать из командной строки с помощью программы **sqlcmd** и из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента. Дополнительные сведения о программе **sqlcmd**см. в разделе «Программа sqlcmd» [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации по. Дополнительные сведения об [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агенте см. в разделе «Автоматизация административных задач ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент)» [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации по.  
  
## <a name="securing-objects-in-sql-server"></a>Защита объектов в SQL Server  
После загрузки преобразованных объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно предоставлять и запрещать разрешения на эти объекты. Рекомендуется сделать это перед переносом данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Сведения о защите объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе «вопросы безопасности для баз данных и приложений баз данных» [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] электронной документации по.  
  
## <a name="next-step"></a>Следующий шаг  
Следующим шагом процесса миграции является [Перенос данных SYBASE ASE в SQL Server или SQL Azure (SybaseToSQL)](./migrating-sybase-ase-data-into-sql-server-azure-sql-db-sybasetosql.md).  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных Sybase ASE в SQL Server — база данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
