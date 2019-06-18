---
title: Указания по программированию (драйвер ODBC для SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 01/12/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 45d1fc9d06dd814e4ee6d80ec5ecbbe9e58d09c3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66798751"
---
# <a name="programming-guidelines"></a>Указания по программированию

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Функции программирования [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на платформах macOS и Linux основаны на ODBC в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ([SQL Server Native Client (ODBC)](https://go.microsoft.com/fwlink/?LinkID=134151)). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client основан на ODBC в компонентах доступа к данным Windows DAC ([Справочник по программированию ODBC](https://go.microsoft.com/fwlink/?LinkID=45250)).  

Приложение ODBC может использовать множественные активные результирующие наборы (MARS) и другие функции, характерные для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], путем включения `/usr/local/include/msodbcsql.h` после включения заголовков unixODBC (`sql.h`, `sqlext.h`, `sqltypes.h` и `sqlucode.h`). Затем используйте те же символьные имена для элементов, связанных с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], которые вы бы стали использовать в приложениях ODBC Windows.

## <a name="available-features"></a>Доступные функции  
Следующие разделы документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client для ODBC ([SQL Server Native Client (ODBC)](https://go.microsoft.com/fwlink/?LinkID=134151)) применяются при использовании драйвера ODBC в macOS и Linux:  

-   [Взаимодействие с SQL Server (ODBC)](https://msdn.microsoft.com/library/ms131692.aspx)  
-   [Поддержка времени ожидания соединения и запроса](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
-   [Курсоры](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
-   [Улучшенная обработка даты и времени (ODBC)](https://msdn.microsoft.com/library/bb677319.aspx)  
-   [Выполнение запросов (ODBC)](https://msdn.microsoft.com/library/ms131677.aspx)  
-   [Обработка ошибок и сообщений](../../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
-   [Проверка подлинности Kerberos](../../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md)  
-   [Определяемые пользователем типы данных больших значений CLR (ODBC)](https://msdn.microsoft.com/library/bb677316.aspx)  
-   [Выполнение транзакций (ODBC) (за исключением распределенных транзакций)](https://msdn.microsoft.com/library/ms131706.aspx)  
-   [Обработка результатов (ODBC)](https://msdn.microsoft.com/library/ms130812.aspx)  
-   [Выполнение хранимых процедур](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)
-   [Поддержка разреженных столбцов (ODBC)](https://msdn.microsoft.com/library/cc280357.aspx)
-   [SSL-шифрование](../../../relational-databases/native-client/features/using-encryption-without-validation.md)
-   [Возвращающие табличные значения параметры](https://docs.microsoft.com/sql/relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc)
-   [UTF-8 и UTF-16 для команд и API данных](https://msdn.microsoft.com/library/ff878241.aspx)
-   [Использование функций каталога](../../../relational-databases/native-client/odbc/using-catalog-functions.md)  

## <a name="unsupported-features"></a>Неподдерживаемые функции

Правильность работы следующих функций в этой версии драйвера ODBC не была проверена на платформах macOS и Linux:

-   Подключение к отказоустойчивому кластеру
-   [Разрешение IP-адресов прозрачной сети](https://docs.microsoft.com/sql/connect/odbc/linux/using-transparent-network-ip-resolution) (до версии 17 драйвера ODBC)
-   [Расширенная трассировка драйвера](https://blogs.msdn.microsoft.com/mattn/2012/05/15/enabling-advanced-driver-tracing-for-the-sql-native-client-odbc-drivers/)

Следующие функции недоступны в этой версии драйвера ODBC на платформах macOS и Linux: 

-   Распределенные транзакции (атрибут SQL_ATTR_ENLIST_IN_DTC не поддерживается)  
-   Зеркальное отображение базы данных  
-   FILESTREAM  
-   Профилирование производительности драйвера ODBC, рассматриваемое в статье [SQLSetConnectAttr](https://go.microsoft.com/fwlink/?LinkId=234099), и следующие атрибуты соединения, связанные с производительностью:  
    -   SQL_COPT_SS_PERF_DATA  
    -   SQL_COPT_SS_PERF_DATA_LOG  
    -   SQL_COPT_SS_PERF_DATA_LOG_NOW  
    -   SQL_COPT_SS_PERF_QUERY  
    -   SQL_COPT_SS_PERF_QUERY_INTERVAL  
    -   SQL_COPT_SS_PERF_QUERY_LOG  
-   SQLBrowseConnect  
-   Типы интервалов C, такие как SQL_C_INTERVAL_YEAR_TO_MONTH (задокументированы в статье [Идентификаторы и дескрипторы типов данных](https://msdn.microsoft.com/library/ms716351(VS.85).aspx))
-   Значение SQL_CUR_USE_ODBC атрибута SQL_ATTR_ODBC_CURSORS функции SQLSetConnectAttr.

## <a name="character-set-support"></a>Поддержка кодировок

Для версий 13 и 13.1 драйвера ODBC данные SQLCHAR должны иметь кодировку UTF-8. Другие кодировки не поддерживаются.

Для версии 17 драйвера ODBC поддерживаются данные SQLCHAR в одной из следующих кодировок:

|Имя|Описание|
|-|-|
|UTF-8|Юникод|
|CP437|Латиница MS-DOS (США)|
|CP850|Латиница 1 MS-DOS|
|CP874|Латиница/тайский|
|CP932|Японский, Shift-JIS|
|CP936|Китайский (упрощенный), GBK|
|CP949|Корейский, EUC-KR|
|CP950|Китайский (традиционный), Big5|
|CP1251|Кириллица|
|CP1253|Greek|
|CP1256|Арабский|
|CP1257|Балтийская|
|CP1258|Вьетнамский|
|ISO-8859-1 / CP1252|Латиница-1|
|ISO-8859-2 / CP1250|Латиница-2|
|ISO-8859-3|Латиница-3|
|ISO-8859-4|Латиница-4|
|ISO-8859-5|Латиница/кириллица|
|ISO-8859-6|Латиница/арабский|
|ISO-8859-7|Латиница/греческий|
|ISO-8859-8 / CP1255|Иврит|
|ISO-8859-9 / CP1254|Турецкий|
|ISO-8859-13|Латиница-7|
|ISO-8859-15|Латиница-9|

При подключении драйвер определяет текущий языковой стандарт процесса, в котором он загружен. Если используется одна из перечисленных выше кодировок, драйвер применяет ее для данных SQLCHAR (узкий набор символов). В противном случае по умолчанию применяется кодировка UTF-8. Так как все процессы по умолчанию запускаются с языковым стандартом "C" (из-за чего драйвер по умолчанию использует кодировку UTF-8), если приложению необходимо использовать одну из перечисленных выше кодировок, перед подключением оно должно задать соответствующий языковой стандарт с помощью функции **setlocale**. При этом нужный языковой стандарт необходимо указать либо явным образом, либо с помощью пустой строки, например `setlocale(LC_ALL, "")`, чтобы использовался языковой стандарт среды.

В обычной среде Linux или Mac применяется кодировка UTF-8, поэтому после обновления драйвера ODBC с версии 13 или 13.1 до версии 17 пользователи не заметят разницы. Однако если приложение использует отличную от UTF-8 кодировку из приведенного выше списка с помощью функции `setlocale()`, оно должно применять ее для данных, передаваемых в драйвер и из него, вместо UTF-8.

Данные SQLWCHAR должны иметь кодировку UTF-16LE (прямой порядок байтов).

Если при привязке входных параметров с помощью SQLBindParameter указан узкосимвольный тип SQL, такой как SQL_VARCHAR, драйвер преобразует предоставленные данные из кодировки клиента в кодировку [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по умолчанию (обычно это кодовая страница 1252). Выходные параметры драйвер преобразует из кодировки, указанной в сведениях о параметрах сортировки, связанных с данными, в кодировку клиента. Однако возможна потеря данных — символы исходной кодировки, не имеющие соответствия в конечной кодировке, преобразуются в вопросительные знаки (?).

Чтобы избежать этого при привязке входных параметров, укажите символьный тип Юникода SQL, например SQL_NVARCHAR. В этом случае драйвер выполняет преобразование из кодировки клиента в кодировку UTF-16, в которой могут быть представлены все символы Юникода. Кроме того, конечный столбец или параметр на сервере также должен иметь тип Юникода (**nchar**, **nvarchar**, **ntext**) или такой тип, в параметрах сортировки или кодировке которого могут быть представлены все символы исходных данных. Чтобы избежать потери данных в выходных параметрах, укажите тип Юникода SQL, а также либо тип Юникода C (SQL_C_WCHAR), вследствие чего драйвер вернет данные в кодировке UTF-16, либо узкосимвольный тип C, и убедитесь в том, что в кодировке клиента могут быть представлены все символы исходных данных (это всегда возможно в случае с UTF-8).

Дополнительные сведения о параметрах сортировки и кодирования см. в разделе [Поддержка параметров сортировки и Юникода](../../../relational-databases/collations/collation-and-unicode-support.md).

Существуют различия в преобразовании кодировки между Windows и рядом версий библиотеки iconv в Linux и macOS. Текстовые данные в кодовой странице 1255 (иврит) имеют одну кодовую точку (0xCA), которая ведет себя по-разному при преобразовании в Юникод. В Windows этот символ преобразуется в кодовую точку UTF-16 0x05BA. В macOS и Linux с библиотекой libiconv до версии 1.15 он преобразуется в кодовую точку 0x00CA. В Linux с библиотеками iconv, которые не поддерживают редакцию 2003 кодировки Big5/CP950 (`BIG5-2003`), символы, добавленные с использованием этой редакции, преобразуются неправильно. В кодовой странице 932 (японский, Shift-JIS) результат декодирования символов, которые изначально не определены в стандарте кодировки, также различается. Например, байт 0x80 преобразуется в U+0080 в Windows, но может стать U+30FB в Linux и macOS в зависимости от версии iconv.

Когда в ODBC Driver 13 и 13.1 многобайтовые символы UTF-8 или суррогаты UTF-16 распределяются между буферами SQLPutData, это приводит к повреждению данных. Для потоковой передачи SQLPutData используйте буферы, которые не заканчиваются на частичные кодировки символов. В версии 17 драйвера ODBC это ограничение снято.

## <a name="additional-notes"></a>Дополнительные замечания  

1.  Вы можете создать выделенное административное соединение с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и комбинации **узел,порт**. Члену роли Sysadmin сначала нужно сначала обнаружить порт выделенного административного соединения. Инструкции см. в статье [Диагностическое соединение для администраторов баз данных](https://docs.microsoft.com/sql/database-engine/configure-windows/diagnostic-connection-for-database-administrators#dac-port). Например, если бы порт выделенного административного соединения имел значение 33000, вы могли бы подключиться к нему с помощью `sqlcmd` следующим образом:  

    ```
    sqlcmd -U <user> -P <pwd> -S <host>,33000
    ```

    > [!NOTE]  
    > Выделенные административные соединения должны использовать проверку подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
    
2.  Диспетчер драйверов UnixODBC возвращает "Недопустимый идентификатор атрибута или параметра" для всех атрибутов инструкции, когда они передаются через SQLSetConnectAttr. Когда в Windows SQLSetConnectAttr получает значение атрибута инструкции, он заставляет драйвер установить это значение для всех активных инструкций, являющихся дочерними элементами дескриптора соединения.  

## <a name="see-also"></a>См. также:  
[Часто задаваемые вопросы](../../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)

[Известные проблемы в данной версии драйвера](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)

[Заметки о выпуске](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)
