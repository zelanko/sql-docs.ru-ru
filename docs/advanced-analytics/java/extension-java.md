---
title: Расширение языка Java в SQL Server 2019 | Документация Майкрософт
description: Запустите пример кода Java на 2019 SQL Server, с помощью расширения языка Java.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/12/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b11025a69a0e72bb7cea1c478350da0f6ede85bf
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51696423"
---
# <a name="java-language-extension-in-sql-server-2019"></a>Расширение языка Java в SQL Server 2019 

Начиная с SQL Server 2019, можно выполнять пользовательский код Java [extensibility framework](../concepts/extensibility-framework.md) как дополнительный компонент для экземпляра компонента database engine. 

Инфраструктура расширяемости — это архитектура для выполнения внешнего кода: Java (начиная с SQL Server 2019), [Python (начиная с SQL Server 2017)](../concepts/extension-python.md), и [R (начиная с SQL Server 2016)](../concepts/extension-r.md). Выполнение кода является изолированной от основных процессов, но полностью интегрирован с выполнение запроса SQL Server. Это означает, что можно передавать данные из любого запроса SQL Server в среду выполнения внешних и использовать или сохранить результаты обратно в SQL Server.

Как и в любых программирования расширений языка, системная хранимая процедура [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) — это интерфейс для выполнения предварительно скомпилированный код Java.

## <a name="prerequisites"></a>предварительные требования

2019 г. SQL Server является обязательным. Более ранние версии не имеют интеграции Java. 

Требования к версии Java меняться в зависимости от Windows и Linux. Среда выполнения Java (JRE) является обязательным, но пакеты JDK полезны, если требуется компилятор Java или пакеты разработки. Поскольку JDK все включительно, если установить JDK, JRE не требуется.

