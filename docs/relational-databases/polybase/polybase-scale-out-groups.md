---
title: "Масштабируемые группы PolyBase | Документация Майкрософт"
ms.custom: 
ms.date: 05/24/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: polybase
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine-polybase
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PolyBase
- PolyBase, scale-out groups
- scale-out PolyBase
ms.assetid: c7810135-4d63-4161-93ab-0e75e9d10ab5
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 018d765aace9ef2f46a1dd8da4e0a6c503a0d35f
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2018
---
# <a name="polybase-scale-out-groups"></a>Масштабируемые группы PolyBase
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Обработка больших наборов данных в Hadoop или хранилище BLOB-объектов Azure автономным экземпляром SQL Server с PolyBase может сопровождаться снижением производительности. Группы PolyBase позволяют создавать кластеры экземпляров SQL Server для обработки больших наборов данных из внешних источников данных (например, Hadoop или хранилища BLOB-объектов Azure), используя возможности масштабирования. Это помогает повысить производительность запросов.  
  
 См. разделы [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md) и [Руководство по PolyBase](../../relational-databases/polybase/polybase-guide.md).  
  
 ![Масштабируемые группы PolyBase](../../relational-databases/polybase/media/polybase-scale-out-groups.png "Масштабируемые группы PolyBase")  
  
## <a name="overview"></a>Обзор  
  
### <a name="head-node"></a>Головной узел  
 Головной узел содержит экземпляр SQL Server, на который отправляются запросы PolyBase. Каждая группа PolyBase может иметь только один головной узел. Головной узел — это логическая группа на экземпляре SQL Server, в которую входят ядро СУБД SQL, а также ядро PolyBase и служба перемещения данных PolyBase.  
  
### <a name="compute-node"></a>Вычислительный узел  
 Вычислительный узел содержит экземпляр SQL Server, который помогает выполнять масштабируемую обработку запросов к внешним данным. Вычислительный узел — это логическая группа на экземпляре SQL Server, в которую входят SQL Server и служба перемещения данных PolyBase. Группа PolyBase может включать несколько вычислительных узлов.  В головном узле и вычислительных узлах должна использоваться одна и та же версия SQL Server.
  
### <a name="distributed-query-processing"></a>Распределенная обработка запросов  
 Запросы PolyBase отправляются на SQL Server на головном узле. Часть запроса, которая относится к внешним таблицам, передается в ядро PolyBase.  
  
 Ядро PolyBase — это ключевой компонент в процессе обработки запросов PolyBase. Оно анализирует запрос к внешним данным, создает план запроса и распределяет работу между службами перемещения данных на вычислительных узлах. После выполнения этой работы ядро PolyBase получает результаты от вычислительных узлов и отправляет их на SQL Server для финальной обработки и передачи клиенту.  
  
 Служба перемещения данных PolyBase получает инструкции от ядра PolyBase и передает данные между HDFS и SQL Server, а также между экземплярами SQL Server на головном и вычислительных узлах.  
  
### <a name="editions-availability"></a>Доступность для разных выпусков  
 После установки SQL Server экземпляр можно назначить как головным, так и вычислительным узлом.  Выбор зависит от того, на какой версии SQL Server работает PolyBase. Экземпляр с установленным выпуском Enterprise Еdition можно назначить как головным, так и вычислительным узлом. Экземпляр с выпуском Standard Еdition можно назначить только вычислительным узлом.  
  
## <a name="to-configure-a-polybase-group"></a>Настройка группы PolyBase  
  
### <a name="prerequisites"></a>предварительные требования  
  
-   N компьютеров, размещенных в одном домене.  
  
-   Доменная учетная запись для запуска служб PolyBase.  
  
### <a name="steps"></a>Шаги  
  
1.  Установите одну и ту же версию SQL Server с PolyBase на все доступные компьютеры (N).  
  
2.  Выберите один экземпляр SQL Server в качестве головного узла. Головным узлом можно назначить только экземпляр с установленным SQL Server Enterprise.  
  
3.  Добавьте в группу остальные экземпляры SQL Server в качестве вычислительных узлов с помощью [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md).  
  
