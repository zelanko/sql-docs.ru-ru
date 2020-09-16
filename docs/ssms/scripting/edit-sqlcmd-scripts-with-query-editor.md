---
title: Изменение скриптов SQLCMD при помощи редактора запросов
description: Скрипты SQLCMD применяются в тех случаях, когда необходимо обработать системные команды Windows и инструкции Transact-SQL в одном и том же скрипте. Узнайте, как писать и редактировать скрипты SQLCMD с помощью редактора запросов ядра СУБД.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], SQLCMD scripts
- SQLCMD scripts
- modifying scripts
- Query Editor [Database Engine], SQLCMD scripts
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: f77b866d-c330-47c9-9e74-0b8d8dff4b31
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/14/2017
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5df33c67466a355dd7b204dcfd6f12f146ac59bb
ms.sourcegitcommit: 9e1f1c6ee8f5a10d18a2599bfd9f3eb6081829e1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2020
ms.locfileid: "89093452"
---
# <a name="edit-sqlcmd-scripts-with-query-editor"></a>Изменение скриптов SQLCMD при помощи редактора запросов

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Используя редактор запросов [!INCLUDE[ssDE](../../includes/ssde-md.md)] в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] можно записывать и редактировать запросы в виде скриптов SQLMD. Скрипты SQLCMD применяются в тех случаях, когда необходимо обработать системные команды Windows и инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] в одном и том же скрипте.  
  
## <a name="sqlcmd-mode"></a>Режим SQLCMD  
 Чтобы при помощи редактора запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] писать и изменять скрипты SQLCMD, необходимо включить режим скриптов SQLCMD. По умолчанию режим скриптов SQLCMD в редакторе запросов отключен. Режим скриптов можно включить, нажав кнопку **Режим SQLCMD** на панели инструментов или выбрав пункт **Режим SQLCMD** в меню **Запрос** .  
  
> [!NOTE]  
>  При включении режима скриптов SQLCMD отключается функция IntelliSense и отладчик [!INCLUDE[tsql](../../includes/tsql-md.md)] в редакторе запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
 В скриптах SQLCMD в редакторе запросов можно использовать те же возможности, что и в любых других скриптах [!INCLUDE[tsql](../../includes/tsql-md.md)] . К таким средствам относятся:  
  
-   выделение цветом;  
  
-   выполнение скриптов;  
  
-   Система управления версиями  
  
-   синтаксический анализ скриптов;  
  
-   Showplan  
  
## <a name="enable-sqlcmd-scripting-in-query-editor"></a>Включение режима скриптов SQLCMD в редакторе запросов  
 Включить режим скриптов SQLCMD для активного окна редактора запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] можно при помощи следующей процедуры.  
  
#### <a name="to-switch-a-database-engine-query-editor-window-to-sqlcmd-mode"></a>Переключение окна редактора запросов компонента Database Engine в режим скриптов SQLCMD  
  
1.  В обозревателе объектов щелкните сервер правой кнопкой мыши и выберите команду **Создать запрос**, чтобы открыть новое окно редактора запросов [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
2.  В меню **Запрос** выберите команду **Режим SQLCMD**.  
  
     Редактор запросов выполняет инструкции **sqlcmd** в контексте редактора запросов.  
  
3.  На панели инструментов **Редактора SQL** в списке **Доступные базы данных** выберите пункт [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
4.  В окне редактора запросов введите две следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] и инструкцию `!!DIR` **sqlcmd**.  
  
    ```  
    SELECT DISTINCT Type FROM Sales.SpecialOffer;  
    GO  
    !!DIR  
    GO  
    SELECT ProductCategoryID, Name FROM Production.ProductCategory;  
    GO  
    ```  
  
5.  Нажмите клавишу F5, чтобы выполнить весь раздел, составленный из инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] и MS-DOS.  
  
     Обратите внимание на две панели с результатами выполнения первой и третьей инструкций SQL.  
  
6.  На панели **Результаты** перейдите на вкладку **Сообщения** , чтобы просмотреть сообщения всех трех инструкций.  
  
    -   (Обработано строк: 6)  
  
    -   \<The directory information>  
  
    -   (Обработано строк: 4)  
  
> [!IMPORTANT]  
>  При выполнении из командной строки служебная программа **sqlcmd** позволяет добиться полного взаимодействия с операционной системой. Используя редактор запросов в **Режиме SQLCMD**, будьте внимательны, чтобы не запустить интерактивные инструкции. Редактор запросов не может моментально ответить операционной системе.  
  
 Дополнительные сведения о выполнении инструкции SQLCMD см. в разделе [Служебная программа sqlcmd](../../tools/sqlcmd-utility.md)или изучите учебник по SQLCMD.  
  
## <a name="enable-sqlcmd-scripting-by-default"></a>Включение режима скриптов SQLCMD по умолчанию  
 Чтобы режим скриптов SQLCMD включался по умолчанию, в меню **Сервис** выберите пункт **Параметры**, раскройте узлы **Выполнение запроса**и **SQL Server**, перейдите на страницу **Общие** и установите флажок **Открывать новые запросы в режиме SQLCMD** .  
  
