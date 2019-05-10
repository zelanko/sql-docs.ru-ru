---
title: Расширение языка Java в SQL Server 2019 - расширения языка SQL Server
description: Установка, Настройка и проверка расширение языка Java на SQL Server 2019 для систем Windows и Linux.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: db57689227445b0f50d6ff59fbf81e1d84ecacdb
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64775488"
---
# <a name="java-language-extension-in-sql-server-2019"></a>Расширение языка Java в SQL Server 2019 

Начиная с версии SQL Server 2019 preview на Windows и Linux, вы можете запустить, пользовательские Java-код и используя [extensibility framework](../concepts/extensibility-framework.md) как дополнительный компонент для экземпляра компонента database engine.

Инфраструктура расширяемости — это архитектура для выполнения внешнего кода: Java (начиная с SQL Server 2019), [Python (начиная с SQL Server 2017)](../concepts/extension-python.md), и [R (начиная с SQL Server 2016)](../concepts/extension-r.md). Выполнение кода изолированы от ядра основные процессы, но полностью интегрирован с выполнение запроса SQL Server. Это означает, что можно передавать данные из любого запроса SQL Server в среду выполнения внешних (Java) и использовать или сохранить результаты обратно в SQL Server.

Как и в любых программирования расширений языка, системная хранимая процедура [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) — это интерфейс для выполнения предварительно скомпилированный код Java.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>предварительные требования

Экземпляр SQL Server 2019 предварительной версии является обязательным. Более ранние версии не имеют интеграции Java.

Java 8 в настоящее время является поддерживаемой версией. Более поздние версии, например Java 11, следует с помощью расширения языка, но в настоящее время не поддерживается. Среда выполнения Java (JRE) является обязательным, но JDK полезно, если требуется компилятор Java и разработки пакетов. Поскольку JDK все включительно, если установить JDK, JRE не требуется.

Можно использовать распределение вероятностей Java 8. Ниже приведены два предлагаемых распределений.

