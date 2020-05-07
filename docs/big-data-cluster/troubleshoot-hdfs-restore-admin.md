---
title: Восстановление прав администратора для HDFS
titleSuffix: SQL Server Big Data Cluster
description: Восстановление прав администратора для HDFS.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
ms.date: 04/21/2020
ms.topic: how-to
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6fb8c7c53c6edf4a02649f256ac6aa6d7080fdf5
ms.sourcegitcommit: 1f9fc7402b00b9f35e02d5f1e67cad2f5e66e73a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2020
ms.locfileid: "82108698"
---
# <a name="restore-hdfs-admin-rights"></a>Восстановление прав администратора для HDFS

Изменения в списках управления доступом (ACL) HDFS могут привести к изменениям папок `/system` и `/tmp` в HDFS. Наиболее вероятная причина изменения списков управления доступом — пользователь вручную изменил списки управления доступом для папок. Непосредственное изменение разрешений в папках /system и /tmp/logs не поддерживается.

## <a name="symptom"></a>Симптом

Задание Spark передается через ADS и завершается ошибкой инициализации SparkContext и исключением AccessControlException.

```
583 ERROR spark.SparkContext: Error initializing SparkContext.
org.apache.hadoop.security.AccessControlException: Permission denied: user=<UserAccount>, access=WRITE, inode="/system/spark-events":sph:BDCAdmin:drwxr-xr-x
```

Для идентификатора приложения пользовательский интерфейс Yarn показывает состояние KILLED (Завершено).

Если вы попытаетесь выполнить запись в папку от имени пользователя домена, эта операция также завершится сбоем. Вы можете выполнить тестирование с помощью следующего примера:

```bash
kinit <UserAccount>
hdfs dfs -touch /system/spark-events/test
hdfs dfs -rm /system/spark-events/test
```

## <a name="cause"></a>Причина

Списки управления доступом HDFS были изменены для группы безопасности домена пользователя BDC. Возможно, были внесены изменения в списки управления доступом для папок /system и /tmp. Изменение этих папок не поддерживается.

Проверьте наличие изменений с помощью журналов Livy:

```
INFO utils.LineBufferedStream: YYYY-MM-DD-HH:MM:SS,858 INFO yarn.Client: Application report for application_1580771254352_0041 (state: ACCEPTED)
...
WARN rsc.RSCClient: Client RPC channel closed unexpectedly.
INFO interactive.InteractiveSession: Failed to ping RSC driver for session <ID>. Killing application
```

Для идентификатора приложения в пользовательском интерфейсе YARN будет показываться состояние KILLED (Завершено).

Чтобы определить основную причину закрытия подключения RPC, просмотрите данные журнала соответствующего приложения YARN. В предыдущем примере это `application_1580771254352_0041`. С помощью команды `kubectl` подключитесь к объекту pod sparkhead-0 и выполните следующую команду:

Следующая команда позволяет запросить журнал YARN для приложения:

```bash
yarn logs -applicationId application_1580771254352_0041
```

В результатах ниже пользователю отказано в разрешении. 

```
YYYY-MM-DD-HH:MM:SS,583 ERROR spark.SparkContext: Error initializing SparkContext.
org.apache.hadoop.security.AccessControlException: Permission denied: user=user1, access=WRITE, inode="/system/spark-events":sph:BDCAdmin:drwxr-xr-x
```

Это может быть вызвано тем, что пользователь BDC был рекурсивно добавлен в корневую папку HDFS. Такое действие могло повлиять на разрешения по умолчанию.

## <a name="resolution"></a>Решение

Восстановите разрешения с помощью следующего скрипта: Используйте команду `kinit` с правами администратора:

```bash
hdfs dfs -chmod 733 /system/spark-events
hdfs dfs -setfacl --set default:user:sph:rwx,default:other::--- /system/spark-events
hdfs dfs -setfacl --set default:user:app-setup:r-x,default:other::--- /system/appdeploy
hadoop fs -chmod 733 /tmp/logs
hdfs dfs -setfacl --set default:user:yarn:rwx,default:other::--- /tmp/logs
```
