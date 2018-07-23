---
Title: 'Tutorial: Additional tips and tricks for using SQL Server Management Studio'
description: 'Учебник, в котором приводятся некоторые дополнительные советы и рекомендации по использованию SSMS. '
keywords: SQL Server, SSMS, SQL Server Management Studio
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: Tutorial
ms.suite: sql
ms.prod: sql
ms.technology: ssms
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
helpviewer_keywords:
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- SQL Server Management Studio [SQL Server], tutorials
- Find SQL Server Instance
- find instance name
- find sql server instance name
ms.openlocfilehash: ef7bbf9b60cb29bee0285d8974a9b97cbe99a3c2
ms.sourcegitcommit: 0dff9dd43e80eee900eb92d25df9ca18397f3485
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37080102"
---
# <a name="tutorial-additional-tips-and-tricks-for-using-ssms"></a>Учебник: дополнительные советы и рекомендации по использованию SSMS
В этом учебнике приводятся некоторые дополнительные советы по использованию SQL Server Management Studio (SSMS). В этой статье показано, как выполнить следующие действия: 

> [!div class="checklist"]
> * Комментирование и раскомментирование текста на языке Transact-SQL (T-SQL)
> * Задание отступов в тексте
> * Фильтрация объектов в обозревателе объектов
> * Доступ к журналу ошибок SQL Server
> * Определение имени экземпляра SQL Server

## <a name="prerequisites"></a>предварительные требования
Для работы с этим учебником требуется среда SQL Server Management Studio, доступ к SQL Server и база данных AdventureWorks. 

