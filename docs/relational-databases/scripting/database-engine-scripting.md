---
title: Работа со скриптами ядра СУБД | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: scripting
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], PowerShell
- scripts [SQL Server]
- scripting [SQL Server Database Engine]
- scripting [SQL Server Database Engine], PowerShell
ms.assetid: 9978a884-59a2-4e7f-a82a-335149f3a261
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 880606bde8711a1679871fce78c08ec8957cb98c
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43079654"
---
# <a name="database-engine-scripting"></a>Работа со сценариями компонента Database Engine
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] поддерживает среду скриптов [!INCLUDE[msCoName](../../includes/msconame-md.md)] PowerShell для управления экземплярами компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и объектами в экземплярах. Можно также строить и запускать запросы компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , содержащие [!INCLUDE[tsql](../../includes/tsql-md.md)] и XQuery, в средах, подобных средам сценариев.  
  
## <a name="sql-server-powershell"></a>SQL Server PowerShell  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включает две оснастки PowerShell [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые реализуют следующее:  
  
-   Поставщик [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell, отображающий иерархии моделей управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в виде путей PowerShell, подобных путям файловой системы. С помощью классов модели управляющих объектов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно управлять объектами, представленными на каждом узле пути.  
  
-   Набор командлетов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , реализующих команды [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Одним из командлетов является **Invoke-Sqlcmd**. Он используется для запуска скриптов запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , выполняемых с помощью программы **sqlcmd** .  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает эти возможности для запуска PowerShell.  
  
-   Модуль PowerShell **sqlps** , который может быть импортирован в сеанс PowerShell, после чего модуль загружает оснастки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Можно запускать нерегламентированные команды PowerShell в интерактивном режиме. Файлы скриптов можно запускать с помощью команды вида «.\MyFolder\MyScript.ps1».  
  
-   Файлы скриптов PowerShell можно использовать в качестве ввода для шагов заданий PowerShell агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые запускают скрипты через назначенные интервалы времени или в ответ на системные события.  
  
-   Программа **sqlps** , которая запускает PowerShell и импортирует модуль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Затем можно выполнять все действия, поддерживаемые в модуле. Программу **sqlps** можно запустить либо из командной строки, либо щелкнув правой кнопкой мыши узлы дерева обозревателя объектов среды [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio и выбрав команду **Запустить PowerShell**.  
  
## <a name="database-engine-queries"></a>Запросы к компоненту Database Engine  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] содержат три типа элементов.  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
-   Инструкции языка XQuery.  
  
-   Команды и переменные из программы **sqlcmd** .  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает три среды для построения и запуска запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
-   Запросы компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] можно запускать в интерактивном режиме и отлаживать в редакторе запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. В одном сеансе можно закодировать и отладить несколько инструкций, а затем сохранить их все в одном файле скрипта.  
  
-   Программа командной строки **sqlcmd** позволяет запускать запросы компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] в интерактивном режиме, а также запускать существующие файлы скриптов с запросами компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] обычно кодируются в интерактивном режиме в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] с помощью редактора запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] . В дальнейшем файл можно открыть в одной из следующих сред.  
  
-   Чтобы открыть файл в новом окне редактора запросов компонента [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **, воспользуйтесь меню**/**/** Открыть [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
-   Чтобы запустить файл с помощью служебной программы **sqlcmd**, укажите параметр **-i***входной_файл*.  
  
-   Чтобы запустить файл с помощью командлета **Invoke-Sqlcmd** в скриптах **PowerShell, укажите параметр** -QueryFromFile [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Для запуска скриптов через назначенные интервалы времени или в ответ на системные события используются шаги заданий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 Кроме того, для формирования скриптов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно использовать мастер формирования скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] . Можно щелкнуть объекты правой кнопкой мыши в обозревателе объектов [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , а затем выбрать пункт меню **Создать скрипт** . Команда**Создать скрипт** запускает мастер, который облегчает процесс создания скрипт.  
  
## <a name="database-engine-scripting-tasks"></a>Работа со скриптами компонента Database Engine  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Описывает порядок использования редактора кода и текстового редактора в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] для интерактивной разработки, отладки и выполнения скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] .|[Редакторы запросов и текста (SQL Server Management Studio)](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)|  
|Описывает порядок использования программы **sqlcmd** для выполнения скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] из командной строки, включая возможность интерактивной разработки скриптов.|[Связанные инструкции по sqlcmd](http://msdn.microsoft.com/library/dd7a2d2b-6327-4d77-ac5a-580d36073ad4)|  
|Описывает порядок интеграции компонентов SQL Server в среду Windows PowerShell с последующей сборкой скриптов PowerShell для управления экземплярами и объектами SQL Server.|[SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)|  
|Описывает порядок использования мастера **формирования и публикации скриптов** для создания скриптов [!INCLUDE[tsql](../../includes/tsql-md.md)] , которые повторно создают один или несколько объектов из базы данных.|[Формирование скриптов (среда SQL Server Management Studio)](../../relational-databases/scripting/generate-scripts-sql-server-management-studio.md)|  
  
## <a name="see-also"></a>См. также:  
 [Программа sqlcmd](../../tools/sqlcmd-utility.md)   
 [Учебник. Составление инструкций Transact-SQL](../../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
