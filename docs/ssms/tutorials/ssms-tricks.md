---
Title: 'Tutorial: Additional Tips and Tricks for using SSMS'
description: 'Учебник, в котором приводятся некоторые дополнительные советы и рекомендации по использованию SSMS. '
keywords: SQL Server, SSMS, SQL Server Management Studio
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: Tutorial
ms.suite: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
helpviewer_keywords:
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- SQL Server Management Studio [SQL Server], tutorials
ms.openlocfilehash: 9f633a8d624fd31913dc2aeb6fde34ff30b7645d
ms.sourcegitcommit: ccb05cb5a4cccaf7ffa9e85a4684fa583bab914e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="tutorial-additional-tips-and-tricks-for-using-ssms"></a>Учебник: дополнительные советы и рекомендации по использованию SSMS
В этом учебнике приводятся некоторые дополнительные советы по использованию SQL Server Management Studio. В нем рассматриваются следующие задачи: 

> [!div class="checklist"]
> * Закомментирование и раскомментирование текста на языке Transact-SQL (T-SQL)
> * Задание отступов в тексте
> * Фильтрация объектов в обозревателе объектов
> * Доступ к журналу ошибок SQL Server
> * Поиск имени экземпляра SQL Server

## <a name="prerequisites"></a>предварительные требования
Для работы с этим учебником требуется среда SQL Server Management Studio, доступ к SQL Server и база данных AdventureWorks. 