- Установите [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Скачайте [пример базы данных AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Инструкции по восстановлению базы данных в среде SSMS см. в разделе [Восстановление базы данных](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 


## <a name="commentuncomment-your-t-sql-code"></a>Комментирование и раскомментирование кода T-SQL
Части текста можно закомментировать и раскомментировать с помощью кнопки **Закомментировать** на панели инструментов. Закомментированный текст не выполняется. 

1. Откройте среду SQL Server Management Studio. 
2. Подключитесь к серверу SQL Server.
3. Откройте окно "Новый запрос". 
4. Вставьте в окно следующий фрагмент кода T-SQL: 

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


5. Выделите часть текста с инструкцией **Alter Database** и нажмите кнопку **Закомментировать** на панели инструментов: 

    ![Кнопка "Закомментировать"](media/ssms-tricks/comment.png)
6. Нажмите кнопку **Выполнить**, чтобы выполнить раскомментированную часть текста. 
7. Выделите все, за исключением **инструкции Alter Database**, а затем нажмите кнопку **Закомментировать**:

    ![Комментирование всего текста](media/ssms-tricks/commenteverything.png)

8. Выделите часть текста с инструкцией **Alter Database** и нажмите кнопку **Раскомментировать** на панели инструментов:

    ![Кнопка "Раскомментировать"](media/ssms-tricks/uncomment.png)
    
9. Нажмите кнопку **Выполнить**, чтобы выполнить раскомментированную часть текста. 

## <a name="indent-your-text"></a>Задание отступов в тексте
Кнопки отступов на панели инструментов позволяют увеличивать и уменьшать отступы в тексте. 

1. Откройте окно "Новый запрос". 
2. Вставьте в окно следующий фрагмент кода T-SQL: 

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
 
3. Выделите часть текста с инструкцией **Alter Database** и нажмите кнопку **Увеличить отступ** на панели инструментов, чтобы сдвинуть текст вправо:

    ![Увеличение отступа](media/ssms-tricks/increaseindent.png)

4. Снова выделите часть текста с инструкцией **Alter Database** и нажмите кнопку **Уменьшить отступ** на панели инструментов, чтобы сдвинуть текст влево.

    ![Уменьшение отступа](media/ssms-tricks/decreaseindent.png)


## <a name="filter-objects-in-object-explorer"></a>Фильтрация объектов в обозревателе объектов
Чтобы упростить поиск объектов в базах данных, содержащих много объектов, можно воспользоваться фильтрацией. В этом разделе описано, как фильтровать таблицы, но эти же действия можно выполнять в любом другом узле обозревателя объектов:

1. Подключитесь к серверу SQL Server.
2. Разверните узел **Базы данных** > **AdventureWorks** > **Таблицы**. Будут показаны все таблицы в базе данных.
5. Щелкните **Таблицы** правой кнопкой мыши, а затем выберите **Фильтр** > **Параметры фильтра**:

    ![Настройки фильтра](media/ssms-tricks/filtersettings.png)

6. В окне **Параметры фильтра** можно изменить некоторые из указанных ниже параметров фильтра:
    - Фильтровать по имени: 
   
      ![Фильтрация по имени](media/ssms-tricks/filterbyname.png)

    - Фильтровать по схеме: 
    
      ![Фильтрация по схеме](media/ssms-tricks/filterbyschema.png)

7. Чтобы сбросить фильтр, щелкните правой кнопкой мыши узел **Таблицы** и выберите **Удалить фильтр**.

    ![Удаление фильтра](media/ssms-tricks/removefilter.png)
    


## <a name="access-your-sql-server-error-log"></a>Доступ к журналу ошибок SQL Server
Журнал ошибок — это файл, который содержит подробные сведения о том, что происходит на вашем экземпляре SQL Server. В среде SSMS можно просмотреть журнал ошибок и выполнить запросы к нему. Журнал ошибок представляет собой LOG-файл, расположенный на вашем диске.

### <a name="open-the-error-log-in-ssms"></a>Открытие журнала ошибок в SSMS
1. Подключитесь к серверу SQL Server.  
2. Разверните узел **Управление** > **Журналы SQL Server**. 
4. Щелкните правой кнопкой мыши **Текущий** журнал ошибок и выберите пункт **Просмотр журнала SQL Server**:

    ![Просмотр журнала ошибок в SSMS](media/ssms-tricks/viewerrorloginssms.png)

### <a name="query-the-error-log-in-ssms"></a>Выполнение запросов к журналу ошибок в SSMS
1. Подключитесь к серверу SQL Server.
2. Откройте окно "Новый запрос".
3. Вставьте в окно запросов следующий фрагмент кода T-SQL:

 ```sql
   sp_readerrorlog 0,1,'Server process ID' 
  ``` 

4. Измените текст в одинарных кавычках на нужный.
5. Выполните запрос и просмотрите результаты:
   
    ![Выполнение запросов к журналу ошибок](media/ssms-tricks/queryerrorlog.png)


### <a name="find-the-error-log-location-if-youre-connected-to-sql-server"></a>Определение расположения журнала ошибок при наличии подключения к SQL Server
1. Подключитесь к серверу SQL Server.
2. Откройте окно "Новый запрос".
3. Вставьте следующий фрагмент кода T-SQL в окно запросов и нажмите кнопку **Выполнить**:

 ```sql
    SELECT SERVERPROPERTY('ErrorLogFileName') AS 'Error log file location'  
  ``` 

4. В результатах показано расположение журнала ошибок в файловой системе: 

    ![Поиск журнала ошибок с помощью запроса](media/ssms-tricks/finderrorlogquery.png)

### <a name="find-the-error-log-location-if-you-cant-connect-to-sql-server"></a>Определение расположения журнала ошибок при отсутствии подключения к SQL Server
1. Откройте диспетчер конфигурации SQL Server. 
2. Разверните узел **Службы**.
3. Щелкните правой кнопкой мыши свой экземпляр SQL Server и выберите **Свойства**:

    ![Свойства сервера Configuration Manager](media/ssms-tricks/serverproperties.PNG)

4. Выберите вкладку **Параметры запуска**.
5. Путь, указанный параметра после "-e" в разделе **Существующие параметры**, представляет собой расположение журнала ошибок: 
    
    ![Журнал ошибок](media/ssms-tricks/errorlog.png)
    
    В этом расположении есть несколько файлов с именем errorlog.*. Файл, имя которого заканчивается на *.log, представляет собой текущий файл журнала ошибок. Файлы, имена которых заканчиваются цифрами, — предыдущие файлы журнала. Каждый раз при перезагрузке сервера SQL Server создается новый файл журнала.

6. Откройте файл errorlog.log в Блокноте. 

## <a name="determine-sql-server-name"></a>Поиск имени экземпляра SQL Server
Определить имя сервера SQL Server до и после подключения к SQL Server можно различными способами.  

### <a name="before-you-connect-to-sql-server"></a>До подключения к SQL Server
1. Выполните инструкции по поиску [журнала ошибок SQL Server на диске](#finding-your-error-log-if-you-cannot-connect-to-sql). 
2. Откройте файл errorlog.log в Блокноте.  
3. Найдите текст *Server name is*.
    
    В одинарных кавычках указано имя экземпляра SQL Server, к которому вы будете подключаться:

    ![Поиск имени сервера в журнале ошибок](media/ssms-tricks/servernameinlog.png)
    
    Имя сервера имеет формат HOSTNAME\INSTANCENAME (имя сервера\имя экземпляра). Если оно включает только имя узла, это значит, что вы задали экземпляр по умолчанию. Имя экземпляра: MSSQLSERVER. При подключении к экземпляру SQL Server по умолчанию нужно указывать только имя узла.  

### <a name="when-youre-connected-to-sql-server"></a>После подключения к SQL Server 
При наличии подключения к SQL Server имя сервера можно найти в трех местах: 

1. Имя сервера указано в обозревателе объектов:

    ![Имя экземпляра SQL Server в обозревателе объектов](media/ssms-tricks/nameinobjectexplorer.png)
2. Имя сервера указано в окне запросов:

    ![Имя экземпляра SQL Server в окне запросов](media/ssms-tricks/nameinquerywindow.png)
3. Имя сервера указано в разделе **Свойства**.
    - В меню **Вид** выберите **Окно "Свойства"**:

      ![Имя экземпляра SQL Server в окне "Свойства"](media/ssms-tricks/nameinproperties.png)

### <a name="if-youre-connected-to-an-alias-or-availability-group-listener"></a>При подключении к псевдониму или прослушивателю группы доступности 
Если вы подключились к псевдониму или прослушивателю группы доступности, то в обозревателе объектов и окне "Свойства" будут указаны сведения о них. В этом случае имя сервера SQL Server может быть недоступно напрямую, и его необходимо запросить: 

1. Подключитесь к серверу SQL Server.
2. Откройте окно "Новый запрос".
3. Вставьте в окно следующий фрагмент кода T-SQL: 

  ```sql
   select @@Servername 
 ``` 
4. Просмотрите результаты запроса, чтобы определить имя сервера SQL Server, к которому вы подключены: 
    
    ![Определение имени сервера SQL Server с помощью запроса](media/ssms-tricks/queryservername.png)


