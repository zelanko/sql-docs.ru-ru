---
title: Настройка подключения PolyBase - Analytics Platform System | Документация Майкрософт
description: В этой статье описывается настройка PolyBase в Parallel Data Warehouse для подключения к внешней Microsoft Azure или Hadoop хранилища BLOB-объектов источников данных. Для выполнения запросов, объединяющие данные из нескольких источников, включая Hadoop, хранилища BLOB-объектов Azure и Parallel Data Warehouse с помощью PolyBase.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 26eeffb1d2a27ee49f01114b015ab4051b145d64
ms.sourcegitcommit: 731c5aed039607a8df34c63e780d23a8fac937e1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909874"
---
# <a name="configure-polybase-connectivity-to-external-data"></a>Настройка подключения PolyBase к внешним данным
В этой статье описывается настройка PolyBase в Parallel Data Warehouse для подключения к внешней Microsoft Azure или Hadoop хранилища BLOB-объектов источников данных. Для выполнения запросов, объединяющие данные из нескольких источников, включая Hadoop, хранилища BLOB-объектов Azure и Parallel Data Warehouse с помощью PolyBase.  
  
### <a name="to-configure-connectivity"></a>Для настройки подключения  
  
1.  Откройте средство запроса, например sqlcmd или SQL Server Data Tools (SSDT) и выполнена процедура sp_configure, чтобы просмотреть текущие параметры 'hadoop connectivity'.  
  
    ![параметр подключения hadoop](./media/configure-polybase-connectivity-to-external-data/APS_PDW_sp_configure.png "APS_PDW_sp_configure")  
  
