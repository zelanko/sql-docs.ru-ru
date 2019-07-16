---
title: Настройка безопасности PolyBase Hadoop в Analytics Platform System | Документация Майкрософт
description: В этой статье описывается настройка PolyBase в Parallel Data Warehouse для подключения к внешней Hadoop.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 10/26/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 1aebac3f63a105f0276e676ccc807aaebdbf097d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960299"
---
# <a name="polybase-configuration-and-security-for-hadoop"></a>Конфигурация и обеспечение безопасности PolyBase для Hadoop

В этой статье содержится для различных параметров конфигурации, которые влияют на подключения APS PolyBase для Hadoop. Пошаговое руководство о том, что PolyBase, см. в разделе [что такое PolyBase](configure-polybase-connectivity-to-external-data.md).

> [!NOTE]
> На точках доступа изменения в XML-файлы требуются на всех вычислительных узлах или управляющем узле.
> 
> Следить при изменении XML-файлы в APS. Все отсутствующие теги или нежелательных символов может сделать недействительным XML-файле, к ухудшению usablilty функции.
> Файлы конфигурации Hadoop находятся по следующему пути:  
> ```  
> C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf 
> ``` 
> Все изменения в XML-файлы требуют перезапуска службы в силу.

## <a id="rpcprotection"></a> Параметр Hadoop.RPC.Protection

Типичный способ защиты взаимодействия в кластере Hadoop — изменение конфигурации hadoop.rpc.protection на Privacy (Конфиденциальность) или Integrity (Целостность). По умолчанию PolyBase предполагает, что задана конфигурация Authenticate (Проверка подлинности). Чтобы переопределить эту настройку по умолчанию, добавьте в файл core-site.xml указанное ниже свойство. Изменение конфигурации позволит осуществлять безопасную передачу данных между узлами Hadoop и использовать SSL-подключение к SQL Server.

```xml
<!-- RPC Encryption information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG -->
   <property>
     <name>hadoop.rpc.protection</name>
     <value></value>
   </property> 
```

## <a id="kerberossettings"></a> Настройка Kerberos  

Когда PolyBase выполняет проверку подлинности в защищенном кластере Kerberos, параметр hadoop.rpc.protection должен по умолчанию иметь значение Authenticate. При этом обмен данными между узлами Hadoop остается в незашифрованном виде. Чтобы использовать значение Privacy или Integrity для параметра hadoop.rpc.protection, обновите файл core-site.xml на сервере PolyBase. Дополнительные сведения см. в предыдущем разделе [Подключение к кластеру Hadoop с параметром Hadoop.rpc.protection](#rpcprotection).

Для подключения к Hadoop с защитой Kerberos кластера с помощью MIT KDC, необходимы следующие изменения на всех точках доступа вычислительных узлах или управляющем узле:

1. Найти каталоги конфигурации Hadoop в каталоге установки APS. Как правило, путь выглядит следующим образом:  

   ```  
   C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf  
   ```  

2. Найдите значение конфигурации для ключей конфигурации, перечисленных в таблице, на компьютере с Hadoop. (Найдите файлы в каталоге конфигурации Hadoop на этом же компьютере.)  
   
3. Скопируйте значения конфигурации в свойство value соответствующих файлов на компьютере с SQL Server.  
   
   |**#**|**Файл конфигурации**|**Ключ конфигурации**|**Действие**|  
   |------------|----------------|---------------------|----------|   
   |1|core-site.xml|polybase.kerberos.kdchost|Укажите имя узла KDC. Например, kerberos.your-realm.com|  
   |2|core-site.xml|polybase.kerberos.realm|Укажите область Kerberos. Пример: YOUR-REALM.COM|  
   |3|core-site.xml|hadoop.security.authentication|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Пример: KERBEROS<br></br>**Примечание по безопасности.** Слово KERBEROS должно быть написано прописными буквами. При использовании строчных букв функция может не включиться.|   
   |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например: hdfs/_HOST@YOUR-REALM.COM.|  
   |5|mapred-site.xml|mapreduce.jobhistory.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например: mapred/_HOST@YOUR-REALM.COM.|  
   |6|mapred-site.xml|mapreduce.jobhistory.address|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Пример: 10.193.26.174:10020|  
   |7|yarn-site.xml yarn|yarn.resourcemanager.principal|Найдите конфигурацию для Hadoop и скопируйте ее на компьютер с SQL Server. Например: yarn/_HOST@YOUR-REALM.COM|  

**Core-site.xml**
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

## <a id="encryptionzone"></a> Настройка зоны шифрования Hadoop
Если вы используете Hadoop зона шифрования изменить core-site.xml и hdfs-site.xml, следующим образом. Укажите IP-адрес, где запущена служба KMS с соответствующий номер порта. Порт по умолчанию для службы KMS в CDH равна 16 000.

**Core-site.xml**
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