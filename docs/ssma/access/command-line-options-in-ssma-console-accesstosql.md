---
title: Параметры командной строки в консоли SSMA (AccessToSQL) | Документация Майкрософт
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
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265527"
---
# <a name="command-line-options-in-the-ssma-console-accesstosql"></a>Параметры командной строки в консоли SSMA (AccessToSQL)
Майкрософт предоставляет широкий набор параметров командной строки для выполнения и SSMA действия управления. Последующих разделах приведены дополнительные сведения.  
  
## <a name="command-line-options-in-the-ssma-console"></a>Параметры командной строки в консоли SSMA  
Описанные здесь, параметры команд консоли.  
  
В этом разделе термин «параметр» также называется «switch».  
  
Параметры не учитывают регистр и может начинаться с " **-** «или» **/** " символов.  
  
Если указаны параметры, это обязательно, что можно указать соответствующие параметры.  
  
Параметры должны быть разделены параметр символов пробелов.  
  
**Примеры синтаксиса.**  
  
`C:\> SSMAforAccessConsole.EXE -s scriptfile`  
  
`C:\> SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\VariableValueFileSample.xml" -c "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml"`  
  
Имена файла или папки, содержащие пробелы должны указываться в двойные кавычки.  
  
Выходные данные командной строки операции и сообщения об ошибках хранится в STDOUT, или в указанном файле.  
  
### <a name="script-file-option--sscript"></a>Параметр файла скрипта: -s или сценарий  
Обязательный параметр, путь и имя файла скрипта указывает сценарий из последовательностей команд, который будет выполнен задачей SSMA.  
  
**Примеры синтаксиса.**  
  
`C:\>SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"`  
  
### <a name="variable-value-file-option--vvariable"></a>Параметр file значение переменной: - v или переменная  
Значение переменной файл состоит из переменных, используемых в файле скрипта. Параметр является необязательным. Если переменные не объявляются в файле переменных и использовать в файле скрипта, приложение выдает ошибку и прекращает выполнение консоли.  
  
**Примеры синтаксиса.**  
  
-   Переменные, определенные в нескольких файлах значение переменной, возможно, один со значением по умолчанию, а другой со значением данного экземпляра, если применимо. Последний переменной файл, указанный в аргументах командной строки принимает приоритет, в случае дублирования переменных:  
  
    `C:\>SSMAforAccessConsole.EXE -s`  
  
    `"C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml" -v c:\migration`  
  
    `projects\global_variablevaluefile.xml -v "c:\migrationprojects\instance_variablevaluefile.xml"`  
  
### <a name="server-connection-file-option--cserverconnection"></a>Параметр файла подключения сервера: - c/serverconnection  
Этот файл содержит сведения о подключении сервера для каждого сервера. Определение каждого сервера идентифицируемый уникальный идентификатор сервера. Идентификаторы Server указываются в файле скрипта для команды, относящиеся к соединению.  
  
Определение сервера может быть частью файла подключения сервера и/или файл скрипта. Идентификатор сервера в файле сценария имеет приоритет над файле подключения сервера, в случае дублирования идентификатор сервера.  
  
**Примеры синтаксиса.**  
  
-   Server идентификаторы используются в файле скрипта. Они определяются в файле подключения отдельный сервер. Этот файл использует переменные, определенные в файле значение переменной:  
  
    `C:\>SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -v`  
  
    `c:\SsmaProjects\myvaluefile1.xml -c`  
  
    `c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
-   Определение сервера внедряется в файле сценария:  
  
    `C:\>SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>Формат вывода XML: - x / xmloutput [xmloutputfile]  
Эта команда используется для вывода команды исходящие сообщения в формате xml на консоль или в XML-файл.  
  
Доступны два варианта для xmloutput, а именно:  
  
-   Если после параметра xmloutput путь к файлу, Вывод перенаправляется в файл.  
  
    **Пример синтаксиса:**  
  
    `C:\>SSMAforAccessConsole.EXE -s`  
  
    `"C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -x d:\xmloutput\project1output.xml`  
  
-   Если после параметра xmloutput не filepath, xmlout отображается на самой консоли.  
  
    **Пример синтаксиса:**  
  
    `C:\>SSMAforAccessConsole.EXE -s "C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -xmloutput`  
  
