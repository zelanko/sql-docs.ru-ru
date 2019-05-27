---
title: Параметры командной строки в консоли SSMA (DB2ToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 237354e9-25c4-4386-9d1f-ca0618d4a9a0
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: de41d864b6bfd8e7fe80188b69b50e2592d6cf16
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63453409"
---
# <a name="command-line-options-in-ssma-console-db2tosql"></a>Параметры командной строки в консоли SSMA (DB2ToSQL)
Майкрософт предоставляет надежные параметры командной строки для выполнения и SSMA действия управления. В последующих разделах подробно описано же.  
  
## <a name="command-line-options-in-ssma-console"></a>Параметры командной строки в консоли SSMA  
Описанные здесь, параметры команд консоли.  
  
В этом разделе термин «параметр» также называется «switch».  
  
Параметры не учитывают регистр и может начинаться с " **-** «или» **/** " символов.  
  
Если указаны параметры, он становится обязательно укажите соответствующие параметры.  
  
Параметры должны быть разделены параметр символов пробелов.  
  
**Примеры синтаксиса.**  
  
`C:\> SSMAforDB2Console.EXE -s scriptfile`  
  
`C:\> SSMAforDB2Console.EXE -s "C Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \AssessmentReportGenerationSample.xml" -v "C Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \VariableValueFileSample.xml" -c "C Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ServersConnectionFileSample.xml"`  
  
Имена файла или папки, содержащие пробелы должны указываться в двойные кавычки.  
  
Выходные данные операции командной строки и сообщения об ошибках, хранятся в STDOUT, или в указанном файле.  
  
### <a name="script-file-option--sscript"></a>Параметр файла скрипта: -s или сценарий  
Обязательный параметр, путь и имя файла скрипта указывает сценарий из последовательностей команд, который будет выполнен задачей SSMA.  
  
**Примеры синтаксиса.**  
  
`C:\>SSMAforDB2Console.EXE -s "C Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml"`  
  
### <a name="variable-value-file-option--vvariable"></a>Переменной параметр File значение: - v или переменная  
Этот файл содержит переменные, используемые в файле скрипта. Это необязательный параметр. Если переменные не объявляются в файле переменных и использовать в файле скрипта, приложение выдает ошибку и прекращает выполнение консоли.  
  
**Примеры синтаксиса.**  
  
-   Переменные, определенные в нескольких файлах значение переменной, возможно, один со значением по умолчанию, а другой с экземпляра конкретное значение, если это применимо. Последний файл переменных, указанные в аргументах командной строки принимает приоритет, в случае дублирования переменных:  
  
    `C:\>SSMAforDB2Console.EXE -s`  
  
    `"C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml" -v c:\migration`  
  
    `projects\global_variablevaluefile.xml -v "c:\migrationprojects\instance_variablevaluefile.xml"`  
  
### <a name="server-connection-file-option--cserverconnection"></a>Параметр файла подключения сервера: -c/serverconnection  
Этот файл содержит сведения о подключении сервера для каждого сервера. Определение каждого сервера идентифицируемый уникальный идентификатор сервера. Идентификаторы Server указываются в файле скрипта для подключения команд, связанных с.  
  
Определение сервера может быть частью файла подключения сервера и/или файл скрипта. Идентификатор сервера в файле сценария имеет приоритет над файле подключения сервера, в случае дублирования идентификатор сервера.  
  
**Примеры синтаксиса.**  
  
-   Server идентификаторы используются в файле скрипта и они определены в файле подключения отдельный сервер, файл подключения сервера использует переменные, которые определены в файле значение переменной:  
  
    `C:\>SSMAforDB2Console.EXE -s "C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml"  -v`  
  
    `c:\SsmaProjects\myvaluefile1.xml -c`  
  
    `c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
-   Определение сервера внедряется в файле сценария:  
  
    `C:\>SSMAforDB2Console.EXE -s "C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml"`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>Формат вывода XML: - x / xmloutput [xmloutputfile]  
Эта команда используется для вывода команды исходящие сообщения в формате xml на консоль или в XML-файл.  
  
Существует два варианта для xmloutput, находящие отклик у..,:  
  
-   Если путь к файлу предоставляется после переключения xmloutput Вывод перенаправляется в файл.  
  
    **Пример синтаксиса:**  
  
    `C:\>SSMAforDB2Console.EXE -s`  
  
    `"C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml"  -x d:\xmloutput\project1output.xml`  
  
-   Если нет путь к файлу предоставляется после переключения xmloutput xmlout отображается на самой консоли.  
  
    **Пример синтаксиса:**  
  
    `C:\>SSMAforDB2Console.EXE -s "C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml"  -xmloutput`  
  
### <a name="log-file-option--llog"></a>Параметр файла журнала: -l/log  
Все операции SSMA в консольном приложении будут сохранены в файле журнала. Это необязательный параметр. Если файл журнала и пути указаны в командной строке, журнала создается в указанном расположении. В противном случае он возвращает создан в расположении по умолчанию.  
  
**Пример синтаксиса:**  
  
`C:\>SSMAforDB2Console.EXE`  
  
`"C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml"  -l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option--eprojectenvironment"></a>Параметр папки проекта среды: -e/projectenvironment  
Эта ошибка означает папке проекта среда параметры для текущего проекта SSMA. Этот параметр является необязательным.  
  
**Пример синтаксиса:**  
  
`C:\>SSMAforDB2Console.EXE -s`  
  
`"C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml"  -e c:\SsmaProjects\CommonEnvironment`  
  
### <a name="secure-password-option--psecurepassword"></a>Безопасный вариант пароля: -p/securepassword  
Этот параметр указывает зашифрованный пароль для соединения с сервером. Он отличается от всех других вариантов: параметр не выполняет все сценарии и не помогает в любых действиях, связанные с миграцией, но помогает управлять шифрование пароля для соединения сервера, используемые в проекте миграции.  
  
Невозможно ввести любой параметр или пароль в качестве параметра командной строки. В противном случае он приводит к ошибке. Дополнительные сведения см. [управление паролями](https://msdn.microsoft.com/56d546e3-8747-4169-aace-693302667e94) раздел.  
  
Следующие вложенные параметры поддерживаются для `-p/securepassword`:  
  
-   Чтобы добавить пароль к защищенное хранилище для указанного ИД сервера или для всех идентификаторов серверов, определенные в файле подключения сервера. Перезаписать параметр обновления, представленные ниже, пароль, если он уже существует:  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}` `-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
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
  
### <a name="help-option--help"></a>Параметр справки:-? / Help  
Отображает сводку синтаксиса параметров консоли SSMA:  
  
`C:\>SSMAforDB2Console.EXE -?`  
  
Табличного отображения команд консоли SSMA параметры командной строки, см. в разделе [приложение 1 &#40;DB2ToSQL&#41;](../../ssma/db2/appendix-1-db2tosql.md).  
  
### <a name="securepassword-help-option--securepassword--help"></a>Параметр справки SecurePassword: - securepassword-? / Help  
Отображает сводку синтаксиса параметров консоли SSMA:  
  
`C:\>SSMAforDB2Console.EXE -securepassword -?`  
  
Табличного отображения команд консоли SSMA параметры командной строки, см. в разделе [приложение 1 &#40;DB2ToSQL&#41;](../../ssma/db2/appendix-1-db2tosql.md)  
  
### <a name="next-step"></a>Следующий шаг  
Следующий шаг зависит от требований проекта:  
  
1.  Для указания пароля или экспорта / импорта пароли, см. в разделе [управление паролями &#40;DB2ToSQL&#41;](../../ssma/db2/managing-passwords-db2tosql.md).  
  
2.  Для создания отчетов, см. в разделе [Создание отчеты &#40;DB2ToSQL&#41;](../../ssma/db2/generating-reports-db2tosql.md).  
  
3.  Для устранения неполадок в консоли, см. в разделе [Устранение неполадок &#40;DB2ToSQL&#41;](../../ssma/db2/troubleshooting-db2tosql.md).  
  