| Операционная система | Версия Java | JRE загрузки | Загрузки JDK |
|------------------|--------------|--------------|--------------|
| Windows          | 1.10         | [JRE 10](https://www.oracle.com/technetwork/java/javase/downloads/jre10-downloads-4417026.html) | [JDK 10](https://www.oracle.com/technetwork/java/javase/downloads/jdk10-downloads-4416644.html)  |
| Linux            | 1.8          |  [JRE 8](https://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) | [JDK 8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  |  

В Linux **mssql-server расширяемости java** пакет автоматически устанавливает JRE 1.8, если они еще не установлены. Скрипты установки также добавить путь виртуальной машины Java для переменной среды JAVA_HOME.

В Windows, мы рекомендуем установить JDK в стандартной /Program файлы и папки, если это возможно. В противном случае требуется дополнительная настройка для предоставления разрешений для исполняемых файлов. Дополнительные сведения см. в разделе [разрешение (Windows)](#perms-nonwindows) настоящего документа.

> [!Note]
> Учитывая, что Java имеет обратную совместимость, могут работать в более ранних версий, а в таблице перечислены версии поддерживаемых и проверенных этой ранней CTP-версии.

<a name="install-on-linux"></a>

## <a name="install-on-linux"></a>Установка в Linux

Вы можете установить [механизм баз данных и расширения Java вместе](../../linux/sql-server-linux-setup-machine-learning.md#chained-installation), или добавить поддержку Java к существующему экземпляру. Следующие примеры добавьте расширение Java к существующей установке.  

```bash
# RedHat install commands
sudo yum install mssql-server-extensibility-java

# Ubuntu install commands
sudo apt-get install mssql-server-extensibility-java

# USE install commands
sudo zypper install mssql-server-extensibility-java
```

При установке **mssql-server расширяемости java**, пакет автоматически устанавливает JRE 1.8, если они еще не установлены. Он также добавляется путь виртуальной машины Java для переменной среды JAVA_HOME.

После завершения установки, ваш следующий шаг — [настройте выполнение внешних скриптов](#configure-script-execution).

> [!Note]
> На устройстве, подключенном к Интернету зависимости пакетов загружаются и устанавливаются как часть установки главного пакета. Дополнительные сведения, включая установки в автономном режиме, см. в разделе [установить машинного обучения SQL Server в Linux](../../linux/sql-server-linux-setup-machine-learning.md).

<a name="install-on-windows"></a>

## <a name="install-on-windows"></a>Установка в Windows

1. [Запустите программу установки](../install/sql-machine-learning-services-windows-install.md) для установки SQL Server 2019.

2. Когда вы дойдете до выбора компонентов, выберите **служб машинного обучения (в базе данных)**. 

   Несмотря на то, что интеграция Java не поставляется с библиотеки машинного обучения, этот вариант в программе установки, предоставляющего платформу для расширения. При желании можно опустить R и Python.

3. Завершение работы мастера установки и затем продолжите следующие две задачи.

### <a name="add-the-javahome-variable"></a>Добавьте переменную JAVA_HOME

JAVA_HOME является переменной среды, который указывает расположение интерпретатора Java. На этом шаге необходимо создайте системную переменную среды для него на Windows.

1. Найдите и скопируйте путь установки JDK/JRE (например, C:\Program Files\Java\jdk-10.0.2).

  В CTP 2.0 Установка JAVA_HOME к папке базовых jdk работает только для Java 1.10. 

  Для Java 1.8 расширить путь для достижения jvm.dll на Windows в JDK (например, «C:\Program Files\Java\jdk1.8.0_181\bin\server». Кроме того, можно указать папку базовый JRE: «C:\Program Files\Java\jre1.8.0_181».

2. В панели управления откройте **система и безопасность**откройте **системы**и нажмите кнопку **дополнительные свойства системы**.

3. Нажмите кнопку **переменные среды**.

4. Создайте новую переменную для JAVA_HOME.

   ![В переменной среды Java Home](../media/java/env-variable-java-home.png "установки для Java")

<a name="perms-nonwindows"></a>

### <a name="grant-permissions-to-java-executables"></a>Предоставление разрешений для исполняемых файлов Java

По умолчанию учетную запись, под которой будет запускаться внешних процессов не имеет доступа к файлам JRE или JDK. В этом разделе выполните следующий сценарий PowerShell для предоставления разрешений на доступ.

1. Найдите и скопируйте расположение установки JDK или JRE. Например он может быть C:\Program Files\Java\jdk-10.0.2.

2. Откройте PowerShell с правами администратора. Если вы не знакомы с этой задачей, см. в разделе [в этой статье](https://www.top-password.com/blog/5-ways-to-run-powershell-as-administrator-in-windows-10/) советы.

3. Выполните следующий скрипт для предоставления **SQLRUserGroup** разрешения к исполняемым файлам Java. 

  **SQLRUserGroup** задает разрешения, в какой внешний выполняются процессы. По умолчанию члены этой группы имеют разрешения на R и Python программные файлы, установленные SQL Server, но не в Java. Для запуска исполняемых файлов Java, вы должны предоставить **SQLRUserGroup** на это разрешение.

   ```powershell
   $Acl = Get-Acl "<YOUR PATH TO JDK / CLASSPATH>"
   $Ar = New-Object  system.security.accesscontrol.filesystemaccessrule("SQLRUsergroup","FullControl","Allow")
   $Acl.SetAccessRule($Ar)
   Set-Acl "<YOUR PATH TO JDK / CLASSPATH>" $Acl 
   ```
4. Выполните следующий скрипт для предоставления **все ПАКЕТЫ ПРИЛОЖЕНИЙ** разрешениями. 

  В SQL Server 2019, контейнеры замените рабочих учетных записей как механизм изоляции процессов, выполняющихся в контейнерах с удостоверением учетной записи службы панели запуска, которой входит **SQLRUserGroup**. Дополнительные сведения см. в разделе [установить различия в SQL Server 2019](../install/sql-machine-learning-services-ver15.md).

   ```powershell
   $Acl = Get-Acl "<YOUR PATH TO JDK / CLASSPATH>" 
   $Ar = New-Object  system.security.accesscontrol.filesystemaccessrule("ALL APPLICATION PACKAGES","FullControl","Allow") 
   $Acl.SetAccessRule($Ar) 
   Set-Acl "<YOUR PATH TO JDK / CLASSPATH>" $Acl 
   ```

5. Повторите предыдущие два шага в Java classpath папкам, содержащим .class или .jar файлы, которые вы хотите запустить на сервере SQL Server. Например, если скомпилированный программ по пути, аналогичному C:\JavaPrograms\my-app, предоставить **SQLRUserGroup** и **все ПАКЕТЫ ПРИЛОЖЕНИЙ** разрешения на папку, чтобы эти программы могут быть загружены.

  Не забудьте предоставить разрешения на полный путь, начиная с корневой папки. Разрешение на только что папки, содержащей не быть достаточно для загрузки кода.

<a name="configure-script-execution"></a>

## <a name="configure-script-execution"></a>Настройте выполнение сценария

На этом этапе все почти готово для выполнения кода Java в Linux или Windows. В качестве последнего шага переключитесь в SQL Server Management Studio или другое средство, которое запускает сценарий Transact-SQL, чтобы включить выполнение внешних скриптов.

  ```sql
  EXEC sp_configure 'external scripts enabled', 1
  RECONFIGURE WITH OVERRIDE
-- No restart is required after this step as of SQl Server 2019
 ```

## <a name="verify-installation"></a>Проверка установки

Чтобы подтвердить работоспособность установки, создания и выполнения [пример приложения](java-first-sample.md) с помощью JDK, установленный, поместив файлы в пути к классам, настроенного ранее.

## <a name="differences-in-ctp-20"></a>Различия в CTP-версии 2.0

Если вы уже знакомы со службами машинного обучения, авторизация и изоляция модель расширения был изменен в этом выпуске. Дополнительные сведения см. в разделе [отличия в установке служб машинного обучения 2019 г. для SQL Server](../install/sql-machine-learning-services-ver15.md).

## <a name="limitations-in-ctp-20"></a>Ограничения в CTP-версии 2.0

* Не может превышать количество значений в входного и выходного буферов `MAX_INT (2^31-1)` потому, что это максимальное количество элементов, которые могут быть распределены в виде массива в Java.

* Выходные параметры в [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) не поддерживаются в этой версии.

* Не поддерживается тип данных LOB для входных и выходных наборов данных в этой версии. См. в разделе [типов данных Java и SQL Server](java-sql-datatypes.md) Дополнительные сведения о данных, какие типы поддерживаются в этой CTP-версии.

* Потоковая передача с помощью параметра sp_execute_external_script @r_rowsPerRead не поддерживается в этой CTP-версии.

* Секционирование с помощью параметра sp_execute_external_script @input_data_1_partition_by_columns не поддерживается в этой CTP-версии.

## <a name="next-steps"></a>Следующие шаги

+ [Как вызвать Java в SQL Server](howto-call-java-from-sql.md)
+ [Пример Java в SQL Server](java-first-sample.md)
+ [Типы данных Java и SQL Server](java-sql-datatypes.md)