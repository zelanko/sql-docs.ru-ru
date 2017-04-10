---
title: "Масштабируемые группы PolyBase | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "05/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-polybase"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PolyBase"
  - "PolyBase, масштабируемые группы"
  - "масштабирование PolyBase"
ms.assetid: c7810135-4d63-4161-93ab-0e75e9d10ab5
caps.latest.revision: 20
author: "barbkess"
ms.author: "barbkess"
manager: "jhubbard"
caps.handback.revision: 19
---
# Масштабируемые группы PolyBase
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Обработка больших наборов данных в Hadoop или хранилище BLOB-объектов Azure автономным экземпляром SQL Server с PolyBase может сопровождаться снижением производительности. Группы PolyBase позволяют создавать кластеры экземпляров SQL Server для обработки больших наборов данных из внешних источников данных (например, Hadoop или хранилища BLOB-объектов Azure), используя возможности масштабирования. Это помогает повысить производительность запросов.  
  
 См. разделы [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md) и [Руководство по PolyBase](../../relational-databases/polybase/polybase-guide.md).  
  
 ![PolyBase scale-out groups](../../relational-databases/polybase/media/polybase-scale-out-groups.png "PolyBase scale-out groups")  
  
## Обзор  
  
### Головной узел  
 Головной узел содержит экземпляр SQL Server, на который отправляются запросы PolyBase. Каждая группа PolyBase может иметь только один головной узел. Головной узел — это логическая группа на экземпляре SQL Server, в которую входят ядро СУБД SQL, а также ядро PolyBase и служба перемещения данных PolyBase.  
  
### Вычислительный узел  
 Вычислительный узел содержит экземпляр SQL Server, который помогает выполнять масштабируемую обработку запросов к внешним данным. Вычислительный узел — это логическая группа на экземпляре SQL Server, в которую входят SQL Server и служба перемещения данных PolyBase. Группа PolyBase может включать несколько вычислительных узлов.  
  
### Распределенная обработка запросов  
 Запросы PolyBase отправляются на SQL Server на головном узле. Часть запроса, которая относится к внешним таблицам, передается в ядро PolyBase.  
  
 Ядро PolyBase — это ключевой компонент в процессе обработки запросов PolyBase. Оно анализирует запрос к внешним данным, создает план запроса и распределяет работу между службами перемещения данных на вычислительных узлах. После выполнения этой работы ядро PolyBase получает результаты от вычислительных узлов и отправляет их на SQL Server для финальной обработки и передачи клиенту.  
  
 Служба перемещения данных PolyBase получает инструкции от ядра PolyBase и передает данные между HDFS и SQL Server, а также между экземплярами SQL Server на головном и вычислительных узлах.  
  
### Доступность для разных выпусков  
 После установки SQL Server экземпляр можно назначить как головным, так и вычислительным узлом.  Выбор зависит от того, на какой версии SQL Server работает PolyBase. Экземпляр с установленным выпуском Enterprise Еdition можно назначить как головным, так и вычислительным узлом. Экземпляр с выпуском Standard Еdition можно назначить только вычислительным узлом.  
  
## Настройка группы PolyBase  
  
### Предварительные требования  
  
-   N компьютеров, размещенных в одном домене.  
  
-   Доменная учетная запись для запуска служб PolyBase.  
  
### Шаги  
  
1.  Установите SQL Server с PolyBase на все доступные компьютеры (N).  
  
2.  Выберите один экземпляр SQL Server в качестве головного узла. Головным узлом можно назначить только экземпляр с установленным SQL Server Enterprise.  
  
3.  Добавьте в группу остальные экземпляры SQL Server в качестве вычислительных узлов с помощью [sp_polybase_join_group](../Topic/sp_polybase_join_group.md).  
  
4.  Для мониторинга узлов группы используйте инструкцию [sys.dm_exec_compute_nodes (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).  
  
5.  Необязательно. Для удаления вычислительных узлов используйте инструкцию [sp_polybase_leave_group (Transact-SQL)](../Topic/sp_polybase_leave_group%20\(Transact-SQL\).md).  
  
## Пошаговое руководство с примерами  
 В этом руководстве мы настроим группу PolyBase, используя следующие ресурсы.  
  
1.  Два компьютера в домене *PQTH4A* со следующими именами:  
  
    -   PQTH4A-CMP01  
  
    -   PQTH4A-CMP02  
  
2.  Учетная запись домена: *PQTH4A\PolybaseUser*  
  
#### Шаг 1. Установка SQL Server с PolyBase на всех компьютерах  
  
1.  Запустите Setup.exe.  
  
2.  На странице выбора компонентов выберите пункт **Служба запросов PolyBase для внешних данных**.  
  
3.  На странице "Конфигурация сервера" настройте ядро SQL Server PolyBase и службы перемещения данных SQL Server PolyBase для запуска под **доменной учетной записью** PQTH4A\PolybaseUser.  
  
4.  На странице настройки PolyBase включите параметр **Использовать экземпляр SQL Server как часть масштабируемой группы PolyBase**. Это позволит открыть брандмауэр для входящих подключений к службе PolyBase.  
  
5.  После завершения настройки запустите **services.msc**. Убедитесь, что запущены SQL Server, ядро PolyBase и служба перемещения данных PolyBase.  
  
     ![PolyBase services](../../relational-databases/polybase/media/polybase-services.png "PolyBase services")  
  
#### Шаг 2. Выбор одного сервера SQL Server в качестве головного узла  
  
-   По завершении установки любой из компьютеров может выполнять роль головного узла группы PolyBase. В нашем примере мы выберем в качестве головного узла MSSQLSERVER на узле PQTH4A-CMP01.  
  
#### Шаг 3. Добавление в группу остальных экземпляров SQL Server в качестве вычислительных узлов  
  
1.  Подключитесь к SQL Server на узле PQTH4A-CMP02.  
  
2.  Запустите хранимую процедуру [sp_polybase_leave_group](../Topic/sp_polybase_join_group.md).  
  
    ```  
    -- Enter head node details:   
    -- head node machine name, head node dms control channel port, head node sql server name  
    EXEC sp_polybase_join_group 'PQTH4A-CMP01', 16450, 'MSSQLSERVER';  
  
    ```  
  
3.  Запустите файл services.msc на вычислительном узле (PQTH4A-CMP02).  
  
4.  Завершите работу ядра PolyBase и перезапустите службу перемещения данных PolyBase.  
  
#### Необязательное действие: удаление вычислительного узла  
  
1.  Подключитесь к вычислительному узлу SQL Server (PQTH4A-CMP02).  
  
2.  Запустите хранимую процедуру sp_polybase_leave_group.  
  
    ```  
    EXEC sp_polybase_leave_group;  
    ```  
  
3.  Запустите файл services.msc на вычислительном узле, который хотите удалить (PQTH4A-CMP02).  
  
4.  Запустите ядро PolyBase. Перезапустите службу перемещения данных PolyBase.  
  
5.  Убедитесь, что узел удален, запустив на узле PQTH4A-CMP01 динамическое административное представление sys.dm_exec_compute_nodes. Теперь узел PQTH4A-CMP02 будет функционировать как автономный головной узел.  
  
## Следующие шаги  
 Дополнительные сведения об устранении неполадок см. в статье [PolyBase troubleshooting with dynamic management views](../Topic/PolyBase%20troubleshooting%20with%20dynamic%20management%20views.md).  
  
## См. также:  
 [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)   
 [Руководство по PolyBase](../../relational-databases/polybase/polybase-guide.md)   
 [Конфигурация PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)  
  
  