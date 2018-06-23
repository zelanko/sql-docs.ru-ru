---
title: 'Урок 6: Перенос базы данных из источника локального компьютера на целевой компьютер в Windows Azure | Документы Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9134ade-7b03-4c5c-8ed3-3bc369a61691
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2f6f0ac359d5358994c0a3a5367c676ca2f83969
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190985"
---
# <a name="lesson-6-migrate-a-database-from-a-source-machine-on-premises-to-a-destination-machine-in-windows-azure"></a>Урок 6: Перенос базы данных из источника локального компьютера на целевой компьютер в Windows Azure
  Для этого занятия предполагается, что у вас уже есть другой экземпляр SQL Server, который может находиться на другом локальном компьютере или на виртуальной машине Windows Azure. Сведения о создании виртуальной машины с SQL Server в Windows Azure см. в разделе [подготовки виртуальной машины SQL Server в Windows Azure](http://www.windowsazure.com/manage/windows/common-tasks/install-sql-server/). После провизионирования виртуальной машины SQL Server в Windows Azure необходимо подключиться к экземпляру SQL Server на этой виртуальной машине с помощью среды SQL Server Management Studio, работающей на другом компьютере.  
  
 Для этого занятия также предполагается, что вы уже выполнили следующие шаги.  
  
-   Получили учетную запись хранения Windows Azure.  
  
-   Создали контейнер с использованием вашей учетной записи хранения Windows Azure.  
  
-   Создали политику в контейнере с правами на чтение, запись и перечисление. Создали ключ SAS.  
  
-   Создали учетные данные SQL Server на исходном компьютере.  
  
-   Создали целевую виртуальную машину SQL Server в Windows Azure. Рекомендуется создать ее, выбрав образ платформы, содержащий SQL Server 2014.  
  
 Чтобы перенести базу данных с локального SQL Server на другую виртуальную машину в Windows Azure, можно выполнить следующие действия.  
  
1.  На исходном компьютере (в этом учебнике это локальный компьютер) откройте окно запросов среды SQL Server Management Studio. Отсоедините базу данных, чтобы переместить ее на другой компьютер, выполнив следующие инструкции:  
  
    ```  
    -- Detach the database in the source machine   
    USE master  
    EXEC sp_detach_db 'TestDB1', 'true';  
    ```  
  
2.  Если требуется перенести базу данных на целевой компьютер, сначала его необходимо подготовить. Для этого необходимо создать на целевом компьютере учетные данные SQL Server. Если это зашифрованная база данных, необходимо также импортировать сертификат с исходного компьютера на целевой.  
  
    1.  Для создания учетных данных SQL Server на целевом компьютере выполните следующие действия.  
  
        1.  Подключитесь к целевому компьютеру с помощью среды SQL Server Management Studio, которая работает на исходном компьютере.  Или запустите среду SQL Server Management Studio непосредственно на целевом компьютере.  
  
        2.  На панели инструментов Стандартная выберите **новый запрос**.  
  
        3.  Скопируйте и вставьте следующий пример в окно запроса (при необходимости измените). В следующей инструкции создаются учетные данные SQL Server для хранения сертификата общего доступа контейнера хранилища.  
  
            ```tsql  
  
            USE master   
            GO   
            CREATE CREDENTIAL [http://teststorageaccnt.blob.core.windows.net/testcontainer]   
            WITH IDENTITY='SHARED ACCESS SIGNATURE',   
            SECRET = 'your SAS key'   
            GO  
  
            ```  
  
        4.  Чтобы увидеть все доступные учетные данные, можно выполнить следующую инструкцию в окне запроса:  
  
            ```tsql  
            SELECT * from sys.credentials   
            ```  
  
        5.  После установления соединения с целевым сервером откройте окно запроса и выполните команду:  
  
            ```tsql  
  
            -- Create a master key and a server certificate   
            USE master   
            GO   
            CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01'; -- You may use a different password.   
            GO   
            CREATE CERTIFICATE MySQLCert   
            FROM FILE = 'C:\certs\MySQLCert.CER'   
            WITH PRIVATE KEY   
            (   
            FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
            DECRYPTION BY PASSWORD = 'MySQLKey01'   
            );   
            GO  
  
            ```  
  
             После завершения этого шага сертификат шифрования, резервная копия которого была получена с исходного компьютера, будет импортирован на целевой компьютер. Далее можно присоединить файлы данных на целевом компьютере.  
  
    2.  Затем с помощью параметра FOR ATTACH создайте базу данных с файлами данных и журнала, указывающими на существующие файлы в хранилище Windows Azure. В окне запроса введите следующую инструкцию:  
  
        ```tsql  
  
        --Create a database on the destination server   
        CREATE DATABASE TestDB1onDest   
        ON   
        (NAME = TestDB1_data,   
            FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Data.mdf' )   
        LOG ON   
         (NAME = TestDB1_log,   
            FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Log.ldf')   
        FOR ATTACH   
        GO  
  
        ```  
  
    3.  В обозревателе объектов щелкните «Базы данных» и щелкните правой кнопкой «Обновить». Вы должны увидеть созданную базу данных TestDB1onDest.  
  
    4.  Затем в окне запроса выполните следующую инструкцию:  
  
        ```tsql  
  
        USE TestDB1onDest   
        SELECT * FROM Table1;   
        GO  
  
        ```  
  
         Должен быть приведен список всех данных, введенных на занятии 4.  
  
 Обратите внимание, что зашифрованная база данных была передана в другой вычислительный экземпляр без перемещения данных.  
  
 Чтобы создать базу данных с файлами данных и журнала, указывающими на существующие файлы, в хранилище Windows Azure с помощью пользовательского интерфейса SQL Server Management Studio, выполните следующие действия.  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента SQL Server Database Engine и разверните его.  
  
2.  Щелкните правой кнопкой мыши элемент **Базы данных**, а затем выберите пункт **Создать базу данных**. Затем щелкните правой кнопкой мыши TestDB1. Щелкните «Задачи» и выберите команду «Отсоединить». В диалоговом окне отсоединения установите флажок «Удалить соединения». Нажмите кнопку **ОК**.  
  
3.  Подключитесь к целевому компьютеру, на котором установлен SQL Server 2014 CTP2 или более поздняя версия. Чтобы подготовить целевой компьютер, на нем необходимо создать учетные данные SQL Server, которые указывают на тот же контейнер, размещенный в TestDB1. Если вы собираетесь повторно присоединить базу данных на том же компьютере, то нет необходимости создавать другие учетные данные.  
  
4.  В **обозревателя объектов**, щелкните правой кнопкой мыши **баз данных** и нажмите кнопку **присоединение**.  
  
5.  В **присоединение баз данных** диалоговое окно для указания базы данных для присоединения, щелкните **добавить**. В **расположение файлов базы данных** диалоговое окно:  
  
     Расположение файла базы данных, введите: `https://teststorageaccnt.blob.core.windows.net/testcontainer/`.  
  
     Введите имя файла: `TestDB1Data.mdf`.  
  
6.  Нажмите кнопку **ОК**.  
  
     ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-6-7.gif "SQL 14 CTP2")  
  
 **Следующее занятие:**  
  
 [Занятие 7. Перемещение файлов данных в хранилище Microsoft Azure](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)  
  
  