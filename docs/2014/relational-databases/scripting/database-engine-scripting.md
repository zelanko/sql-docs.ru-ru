---
title: Работа со сценариями компонента Database Engine
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], PowerShell
- scripts [SQL Server]
- scripting [SQL Server Database Engine]
- scripting [SQL Server Database Engine], PowerShell
ms.assetid: 9978a884-59a2-4e7f-a82a-335149f3a261
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0b092c85ea678ce05c3b9c8bbff4f78d47589bdb
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2019
ms.locfileid: "75244963"
---
# <a name="database-engine-scripting"></a>Работа со сценариями компонента Database Engine
  
  [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] поддерживает среду скриптов [!INCLUDE[msCoName](../../includes/msconame-md.md)] PowerShell для управления экземплярами компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и объектами в экземплярах. Можно также строить и запускать запросы компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , содержащие [!INCLUDE[tsql](../../includes/tsql-md.md)] и XQuery, в средах, подобных средам сценариев.  
  
## <a name="sql-server-powershell"></a>SQL Server PowerShell  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]включает две [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оснастки PowerShell, реализующие:  
  
-   Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell, отображающий иерархии моделей управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в виде путей PowerShell, подобных путям файловой системы. С помощью классов модели управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно управлять объектами, представленными на каждом узле пути.  
  
-   Набор командлетов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , реализующих команды [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Одним из командлетов является **Invoke-Sqlcmd**. Используется для запуска [!INCLUDE[ssDE](../../includes/ssde-md.md)] скриптов запросов, запускаемых с помощью `sqlcmd` программы.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает эти возможности для запуска PowerShell.  
  
-   Модуль PowerShell **sqlps** , который можно импортировать в сеанс PowerShell, затем модуль загружает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] оснастки. Вы можете запускать нерегламентированные команды PowerShell в интерактивном режиме. Файлы скриптов можно запускать с помощью команды вида «.\MyFolder\MyScript.ps1».  
  
-   Файлы скриптов PowerShell можно использовать в качестве ввода для шагов заданий PowerShell агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые запускают скрипты через назначенные интервалы времени или в ответ на системные события.  
  
-   Программа **sqlps** , которая запускает PowerShell и импортирует модуль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Затем можно выполнять все действия, поддерживаемые в модуле. Программу **sqlps** можно запустить либо из командной строки, либо щелкнув правой кнопкой мыши узлы дерева обозревателя объектов среды [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio и выбрав команду **Запустить PowerShell**.  
  
## <a name="database-engine-queries"></a>Запросы к компоненту Database Engine  
 
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] содержат три типа элементов.  
  
-   
  [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
-   Инструкции языка XQuery.  
  
-   Команды и переменные из `sqlcmd` программы.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]предоставляет три среды для создания и выполнения [!INCLUDE[ssDE](../../includes/ssde-md.md)] запросов:  
  
-   Запросы компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] можно запускать в интерактивном режиме и отлаживать в редакторе запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. В одном сеансе можно закодировать и отладить несколько инструкций, а затем сохранить их все в одном файле скрипта.  
  
-   Программа `sqlcmd` командной строки позволяет выполнять [!INCLUDE[ssDE](../../includes/ssde-md.md)] запросы в интерактивном режиме, а также запускать существующие [!INCLUDE[ssDE](../../includes/ssde-md.md)] файлы сценариев запросов.  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]файлы скриптов запросов обычно кодируются в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] интерактивном режиме с помощью редактора [!INCLUDE[ssDE](../../includes/ssde-md.md)] запросов. В дальнейшем файл можно открыть в одной из следующих сред.  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ****/Используйте меню**Открыть** файл, чтобы открыть файл в новом [!INCLUDE[ssDE](../../includes/ssde-md.md)] окне редактора запросов.  
  
-   Используйте параметр **-i**_input_file_ для запуска файла с помощью `sqlcmd` программы.  
  
-   Чтобы запустить файл с помощью командлета **Invoke-Sqlcmd** в скриптах **PowerShell, укажите параметр** -QueryFromFile [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Для запуска скриптов через назначенные интервалы времени или в ответ на системные события используются шаги заданий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 Кроме того, для формирования скриптов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать мастер формирования скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] . Можно щелкнуть объекты правой кнопкой мыши в обозревателе объектов [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , а затем выбрать пункт меню **Создать скрипт** . **Создать скрипт** запускает мастер, который помогает выполнить процесс создания скрипта.  
  
## <a name="database-engine-scripting-tasks"></a>Работа со скриптами компонента Database Engine  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Описывает порядок использования редактора кода и текстового редактора в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] для интерактивной разработки, отладки и выполнения скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] .|[Редакторы запросов и текста &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md)|  
|Описывает порядок использования программы `sqlcmd` для выполнения скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] из командной строки, включая возможность интерактивной разработки скриптов.|[Разделы руководства по sqlcmd](../../database-engine/sqlcmd-how-to-topics.md)|  
|Описывает порядок интеграции компонентов SQL Server в среду Windows PowerShell 2.0 с последующим построением скриптов PowerShell для управления экземплярами и объектами SQL Server.|[SQL Server PowerShell](../../powershell/sql-server-powershell.md)|  
|Описывает порядок использования мастера **формирования и публикации скриптов** для создания скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] , которые повторно создают один или несколько объектов из базы данных.|[Создание скриптов &#40;SQL Server Management Studio&#41;](generate-scripts-sql-server-management-studio.md)|  
  
## <a name="see-also"></a>См. также  
 [Программа sqlcmd](../../tools/sqlcmd-utility.md)   
 [Учебник. Написание инструкций Transact-SQL](../../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
