---
title: Расширение языка Java в SQL Server 2019 - службы машинного обучения SQL Server
description: Установка, Настройка и проверка расширение языка Java на SQL Server 2019 для систем Windows и Linux.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/07/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a258573ff7506f2533c2f91edb5751cfd1121dc8
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2018
ms.locfileid: "53431718"
---
# <a name="java-language-extension-in-sql-server-2019"></a>Расширение языка Java в SQL Server 2019 

Начиная с версии SQL Server 2019 preview на Windows и Linux, можно выполнять пользовательский код Java [extensibility framework](../concepts/extensibility-framework.md) как дополнительный компонент для экземпляра компонента database engine. 

Инфраструктура расширяемости — это архитектура для выполнения внешнего кода: Java (начиная с SQL Server 2019), [Python (начиная с SQL Server 2017)](../concepts/extension-python.md), и [R (начиная с SQL Server 2016)](../concepts/extension-r.md). Выполнение кода является изолированной от основных процессов, но полностью интегрирован с выполнение запроса SQL Server. Это означает, что можно передавать данные из любого запроса SQL Server в среду выполнения внешних и использовать или сохранить результаты обратно в SQL Server.

Как и в любых программирования расширений языка, системная хранимая процедура [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) — это интерфейс для выполнения предварительно скомпилированный код Java.

## <a name="prerequisites"></a>предварительные требования

Экземпляр SQL Server 2019 предварительной версии является обязательным. Более ранние версии не имеют интеграции Java. 

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

Вы можете установить [механизм баз данных и расширения Java вместе](../../linux/sql-server-linux-setup-machine-learning.md#install-all), или добавить поддержку Java к существующему экземпляру. Следующие примеры добавьте расширение Java к существующей установке.  

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

### <a name="grant-permissions-on-linux"></a>GRANT, предоставление разрешений на платформе Linux

Чтобы предоставить SQL Server разрешения на выполнение классов Java, необходимо задать разрешения.

Чтобы предоставляют права чтения и выполнения доступ к JAR-файлы или файлы классов, выполните следующую **chmod** команду для каждого класса или jar-файла. Мы рекомендуем сначала разместить файлы класса в JAR-файл, при работе с SQL Server. Дополнительные сведения о создании JAR-файл, см. в разделе [Создание JAR-файл](#create-jar).

```cmd
chmod ug+rx <MyJarFile.jar>
```
Необходимо также предоставить mssql_satellite разрешения на чтение и выполнение файла каталога или JAR-файл.

* Файлы классов при вызове из SQL Server, mssql_satellite будет нужно чтения/разрешения на выполнение *каждые* в иерархии папок, от корневого до непосредственного родительского каталога.

* При вызове JAR-файл из SQL Server, достаточно выполнить команду на сам файл JAR-файл.

```cmd
chown mssql_satellite:mssql_satellite <directory>
```

```cmd
chown mssql_satellite:mssql_satellite <MyJarFile.jar>
```

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

  Для Java 1.8 расширить путь для достижения jvm.dll на Windows в JDK (например, «C:\Program Files\Java\jdk1.8.0_181\bin\server». Кроме того можно указать папку базовый JRE: «C:\Program Files\Java\jre1.8.0_181».

2. В панели управления откройте **система и безопасность**откройте **системы**и нажмите кнопку **дополнительные свойства системы**.

3. Нажмите кнопку **переменные среды**.

4. Создайте новую переменную для JAVA_HOME.

   ![В переменной среды Java Home](../media/java/env-variable-java-home.png "установки для Java")

<a name="perms-nonwindows"></a>

### <a name="grant-access-to-non-default-jdk-folder-windows-only"></a>Предоставление доступа к папке JDK не по умолчанию (только Windows)

Этот шаг можно пропустить, если вы установили JDK/JRE в папке по умолчанию. 

Для установки папки не по умолчанию, запустите **icacls** команд *с повышенными правами* строки для предоставления доступа к **SQLRUsergroup** и учетные записи служб SQL Server (в  **ALL_APPLICATION_PACKAGES**) для доступа к виртуальной машине Java и Java classpath. Команды будут рекурсивно доступ к данным для всех файлов и папок в пути данного каталога.

#### <a name="sqlrusergroup-permissions"></a>Разрешения SQLRUserGroup

Для именованного экземпляра добавьте имя экземпляра для SQLRUsergroup (например, `SQLRUsergroupINSTANCENAME`).

```cmd
icacls "<PATH TO CLASS or JAR FILES>" /grant "SQLRUsergroup":(OI)(CI)RX /T
```

#### <a name="appcontainer-permissions"></a>Разрешения AppContainer

```cmd
icacls "PATH to JDK/JRE" /grant "ALL APPLICATION PACKAGES":(OI)(CI)RX /T
```

### <a name="add-the-jre-path-to-javahome"></a>Добавить путь JRE JAVA_HOME
Также необходимо добавить путь к JRE в системной переменной среды JAVA_HOME. Если у вас только установить JRE, можно указать путь к папке JRE. Тем не менее если у вас установлен пакет JDK, необходимо будет указать полный путь к виртуальной машине Java, в папке JDK, JRE следующим образом: «C:\Program Files\Java\jdk1.8.0_191\jre\bin\server».

Чтобы создать переменную, используйте панель управления > система и безопасность > системы для доступа к **дополнительные свойства системы**. Нажмите кнопку **переменные среды** и создайте новую переменную для JAVA_HOME.

![В переменной среды Java Home](../media/java/env-variable-java-home.png "установки для Java")

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

<a name="create-jar"></a>

## <a name="how-to-create-a-jar-file-from-class-files"></a>Создание JAR-файл из файлов классов

Перейдите к папке, содержащей файл класса и выполните следующую команду:

```cmd
jar -cf <MyJar.jar> *.class
```

Убедитесь, что путь к **jar.exe** является частью в переменную системного пути. Кроме того укажите полный путь к JAR-файл, который можно найти в разделе/Bin, в папке JDK: `C:\Users\MyUser\Desktop\jdk-10.0.2\bin\jar -cf <MyJar.jar> *.class`

## <a name="next-steps"></a>Следующие шаги

+ [Как вызвать Java в SQL Server](howto-call-java-from-sql.md)
+ [Пример Java в SQL Server](java-first-sample.md)
+ [Типы данных Java и SQL Server](java-sql-datatypes.md)