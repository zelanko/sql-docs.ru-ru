---
title: "Параметры командной строки в консоли SSMA (AccessToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 08/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: c1f3b3f0-0f3e-4e07-b745-2fbdde85c67e
caps.latest.revision: 11
author: Shamikg
ms.author: Shamikg
manager: murato
ms.translationtype: MT
ms.sourcegitcommit: 80642503480add90fc75573338760ab86139694c
ms.openlocfilehash: 827257d90042aa1655545edd9fc20d114952f426
ms.contentlocale: ru-ru
ms.lasthandoff: 08/21/2017

---
# <a name="command-line-options-in-the-ssma-console-accesstosql"></a>Параметры командной строки в консоли SSMA (AccessToSQL)
Майкрософт предоставляет широкий набор параметров командной строки для выполнения и контроля над SSMA действий. В дальнейших разделах содержатся дополнительные сведения.  
  
## <a name="command-line-options-in-the-ssma-console"></a>Параметры командной строки в консоли SSMA  
Описанные здесь, являются консоль параметры командной строки.  
  
В данном разделе термин «параметр» также называется «переключатель».  
  
Параметры не учитывают регистр и могут начинаться с "**-**«или»**/**" символов.  
  
Если указаны параметры, это обязательно указывать соответствующие параметры.  
  
Параметры должны быть разделены от символа параметр пробелы.  
  
**Примеры синтаксиса.**  
  
`C:\> SSMAforAccessConsole.EXE -s scriptfile`  
  
`C:\> SSMAforAccessConsole.EXE -s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml” –v “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\VariableValueFileSample.xml” –c “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml”`  
  
Имена файла или папки, содержащие пробелы должно быть указано в двойные кавычки.  
  
Выходные данные операции командной строки и сообщения об ошибках хранится в STDOUT или в указанный файл.  
  
### <a name="script-file-option-sscript"></a>Параметр файла скрипта: – s исполняемых файлов и сценариев  
Обязательный параметр, путь и имя файла скрипта указывает сценарий последовательности команд для выполнения SSMA.  
  
**Примеры синтаксиса.**  
  
`C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="variable-value-file-option-vvariable"></a>Параметр file значение переменной: – v или переменная  
Файл имя переменной состоит из переменных, используемых в файле скрипта. Параметр является необязательным. Если переменные, объявленные в файле переменных и не используются в файле скрипта, приложение выдает ошибку и прекращает выполнение консоли.  
  
**Примеры синтаксиса.**  
  
-   Переменные, определенные в нескольких файлах значение переменной может быть один со значением по умолчанию, а другой со значением данного экземпляра, если применимо. Последней переменной файл, указанный в аргументах командной строки принимает предпочтений, при наличии дубликатов переменных:  
  
    `C:\>SSMAforAccessConsole.EXE -s`  
  
    `“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml” –v c:\migration`  
  
    `projects\global_variablevaluefile.xml –v “c:\migrationprojects\instance_variablevaluefile.xml”`  
  
### <a name="server-connection-file-option-cserverconnection"></a>Параметр файла подключения сервера:-c или serverconnection  
Этот файл содержит сведения о подключении сервера для каждого сервера. Определение каждого сервера определяется уникальный идентификатор сервера. Идентификаторы серверов указываются в файле скрипта для команды, относящиеся к соединению.  
  
Определение сервера может быть частью файла подключения сервера или файла скрипта. Идентификатор сервера в файле скрипта имеет приоритет над файл подключения сервера, в случае, если есть дублирующиеся идентификатор сервера.  
  
**Примеры синтаксиса.**  
  
-   Сервер идентификаторы используются в файле скрипта. Они определяются в файле подключения отдельный сервер. Этот файл использует переменные, определенные в файле значение переменной:  
  
    `C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –v`  
  
    `c:\SsmaProjects\myvaluefile1.xml –c`  
  
    `c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
