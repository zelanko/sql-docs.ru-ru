---
title: Параметры командной строки в консоли SSMA (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Command Line Options
ms.assetid: 337cbd26-67b7-4c88-9deb-d0a69a3d7714
caps.latest.revision: 11
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8eb96fb924a26d691db1ba6577d0b6f9c93e49ee
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="command-line-options-in-ssma-console-sybasetosql"></a>Параметры командной строки в консоли SSMA (SybaseToSQL)
Майкрософт предоставляет широкий набор параметров командной строки для выполнения и контроля над SSMA действий. В последующих разделах подробно одинаковыми.  
  
## <a name="command-line-options-in-ssma-console"></a>Параметры командной строки в консоли SSMA  
Описанные здесь, являются консоль параметры командной строки.  
  
В данном разделе термин «параметр» также называется «переключатель».  
  
-   Параметры не учитывают регистр и могут начинаться с "**-**«или»**/**" символов.  
  
-   Если параметры заданы, становится требуется указать соответствующие параметры.  
  
-   Параметры должны быть разделены от символа параметр пробелы.  
  
    **Примеры синтаксиса.**  
  
    `C:\> SSMAforSybaseConsole.EXE -s scriptfile`  
  
    `C:\> SSMAforSybaseConsole.EXE -s “C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\AssessmentReportGenerationSample.xml” –v “C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\VariableValueFileSample.xml” –c “C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ServersConnectionFileSample.xml”`  
  
-   Имена файла или папки, содержащие пробелы должно быть указано в двойные кавычки.  
  
-   Выходные данные операции командной строки и сообщения об ошибках, хранятся в STDOUT или в указанный файл.  
  
### <a name="script-file-option-sscript"></a>Параметр файла сценария: – s или сценарий  
Обязательный параметр, путь и имя файла скрипта указывает сценарий последовательности команд для выполнения SSMA.  
  
**Примеры синтаксиса.**  
  
`C:\>SSMAforSybaseConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="variable-value-file-option-vvariable"></a>Параметр File переменной значение: – v или переменная  
Этот файл состоит из переменных, используемых в файле скрипта. Это необязательный параметр. Если переменные, объявленные в файле переменных и не используются в файле скрипта, приложение выдает ошибку и прекращает выполнение консоли.  
  
**Примеры синтаксиса.**  
  
-   Переменные, определенные в нескольких файлах значение переменной может быть одно значение по умолчанию и другой экземпляр конкретное значение, если применимо. Последний файл переменной указаны в аргументах командной строки принимает предпочтений, при наличии дубликатов переменных:  
  
    `C:\>SSMAforSybaseConsole.EXE -s`  
  
    `“C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml” –v c:\migration`  
  
    `projects\global_variablevaluefile.xml –v “c:\migrationprojects\instance_variablevaluefile.xml”`  
  
### <a name="server-connection-file-option-cserverconnection"></a>Параметр файла подключения сервера:-c или serverconnection  
Этот файл содержит сведения о подключении сервера для каждого сервера. Определение каждого сервера определяется уникальный идентификатор сервера. Идентификаторы сервера имеются ссылки в файле скрипта для соединения, связанных с командами.  
  
Определение сервера может быть частью файла подключения сервера или файла скрипта. Идентификатор сервера в файле скрипта имеет приоритет над файл подключения сервера, в случае, если есть дублирующиеся идентификатор сервера.  
  
**Примеры синтаксиса.**  
  
-   Сервер идентификаторы используются в файле скрипта и они определены в файле подключения отдельный сервер, файл подключения сервера использует переменные, которые определены в файле значение переменной:  
  
    `C:\>SSMAforSybaseConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –v`  
  
    `c:\SsmaProjects\myvaluefile1.xml –c`  
  
    `c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
-   Определение сервера внедряется в файле сценария:  
  
    `C:\>SSMAforSybaseConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>Формат вывода XML: - x / xmloutput [xmloutputfile]  
Эта команда используется для вывода выходных сообщений команды в формате xml на консоль или в XML-файл.  
  
Существует два варианта для xmloutput, viz..,:  
  
-   Если путь к файлу указан после параметра xmloutput выходные данные перенаправляется в файл.  
  
    **Пример синтаксиса:**  
  
    `C:\>SSMAforSybaseConsole.EXE –s`  
  
    `“C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –x d:\xmloutput\project1output.xml`  
  
-   Если нет filepath предоставляется после переключения xmloutput xmlout отображается на самой консоли.  
  
    **Пример синтаксиса:**  
  
    `C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –xmloutput`  
  
### <a name="log-file-option-llog"></a>Параметр файла журнала: – l или журнала  
Все операции в консольном приложении SSMA получить записываются в файл журнала. Это необязательный параметр. Если файл журнала и пути указаны в командной строке, журнал возвращает создается в указанном расположении. В противном случае он возвращает сформирован в расположение по умолчанию.  
  
**Пример синтаксиса:**  
  
`C:\>SSMAforSybaseConsole.EXE`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option-eprojectenvironment"></a>Параметр папки проекта среды: – e-projectenvironment  
Эта ошибка означает параметры папки проекта среды для текущего проекта SSMA. Этот параметр является необязательным.  
  
**Пример синтаксиса:**  
  
`C:\>SSMAforSybaseConsole.EXE –s`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –e c:\SsmaProjects\CommonEnvironment`  
  
### <a name="secure-password-option-psecurepassword"></a>Безопасный вариант пароль: – p/securepassword  
Этот параметр указывает зашифрованный пароль для подключения к серверу. Она отличается от других параметров: параметр не выполняет любой скрипт и не помогает в любые действия, связанные с миграцией, но помогает управлять шифрованием пароля для подключения сервера, используемый в проекте миграции.  
  
Любой параметр или пароль невозможно ввести в качестве параметра командной строки. В противном случае он приводит к ошибке. Дополнительные сведения см. в [управление паролями](http://msdn.microsoft.com/en-us/9b6a70f9-6840-4140-a059-bb7bd7ccc67c) раздела.  
  
Поддерживаются следующие вложенные функции `–p/securepassword`:  
  
-   Чтобы добавить пароль в защищенное хранилище для указанного идентификатора сервера или для всех идентификаторов сервера, определенные в файле соединения сервера. Перезаписать параметр ниже обновления пароль, если он уже существует:  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}` `-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-s|-script <server-connection-file> [-v|variable <variable-value-file>] [-o|overwrite]`  
  
-   Чтобы удалить зашифрованный пароль из защищенного хранилища указанного идентификатора сервера или все идентификаторы сервера:  
  
    `–p/securepassword –r/remove {<server_id> [, …n] | all}`  
  
-   Чтобы отобразить список идентификаторов сервера, для которого шифруется пароль:  
  
    `–p/securepassword –l/list`  
  
-   Экспорт пароли, сохраненные в защищенное хранилище для зашифрованного файла. Этот файл защищен определяемый пользователем парольную фразу.  
  
    `–p/securepassword –e/export {<server-id> [, …n] | all} <encrypted-password -file>`  
  
-   Шифрование файл, экспортированный ранее импортируется в локальном защищенное хранилище, с помощью пользовательской парольную фразу. После расшифровки файл сохраняется в новом файле, который в свою очередь, шифруется на локальном компьютере.  
  
    `–p/securepassword –i/import {<server-id> [, …n] | all} <encrypted-password -file>`  
  
    Можно указать несколько идентификаторов сервера при помощи запятые разделители.  
  
### <a name="help-option-help"></a>Параметр справки: –? / Help  
Отображает сводку синтаксиса параметров консоли SSMA:  
  
`C:\>SSMAforSybaseConsole.EXE -?`  
  
Табличного отображения консоли SSMA параметры командной строки, см. в разделе [приложение - 1 &#40; SybaseToSQL &#41; ](../../ssma/sybase/appendix-1-sybasetosql.md).  
  
### <a name="securepassword-help-option-securepassword--help"></a>Параметр справки SecurePassword: – securepassword-? / Help  
Отображает сводку синтаксиса параметров консоли SSMA:  
  
`C:\>SSMAforSybaseConsole.EXE -securepassword -?`  
  
Табличного отображения консоли SSMA параметры командной строки, см. в разделе [приложение - 1 &#40; SybaseToSQL &#41;](../../ssma/sybase/appendix-1-sybasetosql.md)  
  
### <a name="next-step"></a>Следующий шаг  
Следующий шаг зависит от требований проекта:  
  
-   Для указания пароля или экспорта / импорта паролей см. в разделе [управление паролями &#40; SybaseToSQL &#41; ](../../ssma/sybase/managing-passwords-sybasetosql.md).  
  
-   Для создания отчетов, в разделе [создания отчетами &#40; SybaseToSQL &#41; ](../../ssma/sybase/generating-reports-sybasetosql.md).  
  
-   Для устранения неполадок в консоли, в разделе [Устранение неполадок &#40; SybaseToSQL &#41; ](../../ssma/sybase/troubleshooting-sybasetosql.md).  
  