| Distribution | Версия Java | Операционные системы | JDK | JRE |
|-|-|-|-|-|
| [Oracle Java SE](https://www.oracle.com/technetwork/java/javase/downloads/index.html) | 8 | Windows и Linux | Да | Да |
| [Zulu OpenJDK](https://www.azul.com/downloads/zulu/) | 8 | Windows и Linux | Да | Нет |

В Linux, в настоящее время **mssql-server расширяемости java** пакет автоматически устанавливает JRE 8, если они еще не установлены. Скрипты установки также добавить переменную среды с именем переменная путь виртуальной машины Java.

В Windows, мы рекомендуем установить JDK в стандартной `/Program Files/` папку, если это возможно. В противном случае требуется дополнительная настройка для предоставления разрешений для исполняемых файлов. Дополнительные сведения см. в разделе [разрешение (Windows)](#perms-nonwindows) настоящего документа.

> [!Note]
> Учитывая, что Java имеет обратную совместимость, могут работать в более ранних версий, но поддерживаются и проверенные версии этой ранней CTP-версии Java 8. 

<a name="install-on-linux"></a>

## <a name="install-on-linux"></a>Установка в Linux

Вы можете установить [механизм баз данных и расширения Java вместе](../../linux/sql-server-linux-setup-machine-learning.md#install-all), или добавить поддержку Java к существующему экземпляру. Следующие примеры добавьте расширение Java к существующей установке.  

```bash
# RedHat install commands
sudo yum install mssql-server-extensibility-java

# Ubuntu install commands
sudo apt-get install mssql-server-extensibility-java

# SUSE install commands
sudo zypper install mssql-server-extensibility-java
```

При установке **mssql-server расширяемости java**, пакет автоматически устанавливает JRE 8, если они еще не установлены. Он также добавляется путь виртуальной машины Java для переменной среды с именем переменная.

После завершения установки, ваш следующий шаг — [настройте выполнение внешних скриптов](#configure-script-execution).

> [!Note]
> На устройстве, подключенном к Интернету зависимости пакетов загружаются и устанавливаются как часть установки главного пакета. Дополнительные сведения, включая установки в автономном режиме, см. в разделе [установить машинного обучения SQL Server в Linux](../../linux/sql-server-linux-setup-machine-learning.md).

### <a name="grant-permissions-on-linux"></a>GRANT, предоставление разрешений на платформе Linux

Не нужно выполнять этот шаг, если вы используете внешние библиотеки. Рекомендуемый способ работы использует внешние библиотеки. Дополнительные сведения о создании внешней библиотеки из JAR-файл, см. в разделе [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)

Если вы не используете внешние библиотеки, необходимо предоставить разрешения на выполнение классов Java в JAR-файлу SQL Server.

Чтобы предоставляют права чтения и выполнения доступ к JAR-файл, выполните следующую **chmod** команду JAR-файл. Мы рекомендуем всегда помещения файлов класса в JAR-файл, при работе с SQL Server. Дополнительные сведения о создании JAR-файл, см. в разделе [Создание JAR-файл](#create-jar).

```cmd
chmod ug+rx <MyJarFile.jar>
```

Необходимо также предоставить разрешения mssql_satellite JAR-файл для чтения и выполнения.

```cmd
chown mssql_satellite:mssql_satellite <MyJarFile.jar>
```

<a name="install-on-windows"></a>

## <a name="install-on-windows"></a>Установка в Windows

1. Убедитесь, что установлена поддерживаемая версия Java. Дополнительные сведения см. в разделе [предварительные требования](#prerequisites).

2. [Запустите программу установки](../install/sql-machine-learning-services-windows-install.md) для установки SQL Server 2019.

3. Когда вы дойдете до выбора компонентов, выберите **служб машинного обучения (в базе данных)**. 

   Несмотря на то, что интеграция Java не поставляется с библиотеки машинного обучения, этот вариант в программе установки, предоставляющего платформу для расширения. При желании можно опустить R и Python.

4. Завершение работы мастера установки и затем продолжите следующие две задачи.

### <a name="add-the-jrehome-variable"></a>Добавить переменную-переменная

Переменная является переменной среды операционной системы, который указывает расположение интерпретатора Java. На этом шаге необходимо создайте системную переменную среды для него на Windows.

1. Найдите и скопируйте путь к корневому JRE (например, `C:\Program Files\Zulu\zulu-8\jre\`).

    В зависимости от Java нужным образом страну JDK или JRE может отличаться от пути пример выше.
    Даже если у вас установлен пакет JDK, вы часто раз будет получить вложенную папку JRE как часть установки, поэтому в этом случае указывают на папку jre.
    Расширение Java будет пытаться загрузить jvm.dll из пути % JRE_HOME%\bin\server.

2. В панели управления откройте **система и безопасность**откройте **системы**и нажмите кнопку **дополнительные свойства системы**.

3. Нажмите кнопку **переменные среды**.

4. Создать новую переменную для `JRE_HOME` со значением пути JDK/JRE (найденным на шаге 1).

5. Перезапустите [панель запуска](../concepts/extensibility-framework.md#launchpad).

    1. Откройте [диспетчер конфигурации SQL Server](../../relational-databases/sql-server-configuration-manager.md).

    2. В списке служб SQL Server, щелкните правой кнопкой мыши панель запуска SQL Server и выберите **перезапустите**.

<a name="perms-nonwindows"></a>

### <a name="grant-access-to-non-default-jre-folder-windows-only"></a>Предоставление доступа к папке JRE не по умолчанию (только Windows)

Если вы не устанавливали JDK или JRE каталоге program files, необходимо выполнить следующие действия. Запустите **icacls** команд *с повышенными правами* строки для предоставления доступа к **SQLRUsergroup** и учетные записи служб SQL Server (в **ALL_APPLICATION_ ПАКЕТЫ**) для доступа к JRE. Команды будут рекурсивно доступ к данным для всех файлов и папок в пути данного каталога.

#### <a name="sqlrusergroup-permissions"></a>Разрешения SQLRUserGroup

Для именованного экземпляра добавьте имя экземпляра для SQLRUsergroup (например, `SQLRUsergroupINSTANCENAME`).

```cmd
icacls "<PATH to JRE>" /grant "SQLRUsergroup":(OI)(CI)RX /T
```

Этот шаг можно пропустить, если вы установили JDK/JRE в папке по умолчанию в папке program files в Windows.

#### <a name="appcontainer-permissions"></a>Разрешения AppContainer

```cmd
icacls "PATH to JRE" /grant "ALL APPLICATION PACKAGES":(OI)(CI)RX /T
```

<a name="configure-script-execution"></a>

## <a name="configure-script-execution"></a>Настройте выполнение сценария

На этом этапе все почти готово для выполнения кода Java в Linux или Windows. В качестве последнего шага переключитесь в SQL Server Management Studio, Azure data studio, SQL CMD или другое средство, которое дает возможность запускать сценарий Transact-SQL, чтобы включить выполнение внешних скриптов.

  ```sql
  EXEC sp_configure 'external scripts enabled', 1
  RECONFIGURE WITH OVERRIDE
-- No restart is required after this step as of SQl Server 2019
 ```

## <a name="verify-installation"></a>Проверка установки

Чтобы подтвердить работоспособность установки, создания и выполнения [пример приложения](java-first-sample.md) использование просто устанавливается и добавляется переменная среды выполнения Java.

## <a name="differences-in-ctp-25"></a>Различия в CTP-версии 2.5

Если вы уже знакомы со службами машинного обучения, авторизация и изоляция модель расширения был изменен в этом выпуске. Дополнительные сведения см. в разделе [отличия в установке служб машинного обучения 2019 г. для SQL Server](../install/sql-machine-learning-services-ver15.md).

## <a name="limitations-in-ctp-25"></a>Ограничения в CTP-версии 2.5

* Не может превышать количество значений в входного и выходного буферов `MAX_INT (2^31-1)` потому, что это максимальное количество элементов, которые могут быть распределены в виде массива в Java.

* Выходные параметры в [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) не поддерживаются в этой версии.

* Потоковая передача с помощью параметра sp_execute_external_script @r_rowsPerRead не поддерживается в этой CTP-версии.

* Секционирование с помощью параметра sp_execute_external_script @input_data_1_partition_by_columns не поддерживается в этой CTP-версии.

<a name="create-jar"></a>

## <a name="how-to-create-a-jar-file-from-class-files"></a>Создание JAR-файл из файлов классов

Мы рекомендуем всегда упаковку интересующими файлами классов в JAR-файл, при выполнении из SQL Server.
Чтобы создать JAR-файл из файлов классов, перейдите к папке, содержащей файл класса и выполните следующую команду:

```cmd
jar -cf <MyJar.jar> *.class
```

Убедитесь, что путь к **jar.exe** является частью в переменную системного пути. Кроме того укажите полный путь к JAR-файл, который можно найти в разделе/Bin, в папке JDK: `C:\Users\MyUser\Desktop\jdk1.8.0_201\bin\jar -cf <MyJar.jar> *.class`

## <a name="next-steps"></a>Следующие шаги

+ [Как вызвать Java в SQL Server](howto-call-java-from-sql.md)
+ [Пример Java в SQL Server](java-first-sample.md)
+ [Расширения Microsoft SDK для Java для Microsoft SQL Server](java-sdk.md)
+ [Типы данных Java и SQL Server](java-sql-datatypes.md)
