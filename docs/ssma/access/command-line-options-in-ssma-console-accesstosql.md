---
title: Параметры командной строки в консоли SSMA (Акцесстоскл) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 08/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: c1f3b3f0-0f3e-4e07-b745-2fbdde85c67e
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: f6a2bb7e10e487d65c0fa8dfd406a30f9acd557a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68265527"
---
# <a name="command-line-options-in-the-ssma-console-accesstosql"></a>Параметры командной строки в консоли SSMA (Акцесстоскл)
Корпорация Майкрософт предоставляет надежный набор параметров командной строки для выполнения и управления действиями SSMA. В последующих разделах содержатся дополнительные сведения.  
  
## <a name="command-line-options-in-the-ssma-console"></a>Параметры командной строки в консоли SSMA  
Здесь описаны параметры командной консоли.  
  
В этом разделе термин "параметр" также называется "Switch".  
  
Параметры не учитывают регистр и могут начинаться с символа "**-**" или "**/**".  
  
Если указаны параметры, обязательно укажите соответствующие параметры.  
  
Параметры параметров должны отделяться пробелами от символа параметра.  
  
**Примеры синтаксиса:**  
  
`C:\> SSMAforAccessConsole.EXE -s scriptfile`  
  
`C:\> SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\VariableValueFileSample.xml" -c "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml"`  
  
Имена папок или файлов, содержащие пробелы, должны быть указаны в двойных кавычках.  
  
Выходные данные записей командной строки и сообщений об ошибках хранятся в STDOUT или в указанном файле.  
  
### <a name="script-file-option--sscript"></a>Параметр файла скрипта:-s/Script  
Обязательный параметр, путь или имя файла скрипта указывает сценарий последовательностей команд, выполняемых SSMA.  
  
**Примеры синтаксиса:**  
  
`C:\>SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"`  
  
### <a name="variable-value-file-option--vvariable"></a>Параметр файла значения переменной:-v/переменная  
Файл значения переменной состоит из переменных, используемых в файле скрипта. Параметр является необязательным. Если переменные не объявлены в файле переменных и используются в файле скрипта, приложение создает ошибку и завершает выполнение консоли.  
  
**Примеры синтаксиса:**  
  
-   Переменные, определенные в нескольких файлах значений переменных, возможно, один со значением по умолчанию, а другой — со значением, зависящим от экземпляра, если применимо. Последний файл переменной, указанный в аргументах командной строки, имеет предпочтение, если существует дублирование переменных:  
  
    `C:\>SSMAforAccessConsole.EXE -s`  
  
    `"C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml" -v c:\migration`  
  
    `projects\global_variablevaluefile.xml -v "c:\migrationprojects\instance_variablevaluefile.xml"`  
  
### <a name="server-connection-file-option--cserverconnection"></a>Параметр файла соединения сервера:-c/ServerConnection  
Этот файл содержит сведения о подключении сервера для каждого сервера. Определение каждого сервера определяется уникальным ИДЕНТИФИКАТОРом сервера. Идентификаторы серверов указываются в файле скрипта для команд, связанных с подключением.  
  
Определение сервера может быть частью файла подключения к серверу или файла скрипта. Идентификатор сервера в файле скрипта имеет приоритет над файлом соединения с сервером, в случае дублирования идентификатора сервера.  
  
**Примеры синтаксиса:**  
  
-   Идентификаторы серверов используются в файле скрипта. Они определяются в отдельном файле соединения сервера. В этом файле используются переменные, определенные в файле значений переменных:  
  
    `C:\>SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -v`  
  
    `c:\SsmaProjects\myvaluefile1.xml -c`  
  
    `c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
-   Определение сервера внедряется в файл скрипта:  
  
    `C:\>SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>Параметр вывода XML:-x/ксмлаутпут [ксмлаутпутфиле]  
Эта команда используется для вывода выходных сообщений команды в формате XML либо в консоль, либо в XML-файл.  
  
Существует два варианта, которые можно использовать для ксмлаутпут, а именно:  
  
-   Если путь к файлу указан после параметра ксмлаутпут, выходные данные перенаправляются в файл.  
  
    **Пример синтаксиса:**  
  
    `C:\>SSMAforAccessConsole.EXE -s`  
  
    `"C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -x d:\xmloutput\project1output.xml`  
  
-   Если после параметра ксмлаутпут не указан путь к файлу, ксмлаут отображается на самой консоли.  
  
    **Пример синтаксиса:**  
  
    `C:\>SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -xmloutput`  
  
### <a name="log-file-option--llog"></a>Параметр файла журнала:-l/log  
Все операции SSMA в консольном приложении записываются в файл журнала, а параметр является необязательным. Если файл журнала и его путь указаны в командной строке, то журнал создается в указанном расположении. В противном случае он создается в своем расположении по умолчанию.  
  
**Пример синтаксиса:**  
  
`C:\>SSMAforAccessConsole.EXE`  
  
`"C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option--eprojectenvironment"></a>Параметр папки среды проекта:-e/прожектенвиронмент  
Этот необязательный параметр указывает папку параметров среды проекта для текущего проекта SSMA.  
  
**Пример синтаксиса:**  
  
`C:\>SSMAforAccessConsole.EXE -s`  
  
`"C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -e c:\SsmaProjects\CommonEnvironment`  
  
||  
|-|  
||  
  
### <a name="secure-password-option--psecurepassword"></a>Параметр безопасного пароля:-p/секурепассворд  
Этот параметр указывает зашифрованный пароль для подключений к серверу. Он отличается от всех остальных параметров тем, что он не выполняет какой-либо сценарий или справку в действиях, связанных с миграцией, но помогает управлять шифрованием паролей для подключений к серверу, используемых в проекте миграции.  
  
В качестве параметра командной строки нельзя вводить другие параметры или пароли. В противном случае возникает ошибка. Дополнительные сведения см. в разделе [Управление паролями](managing-passwords-accesstosql.md) .  
  
Поддерживаются следующие подкоманды `-p/securepassword`:  
  
-   Для добавления пароля или обновления существующего пароля в защищенном хранилище с указанным ИДЕНТИФИКАТОРом сервера или для всех идентификаторов серверов, определенных в файле подключения к серверу:  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
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
  
`C:\>SSMAforAccessConsole.EXE -?`  
  
Для табличного вывода параметров командной строки консоли SSMA см. [приложение-1 &#40;акцесстоскл&#41;](../../ssma/access/appendix-1-accesstosql.md).  
  
### <a name="securepassword-help-option--securepassword--help"></a>Параметр справки Секурепассворд:-секурепассворд-?/Help  
Отображает сводку синтаксиса параметров консоли SSMA.  
  
`C:\>SSMAforAccessConsole.EXE -securepassword -?`  
  
Для табличного вывода параметров командной строки консоли SSMA см. [приложение 1 &#40;акцесстоскл&#41;](../../ssma/access/appendix-1-accesstosql.md)  
  
### <a name="next-steps"></a>Дальнейшие действия  
Следующий шаг зависит от требований проекта:  
  
1.  Сведения об указании пароля или экспорте и импорте паролей см. в статье [Управление паролями &#40;акцесстоскл&#41;](../../ssma/access/managing-passwords-accesstosql.md).  
  
2.  Сведения о создании отчетов см. в разделе [Создание отчетов &#40;акцесстоскл&#41;](../../ssma/access/generating-reports-accesstosql.md).  
  
3.  Сведения об устранении неполадок в консоли см. в разделе [Устранение неполадок &#40;акцесстоскл&#41;](../../ssma/access/troubleshooting-accesstosql.md).  
  