-   Определение сервера внедряется в файле сценария:  
  
    `C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>Формат вывода XML: - x / xmloutput [xmloutputfile]  
Эта команда используется для вывода выходных сообщений команды в формате xml на консоль или в XML-файл.  
  
Доступны два варианта для xmloutput, а именно:  
  
-   Если после параметра xmloutput путь к файлу, Вывод перенаправляется в файл.  
  
    **Пример синтаксиса:**  
  
    `C:\>SSMAforAccessConsole.EXE –s`  
  
    `“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –x d:\xmloutput\project1output.xml`  
  
-   Если после параметра xmloutput не filepath, xmlout отображается на самой консоли.  
  
    **Пример синтаксиса:**  
  
    `C:\>SSMAforAccessConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –xmloutput`  
  
### <a name="log-file-option-llog"></a>Параметр файла журнала: – l или журнала  
В файл журнала записываются все операции SSMA в консольном приложении, и параметр является необязательным. Если файл журнала и пути указаны в командной строке, журнал возвращает создается в указанном расположении. В противном случае он возвращает сформирован в расположение по умолчанию.  
  
**Пример синтаксиса:**  
  
`C:\>SSMAforAccessConsole.EXE`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option-eprojectenvironment"></a>Проект среды папку параметр: – e-projectenvironment  
Этот необязательный параметр указывает параметры папки проекта среды для текущего проекта SSMA.  
  
**Пример синтаксиса:**  
  
`C:\>SSMAforAccessConsole.EXE –s`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –e c:\SsmaProjects\CommonEnvironment`  
  
||  
|-|  
||  
  
### <a name="secure-password-option-psecurepassword"></a>Безопаснее пароля: – p/securepassword  
Этот параметр указывает зашифрованный пароль для подключения к серверу. Он отличается от других параметров, в том, что выполнение любой сценарий или не помогают в любые действия, связанные с миграцией, но помогает управлять шифрованием пароля для подключения сервера, используемый в проекте миграции.  
  
Любой параметр или пароль невозможно ввести в качестве параметра командной строки. В противном случае он приводит к ошибке. Дополнительные сведения см. в разделе [управление паролями](http://msdn.microsoft.com/b099d0f9-dd37-4c87-8b6f-ed0177881ea4) раздела.  
  
Поддерживаются следующие подпункты `–p/securepassword`:  
  
-   Чтобы добавить пароль или обновить существующий пароль, чтобы защищенного хранилища для указанного идентификатора сервера или все идентификаторы серверов, определенные в файле подключения сервера:  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
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
  
### <a name="help-option-help"></a>Help-параметр:-? / Help  
Отображает сводку синтаксиса параметров консоли SSMA:  
  
`C:\>SSMAforAccessConsole.EXE -?`  
  
Отображаемой консоли SSMA параметров командной строки см. в разделе [приложение - 1 &#40; AccessToSQL &#41; ](../../ssma/access/appendix-1-accesstosql.md).  
  
### <a name="securepassword-help-option-securepassword--help"></a>Параметр справки SecurePassword: – securepassword-? / Help  
Отображает сводку синтаксиса параметров консоли SSMA:  
  
`C:\>SSMAforAccessConsole.EXE -securepassword -?`  
  
Отображаемой консоли SSMA параметров командной строки см. в разделе [приложение - 1 &#40; AccessToSQL &#41;](../../ssma/access/appendix-1-accesstosql.md)  
  
### <a name="next-steps"></a>Следующие шаги  
Следующий шаг зависит от требований проекта:  
  
1.  Для указания пароля или экспорта / импорта паролей см. в разделе [управление паролями &#40; AccessToSQL &#41; ](../../ssma/access/managing-passwords-accesstosql.md).  
  
2.  Для создания отчетов, в разделе [создания отчетами &#40; AccessToSQL &#41; ](../../ssma/access/generating-reports-accesstosql.md).  
  
3.  Для устранения неполадок в консоли, в разделе [Устранение неполадок &#40; AccessToSQL &#41; ](../../ssma/access/troubleshooting-accesstosql.md).  
  

