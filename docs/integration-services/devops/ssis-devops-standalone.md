---
title: Изолированные средства DevOps для служб SQL Server Integration Services (SSIS) | Документация Майкрософт
description: Узнайте, как организовать непрерывную интеграцию и поставку для SSIS с помощью изолированных средств DevOps для SSIS.
ms.date: 10/16/2020
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 52578422cc9f68c728c901cf39bf05425576133b
ms.sourcegitcommit: 36fe62a3ccf34979bfde3e192cfa778505add465
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/11/2020
ms.locfileid: "94521098"
---
# <a name="standalone-sql-server-integration-service-ssis-devops-tools-preview"></a>Изолированные средства DevOps для служб SQL Server Integration Services (SSIS) (предварительная версия)

Изолированные **средства DevOps для SSIS** предоставляют набор исполняемых файлов для выполнения задач CICD в SSIS. Отсутствие зависимостей от установки Visual Studio или среды выполнения SSIS позволяет легко интегрировать эти исполняемые файлы с любой платформой CICD. Предоставляются следующие исполняемые файлы:

- SSISBuild.exe для сборки проектов SSIS по модели развертывания проекта или развертывания пакета;
- SSISDeploy.exe для развертывания файлов ISPAC в каталоге SSIS или файлов DTSX и их зависимостей в файловой системе.

## <a name="installation"></a>Установка

Требуется платформа .NET Framework 4.6.2 или более поздней версии.