- Установите [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).
- Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).
- Скачайте [образцы баз данных AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Инструкции по восстановлению баз данных в SSMS можно найти в статье [Восстановление базы данных](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 

## <a name="comment--uncomment-your-t-sql-code"></a>Закомментирование и раскомментирование кода T-SQL
Части текста можно закомментировать и раскомментировать с помощью кнопки комментария на панели инструментов. Закомментированный текст не выполняется. 

1. Откройте среду SQL Server Management Studio. 
2. Подключитесь к серверу SQL Server.
3. Откройте окно **Новый запрос**. 
4. Вставьте в текстовое окно следующий фрагмент кода T-SQL: 

  ```sql
    USE master
    GO

    -- Drop the database if it already exists
    IF  EXISTS (
        SELECT name 
            FROM sys.databases 
            WHERE name = N'TutorialDB'
            )

    DROP DATABASE TutorialDB
    GO

    CREATE DATABASE TutorialDB
    GO

    ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
    GO
 ``` 


5. Выделите часть текста с инструкцией **Alter Database** и нажмите на панели инструментов кнопку **комментария**: 

    ![Комментарий](media/ssms-tricks/comment.png)
6. Нажмите кнопку **Выполнить**, чтобы выполнить незакомментированную часть текста. 
7. Выделите весь текст, кроме команды **Alter Database**, и нажмите на панели инструментов кнопку **комментария**:

    ![Закомментирование всего текста](media/ssms-tricks/commenteverything.png)

8. Выделите часть текста с инструкцией **Alter Database** и нажмите кнопку **Раскомментировать**, чтобы раскомментировать ее:

    ![Раскомментирование](media/ssms-tricks/uncomment.png)
    
9. Нажмите кнопку **Выполнить**, чтобы выполнить незакомментированную часть текста. 

## <a name="indent-your-text"></a>Задание отступов в тексте
Кнопки отступов позволяют увеличивать и уменьшать отступы в тексте. 

1. Откройте окно **Новый запрос**. 
2. Вставьте в текстовое окно следующий фрагмент кода T-SQL: 

  ```sql
    USE master
    GO

    -- Drop the database if it already exists
    IF  EXISTS (
        SELECT name 
            FROM sys.databases 
            WHERE name = N'TutorialDB'
            )

    DROP DATABASE TutorialDB
    GO

    CREATE DATABASE TutorialDB
    GO

    ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
    GO
 ``` 
 
3. Выделите часть текста с инструкцией **Alter Database** и нажмите на панели инструментов кнопку **Увеличить отступ**, чтобы сдвинуть текст вправо.

    ![Увеличить отступ](media/ssms-tricks/increaseindent.png)

4. Снова выделите часть текста с инструкцией **Alter Database** и нажмите кнопку **Уменьшить отступ**, чтобы сдвинуть текст обратно. 
    ![Уменьшение отступа](media/ssms-tricks/decreaseindent.png)


## <a name="filter-objects-in-object-explorer"></a>Фильтрация объектов в обозревателе объектов
Если база данных содержит много объектов, найти определенный объект может быть непросто. Чтобы упростить эту задачу, можно фильтровать объекты. В этом разделе описывается, как фильтровать таблицы, но аналогичные действия можно использовать для любого другого узла в **обозревателе объектов**.

1. Подключитесь к серверу SQL Server.
2. Разверните узел **Базы данных**.
3. Разверните узел базы данных **AdventureWorks**. 
4. Разверните узел **Таблицы**. 
   - Здесь можно просмотреть все таблицы, имеющиеся в базе данных.
5. Щелкните правой кнопкой мыши узел **Таблицы** и выберите пункты **Фильтр** > **Параметры фильтра**:

    ![Настройки фильтра](media/ssms-tricks/filtersettings.png)

6. В окне "Параметры фильтра" можно изменить параметры фильтра. Вот несколько примеров:
    - Фильтрация по имени: ![Фильтрация по имени](media/ssms-tricks/filterbyname.png)
    - Фильтрация по схеме: ![Фильтрация по схеме](media/ssms-tricks/filterbyschema.png)

7. Чтобы сбросить фильтр, щелкните правой кнопкой мыши узел **Таблицы** > **Удалить фильтр**

    ![Удалить фильтр](media/ssms-tricks/removefilter.png)
    


## <a name="access-your-sql-server-error-log"></a>Доступ к журналу ошибок SQL Server
Журнал ошибок — это файл, который содержит подробные сведения о происходящем с SQL Server. С помощью SSMS можно просматривать его и выполнять к нему запросы. Его можно также можно найти на диске как файл LOG.

### <a name="find-your-error-log-if-you-cannot-connect-to-sql"></a>Поиск журнала ошибок в случае, если не удается подключиться к SQL
1. Откройте диспетчер конфигурации SQL Server. 
2. Разверните узел **Службы**.
3. Щелкните правой кнопкой мыши экземпляр SQL Server и выберите пункт **Свойства**.

    ![Свойства сервера в диспетчере конфигурации](media/ssms-tricks/serverproperties.PNG)

4. Выберите вкладку **Параметры запуска**.
5. В области **Существующие параметры** путь после "-e" — это расположение журнала ошибок: 
    
    ![Журнал ошибок](media/ssms-tricks/errorlog.png)
    - В этом расположении имеется несколько файлов errorlog.*. Текущий журнал — это файл, имя которого заканчивается на *.log. Файлы, имена которых заканчиваются номерами, — это предыдущие журналы. Новый журнал создается при каждом перезапуске SQL Server. 
6. Откройте этот файл в Блокноте. 

### <a name="find-your-error-log-if-youre-connected-to-sql"></a>Поиск журнала ошибок при наличии подключения к SQL
1. Подключитесь к серверу SQL Server.
2. Откройте окно **Новый запрос**.
3. Вставьте в окно запроса следующий фрагмент кода T-SQL и нажмите кнопку **Выполнить**:


  ```sql
   SELECT SERVERPROPERTY('ErrorLogFileName') AS 'Error log file location' 
  ```
3. В результатах показано расположение журнала ошибок в файловой системе: 

![Поиск журнала ошибок с помощью запроса](media/ssms-tricks/finderrorlogquery.png)

### <a name="open-error-log-within-ssms"></a>Откройте журнал ошибок в SSMS.
1. Подключитесь к серверу SQL Server.
2. Разверните узел **Управление** . 
3. Разверните узел **Журналы SQL Server**. 
4. Щелкните правой кнопкой мыши **текущий** журнал ошибок и выберите пункт **Просмотр журнала SQL Server**:

    ![Просмотр журнала ошибок в SSMS](media/ssms-tricks/viewerrorloginssms.png)

### <a name="query-error-log-within-ssms"></a>Запрос журнала ошибок в SSMS
1. Подключитесь к серверу SQL Server.
2. Откройте окно **Новый запрос**.
3. Вставьте в окно запроса следующий фрагмент кода T-SQL:

 ```sql
   sp_readerrorlog 0,1,'Server process ID' 
  ``` 
4. Измените текст в одинарных кавычках на нужный.
5. Выполните запрос и просмотрите результаты:
   
    ![Запрос журнала ошибок](media/ssms-tricks/queryerrorlog.png)

## <a name="determine-sql-server-instance-name"></a>Определение имени экземпляра SQL Server
Определить имя экземпляра до и после подключения к серверу SQL Server можно несколькими способами.  

### <a name="when-you-dont-know-it"></a>Если имя известно
1. Выполните инструкции по поиску [журнала ошибок SQL Server на диске](#finding-your-error-log-if-you-cannot-connect-to-sql). 
2. Откройте файл errorlog.log в Блокноте. 
3. Найдите в файле текст "Имя сервера".
  - В одинарных кавычках указано имя экземпляра, к которому вы будете подключаться: ![Имя сервера в журнале ошибок](media/ssms-tricks/servernameinlog.png)

### <a name="once-youre-connected-to-sql"></a>После подключения к SQL 
Узнать имя экземпляра, к которому выполнено подключение, можно в трех местах. 

1. Имя сервера приводится в **обозревателе объектов**.

    ![Имя экземпляра в обозревателе объектов](media/ssms-tricks/nameinobjectexplorer.png)
2. Имя сервера приводится в окне запроса.

    ![Имя в окне запроса](media/ssms-tricks/nameinquerywindow.png)
3. , и делает это по-другому. Имя сервера также приводится в **окне свойств**.
    - Чтобы открыть его, в меню **Вид** выберите пункт **Окно свойств**.

    ![Имя в окне свойств](media/ssms-tricks/nameinproperties.png)

### <a name="if-youre-connected-to-an-alias-or-availability-group-listener"></a>При подключении к псевдониму или прослушивателю группы доступности 
Если вы подключились к псевдониму или прослушивателю группы доступности, именно они будут указаны в **обозревателе объектов** и окне **Свойства**. В этом случае имя сервера SQL Server недоступно напрямую, и его необходимо запросить. 

1. Соединитесь с SQL Server.
2. Откройте окно **Новый запрос**.
3. Вставьте в окно следующий фрагмент кода T-SQL: 

  ```sql
   select @@Servername 
 ``` 
4. Просмотрите результаты запроса, чтобы определить имя сервера SQL Server, к которому установлено подключение: 
    
    ![Запрос имени сервера](media/ssms-tricks/queryservername.png)


