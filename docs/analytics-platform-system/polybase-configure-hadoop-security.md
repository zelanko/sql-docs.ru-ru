---
title: Настройка безопасности Hadoop в Polybase
description: Объясняется, как настроить Polybase в Parallel Data Warehouse для подключения к внешним Hadoop.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 10/26/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: f275c77556e8abe8932e241075b9e24e2ae5db77
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74400658"
---
# <a name="polybase-configuration-and-security-for-hadoop"></a>Конфигурация и обеспечение безопасности PolyBase для Hadoop

Эта статья содержит справочные сведения о различных параметрах конфигурации, которые влияют на подключение к интерфейсу AP Polybase к Hadoop. Пошаговое руководство по работе с Polybase см. в разделе [понятие polybase](configure-polybase-connectivity-to-external-data.md).

> [!NOTE]
> В APS изменения в XML-файлах необходимы для всех узлов вычислений и управляющих узлов.
> 
> При изменении XML-файлов в ТД следует соблюдать особую осторожность. Любые отсутствующие теги и ненужные символы могут сделать недействительным XML-файл, препятствующий усаблилти функции.
> Файлы конфигурации Hadoop расположены по следующему пути:  
> ```  
> C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf 
> ``` 
> Для вступления в силу любых изменений в XML-файлах требуется перезапуск службы.

## <a id="rpcprotection"></a>Настройка Hadoop. RPC. Protection

Типичный способ защиты взаимодействия в кластере Hadoop — изменение конфигурации hadoop.rpc.protection на Privacy (Конфиденциальность) или Integrity (Целостность). По умолчанию PolyBase предполагает, что задана конфигурация Authenticate (Проверка подлинности). Чтобы переопределить эту настройку по умолчанию, добавьте в файл core-site.xml указанное ниже свойство. Изменение конфигурации позволит осуществлять безопасную передачу данных между узлами Hadoop и использовать SSL-подключение к SQL Server.

```xml
<!-- RPC Encryption information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG -->
   <property>
     <name>hadoop.rpc.protection</name>
     <value></value>
   </property> 
```

## <a id="kerberossettings"></a>Конфигурация Kerberos  

Когда PolyBase выполняет проверку подлинности в защищенном кластере Kerberos, параметр hadoop.rpc.protection должен по умолчанию иметь значение Authenticate. При этом обмен данными между узлами Hadoop остается в незашифрованном виде. Чтобы использовать значение Privacy или Integrity для параметра hadoop.rpc.protection, обновите файл core-site.xml на сервере PolyBase. Дополнительные сведения см. в предыдущем разделе [Подключение к кластеру Hadoop с параметром Hadoop.rpc.protection](#rpcprotection).

Чтобы подключиться к кластеру Hadoop с защитой Kerberos с помощью MIT KDC, необходимо выполнить следующие изменения на всех расчетных узлах APS и узле управления:

1. Найдите каталоги конфигурации Hadoop в пути установки ТД. Как правило, путь выглядит следующим образом:  

   ```  
   C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf  
   ```  

2. Найдите значение конфигурации для ключей конфигурации, перечисленных в таблице, на компьютере с Hadoop. (Найдите файлы в каталоге конфигурации Hadoop на этом же компьютере.)  
   
3. Скопируйте значения конфигурации в свойство value соответствующих файлов на компьютере с SQL Server.  
   
   |**#**|**Файл конфигурации**|**Ключ конфигурации**|**Поддержки**|  
   |------------|----------------|---------------------|----------|   
   |1|core-site.xml|polybase.kerberos.kdchost|Укажите имя узла KDC. Например, kerberos.your-realm.com|  
   |2|core-site.xml|polybase.kerberos.realm|Укажите область Kerberos. Например, YOUR-REALM.COM|  
   |3|core-site.xml|hadoop.security.authentication|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например, KERBEROS<br></br>**Примечание по безопасности.** Протокол KERBEROS должен быть написан в верхнем регистре. При использовании строчных букв функция может не включиться.|   
   |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Пример: hdfs/_HOST@YOUR-REALM.COM|  
   |5|mapred-site.xml|mapreduce.jobhistory.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Пример: mapred/_HOST@YOUR-REALM.COM|  
   |6|mapred-site.xml|mapreduce.jobhistory.address|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например, 10.193.26.174:10020|  
   |7|yarn-site.xml yarn|yarn.resourcemanager.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Пример: yarn/_HOST@YOUR-REALM.COM|  

**core-site.xml**
```xml
<property>
  <name>polybase.kerberos.realm</name>
  <value></value>
</property>
<property>
  <name>polybase.kerberos.kdchost</name>
  <value></value>
</property>
<property>
    <name>hadoop.security.authentication</name>
    <value>KERBEROS</value>
</property>
```

**hdfs-site.xml**
```xml
<property>
  <name>dfs.namenode.kerberos.principal</name>
  <value></value> 
</property>
```

**mapred-site.xml**
```xml
<property>
  <name>mapreduce.jobhistory.principal</name>
  <value></value>
</property>
<property>
  <name>mapreduce.jobhistory.address</name>
  <value></value>
</property>
```

**yarn-site.xml**
```xml
<property>
  <name>yarn.resourcemanager.principal</name>
  <value></value>
</property>
```

4. Создайте объект учетных данных для базы данных, чтобы указать аутентификационные сведения для каждого пользователя Hadoop. См. статью [Объекты T-SQL PolyBase](../relational-databases/polybase/polybase-t-sql-objects.md).

## <a id="encryptionzone"></a>Настройка зоны шифрования Hadoop
Если вы используете зону шифрования Hadoop, измените Core-site. XML и HDFS-site. XML, как показано ниже. Укажите IP-адрес, на котором запущена служба KMS, с соответствующим номером порта. Порт по умолчанию для службы KMS в CDH — 16000.

**core-site.xml**
```xml
<property>
  <name>hadoop.security.key.provider.path</name>
  <value>kms://http@<ip address>:16000/kms</value> 
</property>
```

**hdfs-site.xml**
```xml
<property>
  <name>dfs.encryption.key.provider.uri</name>
  <value>kms://http@<ip address>:16000/kms</value>
</property>
<property>
  <name>hadoop.security.key.provider.path</name>
  <value>kms://http@<ip address>:16000/kms</value>
  </property>
```