### <a name="log-file-option--llog"></a>Параметр файла журнала: -l/log  
В файл журнала записываются все операции SSMA в консольном приложении, и параметр является необязательным. Если файл журнала и пути указаны в командной строке, журнала создается в указанном расположении. В противном случае он возвращает создан в расположении по умолчанию.  
  
**Пример синтаксиса:**  
  
`C:\>SSMAforAccessConsole.EXE`  
  
`"C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option--eprojectenvironment"></a>Параметр среды папку проекта: -e/projectenvironment  
Этот необязательный параметр обозначает папке проекта среда параметры для текущего проекта SSMA.  
  
**Пример синтаксиса:**  
  
`C:\>SSMAforAccessConsole.EXE -s`  
  
`"C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml"  -e c:\SsmaProjects\CommonEnvironment`  
  
||  
|-|  
||  
  
### <a name="secure-password-option--psecurepassword"></a>Защита параметр password: -p/securepassword  
Этот параметр указывает зашифрованный пароль для соединения с сервером. Он отличается от других параметров, в том, что он не выполнить любой скрипт или справки в любых действиях, связанные с миграцией, но помогает управлять шифрование пароля для соединения сервера, используемые в проекте миграции.  
  
Невозможно ввести любой параметр или пароль в качестве параметра командной строки. В противном случае он приводит к ошибке. Дополнительные сведения см. в разделе [управление паролями](managing-passwords-accesstosql.md) раздел.  
  
Поддерживаются следующие подпараметров `-p/securepassword`:  
  
-   Чтобы добавить пароль, или обновить существующий пароль, к защищенному хранилищу для указанного ИД сервера или для всех идентификаторов серверов, определенные в файле подключения сервера:  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-s|-script <server-connection-file> [-v|variable <variable-value-file>] [-o|overwrite]`  
  
-   Чтобы удалить зашифрованный пароль из защищенного хранилища указанного идентификатора сервера, или для всех идентификаторов серверов:  
  
    `-p/securepassword -r/remove {<server_id> [, ...n] | all}`  
  
-   Чтобы отобразить список идентификаторов серверов, для которого шифруется пароль:  
  
    `-p/securepassword -l/list`  
  
-   Чтобы экспортировать паролей, хранящихся в защищенном хранилище для зашифрованного файла. Этот файл шифруется с помощью пользовательской парольную фразу.  
  
    `-p/securepassword -e/export {<server-id> [, ...n] | all} <encrypted-password -file>`  
  
-   Шифрование файл, экспортированный ранее импортируется в локальное хранилище защищенных, с помощью пользовательской парольную фразу. После расшифровки файл сохраняется в новом файле, который, в свою очередь, зашифрован на локальном компьютере.  
  
    `-p/securepassword -i/import {<server-id> [, ...n] | all} <encrypted-password -file>`  
  
    Можно указать несколько идентификаторов серверов при помощи запятые разделители.  
  
### <a name="help-option--help"></a>Help-параметр:-? / Help  
Отображает сводку синтаксиса параметров консоли SSMA:  
  
`C:\>SSMAforAccessConsole.EXE -?`  
  
Табличного отображения команд консоли SSMA параметров командной строки, см. в разделе [приложение 1 &#40;AccessToSQL&#41;](../../ssma/access/appendix-1-accesstosql.md).  
  
### <a name="securepassword-help-option--securepassword--help"></a>Параметр справки SecurePassword: - securepassword-? / Help  
Отображает сводку синтаксиса параметров консоли SSMA:  
  
`C:\>SSMAforAccessConsole.EXE -securepassword -?`  
  
Табличного отображения команд консоли SSMA параметров командной строки, см. в разделе [приложение 1 &#40;AccessToSQL&#41;](../../ssma/access/appendix-1-accesstosql.md)  
  
### <a name="next-steps"></a>Следующие шаги  
Следующий шаг зависит от требований проекта:  
  
1.  Для указания пароля или экспорта / импорта пароли, см. в разделе [управление паролями &#40;AccessToSQL&#41;](../../ssma/access/managing-passwords-accesstosql.md).  
  
2.  Для создания отчетов, см. в разделе [Создание отчеты &#40;AccessToSQL&#41;](../../ssma/access/generating-reports-accesstosql.md).  
  
3.  Для устранения неполадок в консоли, см. в разделе [Устранение неполадок &#40;AccessToSQL&#41;](../../ssma/access/troubleshooting-accesstosql.md).  
  