2.  Решите, где подключение Hadoop, параметр необходимости и нужно ли изменить текущие настройки. Этот параметр применяется для всего региона SQL Server PDW. Полный список параметров конфигурации и версии, см. в разделе [sp_configure](../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
3.  Чтобы изменить параметр 'hadoop connectivity', выполнена процедура sp_configure, с помощью инструкции RECONFIGURE. Ниже приведены некоторые примеры.  
  
    ```sql  
    --Enable connectivity to Hortonworks Data Platform for Windows Server (HDP) or HDInsight’s Microsoft Azure blob storage  
    EXEC sp_configure 'hadoop connectivity', 4;   
    RECONFIGURE;  
  
    -- Enable connectivity to Hortonworks Data Platform (HDP)for Linux   
    EXEC sp_configure 'hadoop connectivity', 5;   
    RECONFIGURE;  
  
    -- Enable connectivity to Cloudera CDH for Linux   
    EXEC sp_configure 'hadoop connectivity', 3;   
    RECONFIGURE;  
  
    -- Disable the Hadoop connectivity option   
    EXEC sp_configure 'hadoop connectivity', 0;  
    RECONFIGURE;  
    ```  
  
    Выполнение хранимой процедуры sp_configure RECONFIGURE задает значение параметра конфигурации. Перезапуск области необходим для задания значения. Поскольку требуется перезагрузка после следующей остановкой также, не нужно выполнять перезагрузку до и после следующего шага, который изменяет core-site.xml.  
  
4.  Чтобы включить хранилище BLOB-объектов Microsoft Azure в качестве внешнего источника данных, добавьте один или несколько ключей доступа Microsoft Azure хранилища учетной записи в файл PDW core-site.xml. Чтобы добавить ключ:  
  
    1.  Найти имя учетной записи хранения Microsoft Azure. Чтобы просмотреть учетные записи хранения, войдите в[портала Azure](https://portal.azure.com) и нажмите кнопку **учетные записи хранения (классика)**.  
  
        ![Имя учетной записи хранения Windows Azure](./media/configure-polybase-connectivity-to-external-data/APS_PDW_AzureStorageAccountName.png "APS_PDW_AzureStorageAccountName")  
  
    2.  Найти ключ доступа учетной записи хранения Azure. Чтобы сделать это, щелкните имя вашей учетной записи хранения и в колонке "Параметры" щелкните **ключи**. Это показано имя и хранилища ключей учетной записи.  
  
        ![Ключи доступа учетной записи хранилища Windows Azure](./media/configure-polybase-connectivity-to-external-data/APS_PDW_AzureStorageAccountAccessKey.png "APS_PDW_AzureStorageAccountAccessKey")  
  
    3.  Откройте удаленный рабочий стол для узла управления PDW.  
  
    4.  Откройте файл C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf\core-site.xml.  
  
    5.  Добавьте следующее свойство с именем и значением атрибутами core-site.xml.  
  
        ```xml  
        <property>  
          <name>fs.azure.account.key.<your storage account name>.blob.core.windows.net</name>  
          <value><your storage account access key></value>  
        </property>  
        ```  
  
        В этом примере используется учетная запись имени и ключа доступа было показано ранее.  
  
        ```xml  
        <property>  
          <name>fs.azure.account.key.CustomerX.blob.core.windows.net</name>  
          <value>yyeTfCxxxxxxxxQ5WdnapXw77W+FwzHUhX/p/f26fIpnNFGtewzyRN90e1/qmTOl1xxxxxxxxa0goG71LsNcw==</value>  
        </property>  
        ```  
  
        > [!CAUTION]  
        > Примите меры безопасности, прежде чем сохранить ключ доступа в core-site.xml. Любой пользователь, получивший разрешение CONTROL SERVER или ALTER ANY EXTERNAL DATA SOURCE можно создать внешний источник данных, получает доступ к этой учетной записи. После создания внешнего источника данных всем пользователям SQL Server PDW с разрешениями CREATE TABLE можно создать внешнюю таблицу, которая обращается к этой учетной записи хранения. Пользователей можно получить доступ к данным учетной записи и потребляют ресурсы в учетной записи.  
  
    6.  Сохраните изменения в файле core-site.xml.  
  
5.  Добавьте в файл yarn-site.xml yarn.application.classpath и значения.  
  
    Если вы подключаетесь к внешней 1.3 Hadoop, этот шаг можно пропустите.  
  
    Файл yarn-site.xml, начиная с Hadoop 2.0, содержит параметры конфигурации для платформы Hadoop YARN. Этот файл находится на узле управления в разделе **C:\program files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf\\**.  
  
    Чтобы выполнение запросов PolyBase для внешних кластера Hadoop 2.0 в Windows или Linux, необходимо настроить yarn.application.classpath и значения для согласования с параметрами yarn-site.xml на внешних кластера Hadoop. Эта настройка необходима, даже если ваш внешний кластер Hadoop использует параметры по умолчанию.  
  
    Пример параметров по умолчанию.  
  
    ```xml  
    <property>  
        <name>yarn.application.classpath</name>  
        <value>  
          %HADOOP_CONF_DIR%,  
          %HADOOP_COMMON_HOME%/share/hadoop/common/*,  
          %HADOOP_COMMON_HOME%/share/hadoop/common/lib/*,  
          %HADOOP_HDFS_HOME%/share/hadoop/hdfs/*,  
          %HADOOP_HDFS_HOME%/share/hadoop/hdfs/lib/*,  
          %HADOOP_YARN_HOME%/share/hadoop/yarn/*,  
          %HADOOP_YARN_HOME%/share/hadoop/yarn/lib/*  
         </value>  
      </property>  
    ```  
  
    После определения любое свойство в yarn-site.xml, PolyBase использует новые значения свойств при выполнении запросов в Hadoop. Если вы планируете выполнять запросы PolyBase к BLOB-объектов хранилища Azure и внешних кластера Hadoop 2.0 на Windows, должна существовать согласованность всех файлов yarn-site.xml, иначе запросы PolyBase завершится ошибкой.  
   
6.  Перезапустите регион PDW. Чтобы сделать это, используйте средство Configuration Manager. См. в разделе [запустить диспетчер конфигурации служб &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
7.  Проверьте параметры безопасности для подключений Hadoop. Если **слабая аутентификация** в Hadoop на стороне включается с помощью `dfs.permission = true`, необходимо создать пользователя Hadoop **pdw_user** и предоставьте полный доступ для чтения и записи разрешения этого пользователя. SQL Server PDW и соответствующие вызовы из SQL Server PDW всегда выдается как **pdw_user**.  — Имя основного пользователя и нельзя изменить в этой версии Hadoop connectivity и выпуска SQL Server PDW. При отключении безопасности в Hadoop с помощью `dfs.permission = false`, а затем нужно принимать никаких дальнейших действий.  
  
8.  Решите, какие пользователи могут создавать внешний источник данных в хранилище BLOB-объектов Microsoft Azure. Присвойте каждого пользователя имя учетной записи хранения, а также **ALTER ANY EXTERNAL DATA SOURCE** или **CONTROL SERVER** разрешение.  
  
9. Для соединений Hadoop решите, какие пользователи могут создавать внешний источник данных в Hadoop. Присвойте каждого пользователя IP-адрес и порт номер каждого узла имен заданий Hadoop и предоставить им **ALTER ANY EXTERNAL DATA SOURCE** или **CONTROL SERVER** разрешение.  
  
10. Также для подключения к WASB требуется перенаправление запросов DNS, чтобы настроить на устройстве. Чтобы настроить перенаправление запросов DNS, см. в разделе [использовать DNS-сервера пересылки для разрешения имен DNS не являющегося устройством &#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
Авторизованные пользователи теперь можно создать внешние источники данных, внешние форматы файлов и внешних таблиц. Их можно использовать для интеграции данных из нескольких источников, включая Hadoop, хранилище BLOB-объектов Microsoft Azure и SQL Server PDW.  

## <a name="kerberos-configuration"></a>Конфигурация Kerberos  
Учтите, что когда PolyBase выполняет проверку подлинности в защищенном кластере Kerberos, параметр hadoop.rpc.protection должен быть установлен для проверки подлинности. При этом обмен данными между узлами Hadoop остается в незашифрованном виде. 

 Для подключения к кластеру Hadoop с защитой Kerberos [с помощью MIT KDC]:
   
  
1.  Найдите каталог конфигурации Hadoop в каталоге установки на узле управления:  
  
    ```  
    C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf
    ```  
  
2.  Найдите значение конфигурации для ключей конфигурации, перечисленных в таблице, на компьютере с Hadoop. (Найдите файлы в каталоге конфигурации Hadoop на этом же компьютере.)  
  
3.  Скопируйте значения конфигурации в свойство value соответствующих файлов в управляющем узле.  
  
    |**#**|**Файл конфигурации**|**Ключ конфигурации**|**Действие**|  
    |------------|----------------|---------------------|----------|   
    |1|core-site.xml|polybase.kerberos.kdchost|Укажите имя узла KDC. Например, kerberos.your-realm.com|  
    |2|core-site.xml|polybase.kerberos.realm|Укажите область Kerberos. Например, YOUR-REALM.COM|  
    |3|core-site.xml|hadoop.security.authentication|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например, KERBEROS<br></br>**Примечание о безопасности:** слово KERBEROS должно быть написано прописными буквами. При использовании строчных букв функция может не включиться.|   
    |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например: hdfs/_HOST@YOUR-REALM.COM.|  
    |5|mapred-site.xml|mapreduce.jobhistory.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например: mapred/_HOST@YOUR-REALM.COM.|  
    |6|mapred-site.xml|mapreduce.jobhistory.address|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например, 10.193.26.174:10020|  
    |7|yarn-site.xml yarn|yarn.resourcemanager.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например: yarn/_HOST@YOUR-REALM.COM.|  
  
4. Создайте объект учетных данных для базы данных, чтобы указать аутентификационные сведения для каждого пользователя Hadoop. См. статью [Объекты T-SQL PolyBase](../relational-databases/polybase/polybase-t-sql-objects.md).  

5. Перезапустите регион PDW. Чтобы сделать это, используйте средство Configuration Manager. См. в разделе [запустить диспетчер конфигурации служб &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).
 
## <a name="see-also"></a>См. также  
[Конфигурация устройства &#40;Analytics Platform System&#41;](appliance-configuration.md)  
<!-- MISSING LINKS [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  -->  
  
