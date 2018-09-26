---
title: Расширение языка Java в SQL Server 2019 | Документация Майкрософт
description: Запустите пример кода Java на 2019 SQL Server, с помощью расширения языка Java.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8acb0a72435306cdec8740ffb41ff499eea61fac
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715371"
---
# <a name="java-language-extension-in-sql-server-2019"></a>Расширение языка Java в SQL Server 2019 

Начиная с SQL Server 2019, можно выполнять пользовательский код Java [extensibility framework](../concepts/extensibility-framework.md) как дополнительный компонент для экземпляра компонента database engine. 

Инфраструктура расширяемости — это архитектура для выполнения внешнего кода: Java (начиная с SQL Server 2019), [Python (начиная с SQL Server 2017)](../concepts/extension-python.md), и [R (начиная с SQL Server 2016)](../concepts/extension-r.md). Выполнение кода является изолированной от основных процессов, но полностью интегрирован с выполнение запроса SQL Server. Это означает, что можно передавать данные из любого запроса SQL Server в среду выполнения внешних и использовать или сохранить результаты обратно в SQL Server.

Как и в любых программирования расширений языка, системная хранимая процедура [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) — это интерфейс для выполнения предварительно скомпилированный код Java.

## <a name="1---feature-installation"></a>1 - Установка компонентов

Запустите программу установки SQL Server 2019 г. в Windows или Linux, чтобы установить расширение языка Java. Экземпляр ядра СУБД SQL Server 2019 является обязательным. Невозможно добавить интеграции Java в более ранних версий.

На Windows, запустите [мастер установки](../install/sql-machine-learning-services-windows-install.md). При выборе компонентов, выберите **служб машинного обучения (в базе данных)**. Несмотря на то, что интеграция Java не поставляется с библиотеки машинного обучения, этот вариант в программе установки, предоставляющего платформу для расширения. При желании можно опустить R и Python.