## <a name="writing-and-editing-sqlcmd-scripts"></a>Создание и изменение скриптов SQLCMD  
 После включения режима скриптов можно писать команды SQLCMD и инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] . Применяются следующие правила.  
  
-   команда SQLCMD должна быть первой инструкцией в строке;  
  
-   в каждой строке разрешается только одна команда SQLCMD;  
  
-   перед командами SQLCMD могут идти комментарии или пробелы;  
  
-   команды SQLCMD внутри символов комментария не выполняются;  
  
-   символами однострочных комментариев являются два дефиса (`--)` , они должны находиться в начале строки;  
  
-   перед командами операционной системы должны стоять два восклицательных знака (`!!`). Два восклицательных знака означают, что следующая за ними команда должна выполняться с помощью командного процессора `cmd.exe` . Текст, следующий после `!!` , передается как параметр в `cmd.exe`, поэтому полная командная строка будет иметь следующий вид: `"%SystemRoot%\system32\cmd.exe /c <text after !!>"`.  
  
-   чтобы четко различать команды SQLCMD и [!INCLUDE[tsql](../../includes/tsql-md.md)], ко всем командам SQLCMD необходимо добавлять префикс в виде двоеточия (`:`);  
  
-   Команда `GO` может использоваться без вводной части. Кроме того, ей может предшествовать `!!:`  
  
-   Редактор запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] поддерживает переменные среды и переменные, определенные в скрипте SQLCMD, однако не поддерживает встроенные переменные SQLCMD и **osql** . Обрабатываемый код SQLCMD среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] чувствителен к регистру переменных. Например, PRINT '$(COMPUTERNAME)' выдаст правильный результат, а PRINT '$(ComputerName)' приведет к ошибке.  
  
> [!CAUTION]
>  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] использует [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]SqlClient для выполнения в обычном режиме и в режиме SQLCMD. При вызове из командной строки SQLCMD использует поставщика OLE DB. Так как могут применяться различные параметры по умолчанию, выполнение одного и того же запроса в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в режиме SQLCMD и в программе SQLCMD может проходить по-разному.  
  
## <a name="supported-sqlcmd-syntax"></a>Поддерживаемый синтаксис SQLCMD  
 Редактор запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] поддерживает следующие ключевые слова сценариев SQLCMD:  
  
 `[!!:]GO[count]`  
  
 `!! <command>`  
  
 `:exit(statement)`  
  
 `:Quit`  
  
 `:r <filename>`  
  
 `:setvar <var> <value>`  
  
 `:connect server[\instance] [-l login_timeout] [-U user [-P password]]`  
  
 `:on error [ignore|exit]`  
  
 `:error <filename>|stderr|stdout`  
  
 `:out <filename>|stderr|stdout`  
  
> [!NOTE]  
>  Для `:error` и `:out`, `stderr` и `stdout` вывод направляется на вкладку сообщений.  
  
 Команды SQLCMD, не перечисленные выше, редактором запросов не поддерживаются. Если выполняется скрипт, содержащий неподдерживаемые ключевые слова SQLCMD, для каждого неподдерживаемого ключевого слова редактор запросов отправляет в целевой объект сообщение "Команда *\<ignored command*> не учитывается". Скрипт будет выполнен успешно, но неподдерживаемые команды не будут учитываться.  
  
> [!CAUTION]  
>  Так как команды SQLCMD запускаются не из командной строки, при запуске редактора запросов в режиме SQLCMD действуют некоторые ограничения. Нельзя передавать параметры командной строки, например переменные. Кроме того, поскольку редактор запросов не поддерживает возможности реагировать на приглашения операционной системы, не следует выполнять интерактивные инструкции.  
  
## <a name="color-coding-in-sqlcmd-scripts"></a>Выделение цветом в скриптах SQLCMD  
 В режиме скриптов SQLCMD программный код скрипта выделяется разными цветами. Выделение цветом ключевых слов [!INCLUDE[tsql](../../includes/tsql-md.md)] остается таким же. Команды SQLCMD представлены с затененным фоном.  
  
## <a name="example"></a>Пример  
 В следующем примере используется инструкция **sqlcmd** . Чтобы создать выходной файл с именем testoutput.txt, выполняются две инструкции SELECT [!INCLUDE[tsql](../../includes/tsql-md.md)] и одна команда операционной системы (вывод содержимого текущего каталога). Итоговый файл содержит информацию о результатах выполнения инструкции `DIR` , которая следует за результатами выполнения инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
```  
:out C:\testoutput.txt  
SELECT @@VERSION As 'Server Version'  
!!DIR  
!!:GO  
SELECT @@SERVERNAME AS 'Server Name'  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Программа sqlcmd](../../tools/sqlcmd-utility.md)  
  
  
