---
title: Работа со скриптами ядра СУБД | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
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
ms.openlocfilehash: 7bf36beb01ee7d31b78e6bdf06921bc460bcbbad
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48199214"
---
# <a name="database-engine-scripting"></a>Работа со сценариями компонента Database Engine
  [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] поддерживает среду скриптов [!INCLUDE[msCoName](../../includes/msconame-md.md)] PowerShell для управления экземплярами компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и объектами в экземплярах. Можно также строить и запускать запросы компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , содержащие [!INCLUDE[tsql](../../includes/tsql-md.md)] и XQuery, в средах, подобных средам сценариев.  
  
## <a name="sql-server-powershell"></a>SQL Server PowerShell  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включает две оснастки PowerShell [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые реализуют следующее:  
  
-   Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell, отображающий иерархии моделей управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в виде путей PowerShell, подобных путям файловой системы. С помощью классов модели управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно управлять объектами, представленными на каждом узле пути.  
  
-   Набор командлетов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , реализующих команды [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Одним из командлетов является **Invoke-Sqlcmd**. Это используется для запуска [!INCLUDE[ssDE](../../includes/ssde-md.md)] скриптов, выполняемых с помощью запросов `sqlcmd` служебной программы.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает эти возможности для запуска PowerShell.  
  
-   Модуль PowerShell **sqlps** , который может быть импортирован в сеанс PowerShell, после чего модуль загружает оснастки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Можно запускать нерегламентированные команды PowerShell в интерактивном режиме. Файлы скриптов можно запускать с помощью команды вида «.\MyFolder\MyScript.ps1».  
  
-   Файлы скриптов PowerShell можно использовать в качестве ввода для шагов заданий PowerShell агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые запускают скрипты через назначенные интервалы времени или в ответ на системные события.  
  
-   Программа **sqlps** , которая запускает PowerShell и импортирует модуль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Затем можно выполнять все действия, поддерживаемые в модуле. Программу **sqlps** можно запустить либо из командной строки, либо щелкнув правой кнопкой мыши узлы дерева обозревателя объектов среды [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio и выбрав команду **Запустить PowerShell**.  
  
## <a name="database-engine-queries"></a>Запросы к компоненту Database Engine  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] содержат три типа элементов.  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
-   Инструкции языка XQuery.  
  
-   Команды и переменные из `sqlcmd` служебной программы.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает три среды для построения и запуска запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
-   Запросы компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] можно запускать в интерактивном режиме и отлаживать в редакторе запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. В одном сеансе можно закодировать и отладить несколько инструкций, а затем сохранить их все в одном файле скрипта.  
  
-   `sqlcmd` Служебная программа командной строки позволяет в интерактивном режиме [!INCLUDE[ssDE](../../includes/ssde-md.md)] запросы, а также запускать существующие [!INCLUDE[ssDE](../../includes/ssde-md.md)] файлы скриптов с запросами.  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] обычно кодируются в интерактивном режиме в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] с помощью редактора запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . В дальнейшем файл можно открыть в одной из следующих сред.  
  
-   Чтобы открыть файл в новом окне редактора запросов компонента [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **, воспользуйтесь меню**/**/** Открыть [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
-   Используйте **-i *** входной_файл* параметр, чтобы запустить файл с `sqlcmd` служебной программы.  
  
-   Чтобы запустить файл с помощью командлета **Invoke-Sqlcmd** в скриптах **PowerShell, укажите параметр** -QueryFromFile [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Для запуска скриптов через назначенные интервалы времени или в ответ на системные события используются шаги заданий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 Кроме того, для формирования скриптов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать мастер формирования скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] . Можно щелкнуть объекты правой кнопкой мыши в обозревателе объектов [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , а затем выбрать пункт меню **Создать скрипт** . Команда**Создать скрипт** запускает мастер, который облегчает процесс создания скрипт.  
  
## <a name="database-engine-scripting-tasks"></a>Работа со скриптами компонента Database Engine  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Описывает порядок использования редактора кода и текстового редактора в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] для интерактивной разработки, отладки и выполнения скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] .|[Редакторы запросов и текста (SQL Server Management Studio)](../scripting/query-and-text-editors-sql-server-management-studio.md)|  
|Описывает использование `sqlcmd` выполнения служебной программой [!INCLUDE[tsql](../../includes/tsql-md.md)] скриптов из командной строки, включая возможность интерактивной разработки скриптов.|[Связанные инструкции по sqlcmd](../../database-engine/sqlcmd-how-to-topics.md)|  
|Описывает порядок интеграции компонентов SQL Server в среду Windows PowerShell 2.0 с последующим построением скриптов PowerShell для управления экземплярами и объектами SQL Server.|[SQL Server PowerShell](../../powershell/sql-server-powershell.md)|  
|Описывает порядок использования мастера **формирования и публикации скриптов** для создания скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] , которые повторно создают один или несколько объектов из базы данных.|[Формирование скриптов (среда SQL Server Management Studio)](generate-scripts-sql-server-management-studio.md)|  
  
## <a name="see-also"></a>См. также  
 [Программа sqlcmd](../../tools/sqlcmd-utility.md)   
 [Учебник. Составление инструкций Transact-SQL](../../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
