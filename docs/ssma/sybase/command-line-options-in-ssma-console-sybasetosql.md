---
title: Параметры командной строки в консоли SSMA (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sybase Console,Command Line Options
ms.assetid: 337cbd26-67b7-4c88-9deb-d0a69a3d7714
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 5aef07e7b7d1d96d93fba34a376e5374b1754fce
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87932135"
---
# <a name="command-line-options-in-ssma-console-sybasetosql"></a>Параметры командной строки в консоли SSMA (SybaseToSQL)
Корпорация Майкрософт предоставляет надежный набор параметров командной строки для выполнения и управления действиями SSMA. Эти разделы подробно описываются.  
  
## <a name="command-line-options-in-ssma-console"></a>Параметры командной строки в консоли SSMA  
Здесь описаны параметры командной консоли.  
  
В этом разделе термин "параметр" также называется "Switch".  
  
-   Параметры не учитывают регистр и могут начинаться с символа " **-** " или " **/** ".  
  
-   Если указаны параметры, они становятся обязательными для указания соответствующих параметров параметра.  
  
-   Параметры параметров должны отделяться пробелами от символа параметра.  
  
    **Примеры синтаксиса:**  
  
    `C:\> SSMAforSybaseConsole.EXE -s scriptfile`  
  
    `C:\> SSMAforSybaseConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\VariableValueFileSample.xml" -c "C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ServersConnectionFileSample.xml"`  
  
-   Имена папок или файлов, содержащие пробелы, должны быть указаны в двойных кавычках.  
  
-   Выходные данные записей командной строки и сообщений об ошибках хранятся в STDOUT или в указанном файле.  
  
### <a name="script-file-option--sscript"></a>Параметр файла скрипта:-s/Script  
Обязательный параметр, путь или имя файла скрипта указывает сценарий последовательностей команд, выполняемых SSMA.  
  
**Примеры синтаксиса:**  
  
`C:\>SSMAforSybaseConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml"`  
  
### <a name="variable-value-file-option--vvariable"></a>Параметр файла значения переменной:-v/переменная  
Этот файл состоит из переменных, используемых в файле скрипта. Это необязательный параметр. Если переменные не объявлены в файле переменных и используются в файле скрипта, приложение создает ошибку и завершает выполнение консоли.  
  
**Примеры синтаксиса:**  
  
-   Переменные, определенные в нескольких файлах значений переменных, возможно, одна со значением по умолчанию, а другая — с определенным значением, если применимо. Последний файл переменной, указанный в аргументах командной строки, имеет предпочтение, если существует дублирование переменных:  
  
    `C:\>SSMAforSybaseConsole.EXE -s`  
  
    `"C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml" -v c:\migration`  
  
    `projects\global_variablevaluefile.xml -v "c:\migrationprojects\instance_variablevaluefile.xml"`  
  
### <a name="server-connection-file-option--cserverconnection"></a>Параметр файла соединения сервера:-c/ServerConnection  
Этот файл содержит сведения о подключении сервера для каждого сервера. Определение каждого сервера определяется уникальным ИДЕНТИФИКАТОРом сервера. Идентификаторы серверов указываются в файле скрипта для команд, связанных с подключением.  
  
Определение сервера может быть частью файла подключения к серверу или файла скрипта. Идентификатор сервера в файле скрипта имеет приоритет над файлом соединения с сервером, в случае дублирования идентификатора сервера.  
  
**Примеры синтаксиса:**  
  
-   Идентификаторы серверов используются в файле скрипта и определяются в отдельном файле соединения сервера. в файле соединения сервера используются переменные, определенные в файле значений переменных:  
  
    `C:\>SSMAforSybaseConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -v`  
  
    `c:\SsmaProjects\myvaluefile1.xml -c`  
  
    `c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
-   Определение сервера внедряется в файл скрипта:  
  
    `C:\>SSMAforSybaseConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml"`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>Параметр вывода XML:-x/ксмлаутпут [ксмлаутпутфиле]  
Эта команда используется для вывода выходных сообщений команды в формате XML либо в консоль, либо в XML-файл.  
  
Существует два варианта, доступных для ксмлаутпут, визуализациям..,:  
  
-   Если путь к файлу указан после параметра ксмлаутпут, выходные данные перенаправляются в файл.  
  
    **Пример синтаксиса:**  
  
    `C:\>SSMAforSybaseConsole.EXE -s`  
  
    `"C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -x d:\xmloutput\project1output.xml`  
  
-   Если после параметра ксмлаутпут не указан путь к файлу, ксмлаут отображается на самой консоли.  
  
    **Пример синтаксиса:**  
  
    `C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -xmloutput`  
  
### <a name="log-file-option--llog"></a>Параметр файла журнала:-l/log  
Все операции SSMA в консольном приложении записываются в файл журнала. Это необязательный параметр. Если файл журнала и его путь указаны в командной строке, то журнал создается в указанном расположении. В противном случае он создается в своем расположении по умолчанию.  
  
**Пример синтаксиса:**  
  
`C:\>SSMAforSybaseConsole.EXE`  
  
`"C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option--eprojectenvironment"></a>Параметр папки среды проекта:-e/прожектенвиронмент  
Это означает папку параметров среды проекта для текущего проекта SSMA. Этот параметр является необязательным.  
  
**Пример синтаксиса:**  
  
`C:\>SSMAforSybaseConsole.EXE -s`  
  
`"C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -e c:\SsmaProjects\CommonEnvironment`  
  
### <a name="secure-password-option--psecurepassword"></a>Параметр безопасного пароля:-p/секурепассворд  
Этот параметр указывает зашифрованный пароль для подключений к серверу. Он отличается от всех остальных параметров: параметр не выполняет ни один скрипт и не помогает выполнять операции миграции, но помогает управлять шифрованием паролей для подключений к серверу, используемых в проекте миграции.  
  
В качестве параметра командной строки нельзя ввести любой другой параметр или пароль. В противном случае возникает ошибка. Дополнительные сведения см. в разделе [Управление паролями](managing-passwords-sybasetosql.md) .  
  
Поддерживаются следующие подпараметры `-p/securepassword` :  
  
-   Чтобы добавить пароль в защищенное хранилище для указанного идентификатора сервера или для всех идентификаторов серверов, определенных в файле соединения с сервером. Параметр-overwrite ниже обновляет пароль, если он уже существует:  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}` `-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-s|-script <server-connection-file> [-v|variable <variable-value-file>] [-o|overwrite]`  
  
-   Чтобы удалить зашифрованный пароль из защищенного хранилища с указанным ИДЕНТИФИКАТОРом сервера или для всех идентификаторов серверов, выполните следующие действия.  
  
    `-p/securepassword -r/remove {<server_id> [, ...n] | all}`  
  
-   Для вывода списка идентификаторов серверов, для которых шифруется пароль:  
  
    `-p/securepassword -l/list`  
  
-   Экспорт паролей, хранящихся в защищенном хранилище, в зашифрованный файл. Этот файл шифруется с помощью заданной пользователем парольной фразы.  
  
    `-p/securepassword -e/export {<server-id> [, ...n] | all} <encrypted-password -file>`  
  
-   Зашифрованный файл, который был экспортирован ранее, импортируется в локальное защищенное хранилище с помощью заданной пользователем парольной фразы. После расшифровки файла он сохраняется в новом файле, который, в свою очередь, шифруется на локальном компьютере.  
  
    `-p/securepassword -i/import {<server-id> [, ...n] | all} <encrypted-password -file>`  
  
    Несколько идентификаторов серверов можно указать с помощью разделителей-запятыми.  
  
### <a name="help-option--help"></a>Параметр справки:-?/Help  
Отображает сводку синтаксиса параметров консоли SSMA.  
  
`C:\>SSMAforSybaseConsole.EXE -?`  
  
Для табличного вывода параметров командной строки консоли SSMA см. [приложение-1 &#40;SybaseToSQL&#41;](../../ssma/sybase/appendix-1-sybasetosql.md).  
  
### <a name="securepassword-help-option--securepassword--help"></a>Параметр справки Секурепассворд:-секурепассворд-?/Help  
Отображает сводку синтаксиса параметров консоли SSMA.  
  
`C:\>SSMAforSybaseConsole.EXE -securepassword -?`  
  
Для табличного вывода параметров командной строки консоли SSMA см. [приложение 1 &#40;SybaseToSQL&#41;](../../ssma/sybase/appendix-1-sybasetosql.md)  
  
### <a name="next-step"></a>Следующий шаг  
Следующий шаг зависит от требований проекта:  
  
-   Сведения об указании пароля или экспорте и импорте паролей см. в статье [Управление паролями &#40;SybaseToSQL&#41;](../../ssma/sybase/managing-passwords-sybasetosql.md).  
  
-   Сведения о создании отчетов см. в разделе [Создание отчетов &#40;SybaseToSQL&#41;](../../ssma/sybase/generating-reports-sybasetosql.md).  
  
-   Сведения об устранении неполадок в консоли см. в разделе [Устранение неполадок &#40;SybaseToSQL&#41;](../../ssma/sybase/troubleshooting-sybasetosql.md).  
  