В Linux, установите [СУБД](https://docs.microsoft.com/sql/linux/sql-server-linux-setup), а также [расширяемости пакета и пакета расширения Java](../../linux/sql-server-linux-setup-machine-learning.md).

В следующих примерах приведен синтаксис для каждой операционной системы Linux.

```bash
# RedHat install commands
sudo yum install mssql-server-extensibility
sudo yum install mssql-server-extensibility-java

# Ubuntu install commands
sudo apt-get install mssql-server-extensibility
sudo apt-get install mssql-server-extensibility-java

# USE install commands
sudo zypper install mssql-server-extensibility
sudo zypper install mssql-server-extensibility-java
```

## <a name="2---configuration"></a>2 - конфигурации

С помощью SQL Server Management Studio или другое средство, которое запускает сценарий Transact-SQL, настройте выполнение внешних скриптов на экземпляре компонента database engine.

  ```sql
  EXEC sp_configure 'external scripts enabled', 1
  RECONFIGURE WITH OVERRIDE
-- No restart is required after this step as of SQl Server 2019
 ```

## <a name="3---bring-your-own-java"></a>3 - перевести свои собственные Java

Одной из предыдущих интеграции языков, таких как R и Python разница в которой вы управляете, используемого виртуальной машины Java с SQL Server.

| Версия Java | Операционная система |
|--------------|------------------|
| [Java 1,10](http://jdk.java.net/10/)   | Windows |
| Java 1.8   | Linux | 

Учитывая, что Java имеет обратную совместимость, могут работать в более ранних версий, а в таблице перечислены версии поддерживаемых и проверенных этой ранней CTP-версии.

> [!Note]
>Для выполнения приложений Java с помощью SQL Server, с технической точки зрения достаточно [Java Runtime Environment](http://www.oracle.com/technetwork/java/javase/downloads/jre10-downloads-4417026.html) установлен (JRE). Пакет JDK по разработке пакета, включая компилятор Java и других разработки, связанные с пакетами. Если вы уже установлена среда разработки, среду выполнения Java на компьютере сервера, можно игнорировать инструкции по установке JDK и только установить JRE.

## <a name="jdk-on-windows"></a>JDK в Windows

Загрузите версию Windows [Java SE Development Kit (JDK)](http://www.oracle.com/technetwork/java/javase/downloads/jdk10-downloads-4416644.html).

Установите JDK в группе по умолчанию файлы /Program / чтение папки, если вы хотите избежать необходимости предоставления разрешения на **все ПАКЕТЫ ПРИЛОЖЕНИЙ** и **SQLRUserGroup** в альтернативное расположение группы безопасности . То же руководство применимо для доступа к вашим папкам classpath Java, где при хранении файлов .class или .jar. 

> [!Note]
> Авторизация и изоляция модель расширения был изменен в этом выпуске. Дополнительные сведения см. в разделе [отличия в установке служб машинного обучения 2019 г. для SQL Server](../install/sql-machine-learning-services-ver15.md).

<a name="perms-nonwindows"></a>

### <a name="grant-access-to-non-default-jdk-folder-windows-only"></a>Предоставление доступа к папке JDK не по умолчанию (только Windows)

Этот шаг можно пропустить, если вы установили JDK/JRE в папке по умолчанию. Для установки папки не по умолчанию, запустите следующие скрипты PowerShell, чтобы предоставить доступ к **SQLRUsergroup** и учетные записи служб SQL Server (в ALL_APPLICATION_PACKAGES) для доступа к виртуальной машине Java и Java classpath.

#### <a name="sqlrusergroup-permissions"></a>Разрешения SQLRUserGroup

```powershell
$Acl = Get-Acl "<YOUR PATH TO JDK / CLASSPATH>"
$Ar = New-Object  system.security.accesscontrol.filesystemaccessrule("SQLRUsergroup","FullControl","Allow")
$Acl.SetAccessRule($Ar)
Set-Acl ""<YOUR PATH TO JDK / CLASSPATH>" $Acl 
```

#### <a name="appcontainer-permissions"></a>Разрешения AppContainer

```powershell
$Acl = Get-Acl "<YOUR PATH TO JDK / CLASSPATH>" 
$Ar = New-Object  system.security.accesscontrol.filesystemaccessrule("ALL APPLICATION PACKAGES","FullControl","Allow") 
$Acl.SetAccessRule($Ar) 
Set-Acl "<YOUR PATH TO JDK / CLASSPATH>" $Acl 
```

### <a name="add-the-jdk-path-to-javahome"></a>Добавить путь к JDK JAVA_HOME
Также необходимо добавить путь установки JDK/JRE (например, «C:\Program Files\Java\jdk-10.0.2») для переменной среды операционной системы, имя «JAVA_HOME». 

Чтобы создать переменную, используйте панель управления > система и безопасность > системы для доступа к **дополнительные свойства системы**. Нажмите кнопку **переменные среды** и создайте новую переменную для JAVA_HOME.

![В переменной среды Java Home](../media/java/env-variable-java-home.png "установки для Java")

## <a name="jdk-on-linux"></a>JDK на платформе Linux

В Linux пакет mssql-server расширяемости java автоматически устанавливает JRE 1.8, если они еще не установлены. Он также добавляется путь виртуальной машины Java для переменной среды JAVA_HOME.

## <a name="limitations-in-ctp-20"></a>Ограничения в CTP-версии 2.0

* Не может превышать количество значений в входного и выходного буферов `MAX_INT (2^31-1)` потому, что это максимальное количество элементов, которые могут быть распределены в виде массива в Java.

* В этой версии не поддерживаются выходные параметры в sp_execute_external_script.

* Не поддерживается тип данных LOB для входных и выходных наборов данных в этой версии. См. в разделе [типов данных Java и SQL Server](java-sql-datatypes.md) Дополнительные сведения о данных, какие типы поддерживаются в этой CTP-версии.

* Потоковая передача с помощью параметра sp_execute_external_script @r_rowsPerRead не поддерживается в этой CTP-версии.

* Секционирование с помощью параметра sp_execute_external_script @input_data_1_partition_by_columns не поддерживается в этой CTP-версии.

## <a name="next-steps"></a>Следующие шаги

+ [Как вызвать Java в SQL Server](howto-call-java-from-sql.md)
+ [Пример Java в SQL Server](java-first-sample.md)
+ [Типы данных Java и SQL Server](java-sql-datatypes.md)