Скачайте последнюю версию установщика из [центра загрузки](https://aka.ms/AA9xp65), а затем установите его с помощью мастера или из командной строки.

- Установка с помощью мастера

Дважды щелкните EXE-файл, чтобы запустить установку, а затем укажите папку для извлечения исполняемых файлов и зависимостей.

![Расположение установки](media/installation-location.png)

- Установка из командной строки

```
SSISDevOpsTools.exe /Q /C /T:<full path>
```

![Командная строка для установки](media/installation-command-line.png)


## <a name="ssisbuildexe"></a>SSISBuild.exe

**Синтаксис**

```
SSISBuild.exe -project|-p:<dtproj file path> [-configuration|-c:<configuration name>] [-projectPassword|-pp:<project password>] [-stripSensitive|-ss] [-output|-o:<output path>] [-log|-l:<log level>[;<log path>]] [-quiet|-q] [-help|-h|-?]
```

**Параметры**

|Параметр|Описание|
|---------|---------|
|-project \|-p:\<dtproj file path>|Путь в файловой системе к файлу dtproj для сборки.|
|-configuration\|-c:\<configuration name>|Имя конфигурации проекта, которую необходимо использовать для сборки. Если не указано, по умолчанию используется первая конфигурация проекта, определенная в DTPROJ-файле.|
|-projectPassword\|-pp:\<project password>|Пароль для проекта SSIS и его пакетов. Этот аргумент допустим только в том случае, если для проекта и пакетов SSIS установлен уровень защиты EncryptSensitiveWithPassword или EncryptAllWithPassword. В модели развертывания пакета все пакеты должны иметь одинаковый пароль, который и указывается в этом аргументе.|
|-stripSensitive\|-ss|Изменяет для проекта SSIS уровень защиты на DontSaveSensitve. Если установлен уровень защиты EncryptSensitiveWithPassword или EncryptAllWithPassword, аргумент -projectPassword должен быть задан правильно. Этот параметр допустим только для модели развертывания проекта.|
|-output\|-o:\<output path>|Выходной путь для артефакта сборки. Значение этого аргумента заменит собой путь вывода по умолчанию, заданный в конфигурации проекта.|
|-log\|-l:\<log level>[;\<log path>]|Параметры для журнала. <li>log level (уровень ведения журнала): В файл журнала будут помещаться только записи, у которых уровень ведения журнала равен этому значению или превышает его. Различают четыре уровня ведения журнала (в порядке повышения важности): DIAG, INFO, WRN, ERR. По умолчанию используется уровень ведения журнала INFO, если этот аргумент не указан. <li> log path: (путь к журналу): Путь к файлу для сохранения журналов. Если этот путь не указан, файл журнала не создается.|
|-quiet\|-q|Подавляет вывод журналов в стандартный поток вывода.|
|-help\|-h\|-?|Отображает подробные сведения об использовании этой служебной программы командной строки.|

**Примеры**

- Сборка DTPROJ-файла с первой по порядку конфигурацией проекта, без шифрования с паролем:    
    ```
    SSISBuild.exe -p:"C:\projects\demo\demo.dtproj"
    ```

- Сборка DTPROJ-файла с конфигурацией DevConfiguration, с шифрованием на основе пароля и вывод артефактов сборки в указанную папку:
    ```
    SSISBuild.exe -p:C:\projects\demo\demo.dtproj -c:DevConfiguration -pp:encryptionpassword -o:D:\folder
    ```

- Сборка DTPROJ-файла с конфигурацией DevConfiguration, с шифрованием на основе пароля, удаление из файла конфиденциальных данных и установка уровня ведения журнала DIAG:
    ```
    SSISBuild.exe -p:C:\projects\demo\demo.dtproj -c:DevConfiguration -pp:encryptionpassword -ss -l:diag
    ```

## <a name="ssisdeployexe"></a>SSISDeploy.exe

**Синтаксис**

```
SSISDeploy.exe -source|-s:<source path> -destination|-d:<type>;<path>[;server] [-authType|-at:<auth type name>] [-connectionStringSuffix|-css:<connection string suffix>] [-projectPassword|-pp:<project password>] [-username|-u:<username>] [-password|-p:<password>] [-log|-l:<log level>[;<log path>]] [-quiet|-q] [-help|-h|-?]
```

**Параметры**

|Параметр|Описание|
|---------|---------|
|-source\|-s:\<source path>|Путь к файлу артефактов для развертывания в локальной файловой системе. Поддерживаются значения ISPAC, DTSX, путь к папке для DTSX, SSISDeploymentManfiest.|
|-destination\|-d:\<type>;\<path>[;сервер]|Тип назначения, путь к конечной папке и имя сервера для каталога SSIS, в котором будет развернут исходный файл. В настоящее время поддерживаются следующие два типа назначения: <li> *CATALOG* означает развертывание одного или нескольких ISPAC-файлов в указанном каталоге SSIS. Путь к целевому расположению CATALOG должен иметь такой формат: <br> /SSISDB/\<folder name>[/\<project name>] <br> Необязательный <project name> допустим только в том случае, если источник определяет путь к одному ISPAC-файлу. Для целевого расположения CATALOG должно быть указано имя сервера. <li> *FILE* определяет развертывание пакетов или файлов SSIS, указанных в одном или нескольких файлах SSISDeploymentManifest, по заданному пути в файловой системе. Путь к целевому расположению FILE может указывать на локальную папку или сетевую папку в таком формате: <br>\\\\\<machine name>\\\<folder name>[\\\<sub folder name>\...]|
|-authType\|-at:\<auth type name>|Тип проверки подлинности для доступа к SQL Server. Обязателен для целевого расположения CATALOG. Поддерживаются следующие типы: <li> WIN:  Проверка подлинности Windows <li> SQL:  Проверка подлинности SQL Server <li> ADPWD:  "Active Directory — пароль"; <li> ADINT:  "Active Directory — встроенная".|
|-connectionStringSuffix\|-css:\<connection string suffix> |Суффикс для строки подключения к каталогу SSIS.|
|-projectPassword\|-pp:\<project password> |Пароль для расшифровки файлов ISPAC или DTSX.|
|-username\|-u:\<username>  |Имя пользователя для доступа к указанной файловой системе или каталогу SSIS. Для доступа к файловой системе поддерживается префикс с доменным именем.|
|-password\|-p:\<password>  |Пароль для доступа к указанной файловой системе или каталогу SSIS.|
|-log\|-l:\<log level>[;\<log path>] |Параметры выполнения служебной программы, связанные с ведением журнала. <li> log level (уровень ведения журнала): В файл журнала будут помещаться только записи, у которых уровень ведения журнала равен этому значению или превышает его. Различают четыре уровня ведения журнала (в порядке повышения важности): DIAG, INFO, WRN, ERR. По умолчанию используется уровень ведения журнала INFO, если этот аргумент не указан. <li> log path: (путь к журналу): Путь к файлу для сохранения журналов. Если этот путь не указан, файл журнала не создается.|
|-quiet\|-q |Подавляет вывод журналов в стандартный поток вывода.|
|-help\|-h\|-?  |Отображает подробные сведения об использовании этой служебной программы командной строки.|

**Примеры**

- Развертывание одного ISPAC-файла без шифрования на основе пароля в каталог SSIS с проверкой подлинности Windows.
    ```
    SSISDeploy.exe -s:D:\myfolder\demo.ispac -d:catalog;/SSISDB/destfolder;myssisserver -at:win
    ```

- Развертывание одного ISPAC-файла с шифрованием на основе пароля в каталог SSIS с проверкой подлинности SQL с последующим изменением имени проекта.
    ```
    SSISDeploy.exe -s:D:\myfolder\test.ispac -d:catalog;/SSISDB/folder/testproj;myssisserver -at:sql -u:sqlusername -p:sqlpassword -pp:encryptionpassword
    ```

- Развертывание одного файла SSISDeploymentManifest и связанных с ним файлов в общей папке Azure.
    ```
    SSISDeploy.exe -s:D:\myfolder\mypackage.SSISDeploymentManifest -d:file;\\myssisshare.file.core.windows.net\destfolder -u:Azure\myssisshare -p:storagekey
    ```

- Развертывание папки с DTSX-файлами в локальной файловой системе.
    ```
    SSISDeploy.exe -s:D:\myfolder -d:file;\\myssisshare\destfolder
    ```

## <a name="release-notes"></a>заметки о выпуске;

### <a name="version-011-preview"></a>Предварительная версия 0.1.1

Дата выпуска: 11 ноября 2020 г.

- Исправлена проблема, из-за которой SSISDeploy.exe не удавалось загрузить сборку при развертывании ispac в каталоге SSIS.

### <a name="version-010-preview"></a>Предварительная версия 0.1.0

Дата выпуска: 16 октября 2020 г.

Выпуск начальной предварительной версии изолированных средств DevOps для SSIS.

## <a name="next-steps"></a>Дальнейшие действия

- Получите [изолированные средства DevOps для SSIS](https://aka.ms/AA9xp65)
- Если у вас есть вопросы, посетите страницу [вопросов и ответов](https://marketplace.visualstudio.com/items?itemName=SSIS.ssis-devops-tools&ssr=false#qna).
