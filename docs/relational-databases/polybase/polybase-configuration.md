---
title: "Конфигурация PolyBase | Microsoft Docs"
ms.custom: ""
ms.date: "11/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80ff73c1-2861-438b-a13f-309155f3d6e1
caps.latest.revision: 17
author: "barbkess"
ms.author: "barbkess"
manager: "jhubbard"
caps.handback.revision: 12
---
# Конфигурация PolyBase
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  В этом разделе приведены процедуры для настройки PolyBase.  
  
## <a name="external-data-source-configuration"></a>Конфигурация внешнего источника данных  
 Обеспечьте подключение к внешнему источнику данных с помощью SQL Server. Тип подключения ощутимо влияет на ожидаемую производительность запроса. Например, в рамках 10-гигабитного соединения Ethernet ответ на запрос PolyBase приходит быстрее, чем в рамках 1-гигабитного соединения Ethernet.  
  
 Необходимо настроить SQL Server для подключения к вашей версии Hadoop или хранилищу BLOB-объектов Azure с помощью **sp_configure**. В PolyBase поддерживается два типа распределений: Hortonworks Data Platform (HDP) и Cloudera Distributed Hadoop (CDH).  Полный список поддерживаемых внешних источников данных см. в статье [Конфигурация PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).  
  
### <a name="run-spconfigure"></a>Выполнение процедуры sp_configure  
  
1.  Запустите хранимую процедуру sp_configure 'hadoop connectivity' и задайте соответствующее значение.  Значение см. в статье [Конфигурация подключения к PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md).  
  
    ```tsql  
    -- Values map to various external data sources.  
    -- Example: value 7 stands for Azure blob storage and Hortonworks HDP 2.3 on Linux.  
    sp_configure @configname = 'hadoop connectivity', @configvalue = 7;   
    GO   
  
    RECONFIGURE   
    GO   
    ```  
  
2.  Перезапустите SQL Server с помощью **services.msc**. При перезапуске SQL Server следующие службы также будут перезапущены:  
  
    -   Служба перемещения данных SQL Server PolyBase  
  
    -   Компонент SQL Server PolyBase Engine  
  
## <a name="pushdown-configuration"></a>Конфигурация Pushdown  
 Чтобы улучшить производительность при выполнении запроса, активируйте вычисление Pushdown для кластера Hadoop.  
  
1.  Найдите файл **yarn-site.xml** в каталоге установки SQL Server. Как правило, путь выглядит следующим образом:  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase\Hadoop\conf  
    ```  
  
2.  Найдите аналогичный файл на компьютере с Hadoop в каталоге конфигурации. Открыв его, найдите и скопируйте значение ключа конфигурации yarn.application.classpath.  
  
3.  На компьютере SQL Server в файле **yarn.site.xml** найдите свойство **yarn.application.classpath** . Вставьте значение, скопированное на компьютере с Hadoop, в качестве значения элемента.  
  
## <a name="kerberos-configuration"></a>Конфигурация Kerberos  
 Чтобы подключиться к защищенному с помощью Kerberos кластеру Hadoop [с помощью MIT KDC], сделайте следующее.  
  
1.  Найдите каталог конфигурации Hadoop в каталоге установки SQL Server. Как правило, путь выглядит следующим образом:  
  
    ```  
    C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Polybase\Hadoop\conf  
    ```  
  
2.  Найдите значение конфигурации для ключей конфигурации, перечисленных в таблице, на компьютере с Hadoop. (Найдите файлы в каталоге конфигурации Hadoop на этом же компьютере.)  
  
3.  Скопируйте значения конфигурации в свойство value соответствующих файлов на компьютере с SQL Server.  
  
    |**#**|**Файл конфигурации**|**Ключ конфигурации**|**Действие**|  
    |------------|----------------|---------------------|----------|   
    |1|core-site.xml|polybase.kerberos.kdchost|Укажите область Kerberos. Например, YOUR-REALM.COM|  
    |2|core-site.xml|polybase.kerberos.realm|Укажите имя узла KDC. Например, kerberos.your-realm.com|  
    |3|core-site.xml|hadoop.security.authentication|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например, KERBEROS<br></br>**Примечание о безопасности:** слово KERBEROS должно быть написано прописными буквами. При использовании строчных букв функция может не включиться.|   
    |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например: hdfs/_HOST@YOUR-REALM.COM.|  
    |5|mapred-site.xml|mapreduce.jobhistory.address|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например: mapred/_HOST@YOUR-REALM.COM.|  
    |6|mapred-site.xml|mapreduce.jobhistory.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например, 10.193.26.174:10020|  
    |7|yarn-site.xml yarn|yarn.resourcemanager.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например: yarn/_HOST@YOUR-REALM.COM.|  
  
4.  Создайте объект учетных данных для базы данных, чтобы указать аутентификационные сведения для каждого пользователя Hadoop. См. статью [Объекты T-SQL PolyBase](../../relational-databases/polybase/polybase-t-sql-objects.md).  
  
## <a name="next-steps"></a>Следующие шаги  
 [Объекты PolyBase T-SQL](../../relational-databases/polybase/polybase-t-sql-objects.md)  
  
 [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)  
  
## <a name="see-also"></a>См. также:  
 [Конфигурация PolyBase (Transact-SQL)](../../database-engine/configure-windows/polybase-connectivity-configuration-transact-sql.md)   
 [Руководство по PolyBase](../../relational-databases/polybase/polybase-guide.md)  
  
  