---
title: Советы и рекомендации по использованию SQL Server Management Studio (SSMS)
description: Из этой статьи вы узнаете, как вставлять комментарии в код и удалять их из него, использовать отступы для текста, фильтровать объекты в обозревателе объектов, получать доступ к журналу ошибок SQL Server, а также находить имя экземпляра SQL Server с помощью SQL Server Management Studio.
ms.topic: tutorial
ms.prod: sql
ms.technology: ssms
ms.prod_service: sql-tools
author: MashaMSFT
ms.author: mathoma
ms.reviewer: sstein
helpviewer_keywords:
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- SQL Server Management Studio [SQL Server], tutorials
- Find SQL Server Instance
- find instance name
- find sql server instance name
ms.custom: ''
ms.date: 03/13/2018
ms.openlocfilehash: d5b52a35bce720e3985a8191335491c50e43c50e
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267582"
---
# <a name="tips-and-tricks-for-using-sql-server-management-studio-ssms"></a>Советы и рекомендации по использованию SQL Server Management Studio (SSMS)

В этой статье приводятся некоторые советы и рекомендации по использованию SQL Server Management Studio (SSMS). В этой статье показано, как выполнить следующие действия: 

> [!div class="checklist"]
> * Комментирование и раскомментирование текста на языке Transact-SQL (T-SQL)
> * Задание отступов в тексте
> * Фильтрация объектов в обозревателе объектов
> * Доступ к журналу ошибок SQL Server
> * Определение имени экземпляра SQL Server

## <a name="prerequisites"></a>предварительные требования

Чтобы выполнить шаги, приведенные в этой статье, требуются среда SQL Server Management Studio, доступ к SQL Server и база данных AdventureWorks. 

* Установите [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
* Установите выпуск [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
* Скачайте [пример базы данных AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Инструкции по восстановлению базы данных в среде SSMS см. в разделе [Восстановление базы данных](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 

## <a name="commentuncomment-your-t-sql-code"></a>Комментирование и раскомментирование кода T-SQL

Части текста можно закомментировать и раскомментировать с помощью кнопки **Закомментировать** на панели инструментов. Закомментированный текст не выполняется.

1. Откройте среду SQL Server Management Studio.

2. Подключитесь к серверу SQL Server.

3. Откройте окно "Новый запрос".

4. Вставьте следующий код T-SQL в текстовое окно.

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

    > [!NOTE]
    > Текст можно комментировать с помощью сочетания клавиш **CTRL+K, CTRL+C**.

8. Выделите часть текста с инструкцией **Alter Database** и нажмите кнопку **Раскомментировать** на панели инструментов:

    ![Кнопка "Раскомментировать"](media/ssms-tricks/uncomment.png)

    > [!NOTE]
    > Чтобы раскомментировать текст, используйте сочетания клавиш **CTRL+K, CTRL+U**.

9. Нажмите кнопку **Выполнить**, чтобы выполнить раскомментированную часть текста.

## <a name="indent-your-text"></a>Задание отступов в тексте

Кнопки отступов на панели инструментов позволяют увеличивать и уменьшать отступы в тексте.

1. Откройте окно "Новый запрос".

2. Вставьте в окно следующий фрагмент кода T-SQL:

    ```sql
    USE master
      GO

      --Drop the database if it already exists
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

В базах данных, в которых имеется множество объектов, можно использовать фильтрацию для поиска конкретных таблиц, представлений и т. д. В этом разделе описано, как фильтровать таблицы, но эти же действия можно выполнять в любом другом узле обозревателя объектов:

1. Подключитесь к серверу SQL Server.

2. Разверните узел **Базы данных** > **AdventureWorks** > **Таблицы**. Будут показаны все таблицы в базе данных.

3. Щелкните **Таблицы** правой кнопкой мыши, а затем выберите **Фильтр** > **Параметры фильтра**:

    ![Настройки фильтра](media/ssms-tricks/filtersettings.png)

4. В окне **Параметры фильтра** можно изменить некоторые из указанных ниже параметров фильтра:
    * Фильтровать по имени: 

      ![Фильтрация по имени](media/ssms-tricks/filterbyname.png)

    * Фильтровать по схеме: 

      ![Фильтрация по схеме](media/ssms-tricks/filterbyschema.png)

5. Чтобы сбросить фильтр, щелкните правой кнопкой мыши узел **Таблицы** и выберите **Удалить фильтр**.

    ![Удаление фильтра](media/ssms-tricks/removefilter.png)

## <a name="access-your-sql-server-error-log"></a>Доступ к журналу ошибок SQL Server

Журнал ошибок — это файл, который содержит подробные сведения о том, что происходит на вашем экземпляре SQL Server. В среде SSMS можно просмотреть журнал ошибок и выполнить запросы к нему. Журнал ошибок представляет собой LOG-файл, расположенный на вашем диске.

### <a name="open-the-error-log-in-ssms"></a>Открытие журнала ошибок в SSMS

1. Подключитесь к серверу SQL Server.  

2. Разверните узел **Управление** > **Журналы SQL Server**. 

3. Щелкните правой кнопкой мыши **Текущий** журнал ошибок и выберите пункт **Просмотр журнала SQL Server**:

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

Путь к журналу ошибок SQL Server зависит от параметров конфигурации. Путь к расположению журнала ошибок можно найти в параметрах запуска в диспетчере конфигурации SQL Server. Найдите параметр запуска, указывающий расположение журнала ошибок SQL Server, выполнив следующие действия. *Ваш путь может отличаться от указанного ниже*.

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

1. Выполните инструкции по поиску [журнала ошибок SQL Server на диске](#find-the-error-log-location-if-you-cant-connect-to-sql-server). Ваш путь может отличаться от указанного на рисунке ниже.

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
    * В меню **Вид** выберите **Окно "Свойства"** :

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

## <a name="next-steps"></a>Следующие шаги

Лучший способ познакомиться с SSMS — это поработать в среде самостоятельно. Эти *руководства* и *статьи* помогут вам ознакомиться с различными функциями SSMS.  С их помощью вы научитесь работать с компонентами SSMS и легко находить регулярно используемые функции.

* [Подключение к экземпляру и отправка запросов к нему](connect-query-sql-server.md)
* [Создание скриптов](scripting-ssms.md)
* [Использование шаблонов в SSMS](../template/templates-ssms.md)
* [Конфигурация SSMS](ssms-configuration.md)