4.  Для мониторинга узлов группы используйте инструкцию [sys.dm_exec_compute_nodes (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).  
  
5.  Необязательный параметр. Для удаления вычислительных узлов используйте инструкцию [sp_polybase_leave_group (Transact-SQL)](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-leave-group.md).  
  
## <a name="example-walk-through"></a>Пошаговое руководство с примерами  
 В этом руководстве мы настроим группу PolyBase, используя следующие ресурсы.  
  
1.  Два компьютера в домене *PQTH4A* со следующими именами:  
  
    -   PQTH4A-CMP01  
  
    -   PQTH4A-CMP02  
  
2.  Учетная запись домена: *PQTH4A\PolybaseUser*  
  
#### <a name="step-1-install-sql-server-with-polybase-on-all-machines"></a>Шаг 1. Установка SQL Server с PolyBase на всех компьютерах  
  
1.  Запустите Setup.exe.  
  
2.  На странице выбора компонентов выберите пункт **Служба запросов PolyBase для внешних данных**.  
  
3.  На странице "Конфигурация сервера" настройте ядро SQL Server PolyBase и службы перемещения данных SQL Server PolyBase для запуска под **доменной учетной записью** PQTH4A\PolybaseUser.  
  
4.  На странице настройки PolyBase включите параметр **Использовать экземпляр SQL Server как часть масштабируемой группы PolyBase**. Это позволит открыть брандмауэр для входящих подключений к службе PolyBase.  
  
5.  После завершения настройки запустите **services.msc**. Убедитесь, что запущены SQL Server, ядро PolyBase и служба перемещения данных PolyBase.  
  
     ![Службы PolyBase](../../relational-databases/polybase/media/polybase-services.png "Службы PolyBase")  
  
#### <a name="step-2-select-one-sql-server-as-head-node"></a>Шаг 2. Выбор одного сервера SQL Server в качестве головного узла  
  
-   По завершении установки любой из компьютеров может выполнять роль головного узла группы PolyBase. В нашем примере мы выберем в качестве головного узла MSSQLSERVER на узле PQTH4A-CMP01.  
  
#### <a name="step-3-add-other-sql-server-instances-as-compute-nodes"></a>Шаг 3. Добавление в группу остальных экземпляров SQL Server в качестве вычислительных узлов  
  
1.  Подключитесь к SQL Server на узле PQTH4A-CMP02.  
  
2.  Запустите хранимую процедуру [sp_polybase_leave_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md).  
  
    ```  
    -- Enter head node details:   
    -- head node machine name, head node dms control channel port, head node sql server name  
    EXEC sp_polybase_join_group 'PQTH4A-CMP01', 16450, 'MSSQLSERVER';  
  
    ```  
  
3.  Запустите файл services.msc на вычислительном узле (PQTH4A-CMP02).  
  
4.  Завершите работу ядра PolyBase и перезапустите службу перемещения данных PolyBase.  
  
#### <a name="optional-remove-a-compute-node"></a>Необязательное действие: удаление вычислительного узла  
  
1.  Подключитесь к вычислительному узлу SQL Server (PQTH4A-CMP02).  
  
2.  Запустите хранимую процедуру sp_polybase_leave_group.  
  
    ```  
    EXEC sp_polybase_leave_group;  
    ```  
  
3.  Запустите файл services.msc на вычислительном узле, который хотите удалить (PQTH4A-CMP02).  
  
4.  Запустите ядро PolyBase. Перезапустите службу перемещения данных PolyBase.  
  
5.  Убедитесь, что узел удален, запустив на узле PQTH4A-CMP01 динамическое административное представление sys.dm_exec_compute_nodes. Теперь узел PQTH4A-CMP02 будет функционировать как автономный головной узел.  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения об устранении неполадок см. в статье [PolyBase troubleshooting with dynamic management views](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80).  
  
## <a name="see-also"></a>См. также:  
 [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)   
 [Руководство по PolyBase](../../relational-databases/polybase/polybase-guide.md)   
 [Конфигурация PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)  
  
  
