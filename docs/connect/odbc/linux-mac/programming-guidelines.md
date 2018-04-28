---
title: Рекомендации по программированию (драйвер ODBC для SQL Server) | Документы Microsoft
ms.custom: ''
ms.date: 01/11/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e30ed328931cc33b62dd9d65301dee8921e1cc3f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="programming-guidelines"></a>Указания по программированию

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Функции программирования [!INCLUDE[msCoName](../../../includes/msconame_md.md)] драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] на macOS и Linux основаны на ODBC в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client ([собственного клиента SQL Server (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client основан на ODBC в компонентах доступа к данным Windows ([справочнике программиста ODBC](http://go.microsoft.com/fwlink/?LinkID=45250)).  

Приложение ODBC может использовать несколько активные результирующие наборы (MARS) и других [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] конкретные компоненты, включая `/usr/local/include/msodbcsql.h` после включения заголовков unixODBC (`sql.h`, `sqlext.h`, `sqltypes.h`, и `sqlucode.h`). Затем используйте те же символьные имена для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]-определенных элементов, которые вы будете использовать в приложениях Windows ODBC.

## <a name="available-features"></a>Доступные функции  
В следующих разделах из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] документации Native Client для ODBC ([собственного клиента SQL Server (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)) при использовании драйвера ODBC в macOS и Linux:  

-   [Взаимодействие с SQL Server (ODBC)](http://msdn.microsoft.com/library/ms131692.aspx)  
-   [Поддержка времени ожидания соединения и запроса](http://msdn.microsoft.com/library/ms130822.aspx)  
-   [Курсоры](http://msdn.microsoft.com/library/ms130794(SQL.110).aspx)  
-   [Дата и время усовершенствования (ODBC)](http://msdn.microsoft.com/library/bb677319.aspx)  
-   [Выполнение запросов (ODBC)](http://msdn.microsoft.com/library/ms131677.aspx)  
-   [Обработка ошибок и сообщений](http://msdn.microsoft.com/library/ms131289.aspx)  
-   [Проверка подлинности Kerberos](http://msdn.microsoft.com/library/cc280459.aspx)  
-   [Определяемые пользователем типы данных больших значений CLR (ODBC)](http://msdn.microsoft.com/library/bb677316.aspx)  
-   [Выполнение транзакций (ODBC) (за исключением распределенных транзакций)](http://msdn.microsoft.com/library/ms131706.aspx)  
-   [Обработка результатов (ODBC)](http://msdn.microsoft.com/library/ms130812.aspx)  
-   [Выполнение хранимых процедур](http://msdn.microsoft.com/library/ms131440.aspx)
-   [Поддержка разреженных столбцов (ODBC)](http://msdn.microsoft.com/library/cc280357.aspx)
-   [SSL-шифрования](http://msdn.microsoft.com/library/ms131691.aspx)
-   [Таблица табличное значение параметры](https://docs.microsoft.com/en-us/sql/relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc)
-   [UTF-8 и UTF-16 для команд и API данных](http://msdn.microsoft.com/library/ff878241.aspx)
-   [Использование функций каталога](http://msdn.microsoft.com/library/ms131490.aspx)  

## <a name="unsupported-features"></a>Неподдерживаемые функции

Следующие функции не были проверены для правильной работы в этот выпуск драйвера ODBC на macOS и Linux:

-   Подключение отказоустойчивого кластера
-   [Разрешение IP-адресов для прозрачной сети](https://docs.microsoft.com/en-us/sql/connect/odbc/linux/using-transparent-network-ip-resolution) (до 17 драйвер ODBC)
-   [Трассировка дополнительного драйвера](https://blogs.msdn.microsoft.com/mattn/2012/05/15/enabling-advanced-driver-tracing-for-the-sql-native-client-odbc-drivers/)

Следующие функции недоступны в этой версии драйвера ODBC в macOS и Linux: 

-   Распределенные транзакции (атрибут SQL_ATTR_ENLIST_IN_DTC не поддерживается)  
-   Зеркальное отображение базы данных  
-   FILESTREAM  
-   Профилирование производительности драйвера ODBC, рассматриваемые в [SQLSetConnectAttr](http://go.microsoft.com/fwlink/?LinkId=234099)и следующие атрибуты соединения, связанные с производительностью:  
    -   SQL_COPT_SS_PERF_DATA  
    -   SQL_COPT_SS_PERF_DATA_LOG  
    -   SQL_COPT_SS_PERF_DATA_LOG_NOW  
    -   SQL_COPT_SS_PERF_QUERY  
    -   SQL_COPT_SS_PERF_QUERY_INTERVAL  
    -   SQL_COPT_SS_PERF_QUERY_LOG  
-   SQLBrowseConnect  
-   Типы интервала C, такие как SQL_C_INTERVAL_YEAR_TO_MONTH (задокументированы в [данных идентификаторы и дескрипторы типов](http://msdn.microsoft.com/library/ms716351(VS.85).aspx))
-   Значение SQL_CUR_USE_ODBC атрибута SQL_ATTR_ODBC_CURSORS функции SQLSetConnectAttr.

## <a name="character-set-support"></a>Поддержка набор символов

ODBC Driver 13 и 13.1 данные SQLCHAR должны быть UTF-8. Поддерживаются другие форматы кодировки.

17 драйвера ODBC поддерживаемые данных SQLCHAR в одном из следующих наборов или кодировок:

|Название|Описание|
|-|-|
|UTF-8|Юникод|
|CP437|Латинская MS-DOS США|
|CP850|MS-DOS латиница 1|
|CP874|Латинская и тайский|
|CP932|Японская Shift-JIS|
|CP936|Китайский (упрощенный), GBK|
|CP949|Корейский, EUC KR|
|CP950|Китайский (традиционный), Big5|
|CP1251|Кириллица|
|CP1253|Greek|
|CP1256|Арабский|
|CP1257|Балтийская|
|CP1258|Вьетнамский|
|ISO-8859-1 / CP1252|Латиница 1|
|ISO-8859-2 / CP1250|Латиница-2|
|ISO-8859-3|Латиница-3|
|ISO-8859-4|Латиница-4|
|ISO-8859-5|Латиница и кириллица|
|ISO-8859-6|Латинская/арабский|
|ISO-8859-7|Латиница греческая|
|ISO-8859-8 / CP1255|Иврит|
|ISO-8859-9 / CP1254|Турецкий|
|ISO-8859-13|Латиница-7|
|ISO-8859-15|Латиница 9|

После создания соединения драйвер обнаруживает процесса, который загружается в текущий языковой стандарт. Если он использует одну из кодировок, которые выше, драйвер использует кодировку для данных SQLCHAR (узкие символьные); в противном случае по умолчанию используется UTF-8. Поскольку все процессы запуск в языковом стандарте «C» по умолчанию (и тем самым вызвать драйверу по умолчанию UTF-8), если приложению требуется для применения описанных выше кодировок, следует использовать **setlocale** функции перед соответствующим образом указывать языковой стандарт подключение; явное указание нужного языкового стандарта или используя пустую строку, например `setlocale(LC_ALL, "")` использовать региональные настройки среды.

Таким образом в типичной Mac или Linux среде где кодировку UTF-8 — обновление 17 драйвера ODBC 13 или 13.1 пользователей не будет наблюдать любые различия. Тем не менее, приложения, использующие кодировку отличном от UTF-8 в приведенном выше списке через `setlocale()` должны использовать эту кодировку для данных из драйвера вместо UTF-8.

Данные SQLWCHAR должны иметь кодировку UTF-16LE (прямой порядок байтов).

При привязке входных параметров с SQLBindParameter, если тип SQL узких символов, например указан SQL_VARCHAR, драйвер преобразует предоставленные данные от клиента, кодировка по умолчанию (обычно кодовая страница 1252) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] кодировку. Для выходных параметров драйвер преобразует кодировку, заданную в сведения о параметрах сортировки, связанное с данными для клиент кодировки. Тем не менее, возможна потеря данных — преобразует символы в кодировке источника не может быть представлен в целевой кодировке с вопросительным знаком ("?").

Чтобы избежать потерю данных при привязке входных параметров, укажите тип символа SQL Юникода, например SQL_NVARCHAR. В этом случае драйвер преобразует от клиента, кодировка UTF-16, который может представлять все символы Юникода. Кроме того, целевой столбец или параметр на сервере также должны либо тип Юникода (**nchar**, **nvarchar**, **ntext**) или один из параметров сортировки и кодировке, который может представления всех символов исходный источник данных. Для предотвращения потери данных с выходными параметрами, укажите тип SQL Юникода и либо Юникода C тип (SQL_C_WCHAR) вызывает драйвер для возврата данных в виде UTF-16. или узких C введите и убедитесь, что клиент кодирование может представлять все символы источника данных (это всегда возможно UTF-8.)

Дополнительные сведения о параметрах сортировки и кодировок см. в разделе [Collation and Unicode Support](../../../relational-databases/collations/collation-and-unicode-support.md).

Несколько отличаются кодировки преобразование между Windows и библиотекой iconv в Linux и macOS несколько версий. Текстовые данные в кодовой странице 1255 (иврит) имеют одну кодовую точку (0xCA), ведет себя по-разному, при преобразовании в Юникод. В Windows этот символ преобразуется в кодовую точку в кодировке UTF-16 0x05BA. В macOS и Linux с libiconv версий более ранних, чем 1.15 преобразуется 0x00CA. В Linux с iconv библиотек, которые не поддерживают версии 2003 Big5/CP950 (с именем `BIG5-2003`), символов, добавленных с помощью этой версии не будет правильно преобразовать. В кодовой странице 932 (японский, Shift-JIS) результат декодирование символов, которые первоначально не были определены в кодировке отличается. Например байтов 0x80 преобразует U + 0080 в Windows, но может оказаться U + 30FB на macOS, в зависимости от версии iconv и Linux.

В ODBC Driver 13 и 13.1 когда многобайтовые символы UTF-8 или суррогаты UTF-16 распределяются между буферами SQLPutData, он приводит к повреждению данных. Для потоковой передачи SQLPutData используйте буферы, которые не заканчиваются на частичные кодировки символов. Это ограничение снято с 17 драйвера ODBC.

## <a name="additional-notes"></a>Дополнительные замечания  

1.  Можно сделать выделенное административное соединение (DAC) с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] проверки подлинности и **узел, порт**. Члену роли Sysadmin сначала нужно сначала обнаружить порт выделенного административного соединения. В разделе [диагностическое соединение для администраторов баз данных](https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/diagnostic-connection-for-database-administrators#dac-port) для обнаружения как. Например, если порт выделенного административного Соединения 33000, может к ним можно подключиться с `sqlcmd` следующим образом:  

    ```
    sqlcmd –U <user> -P <pwd> -S <host>,33000
    ```

    > [!NOTE]  
    > Необходимо использовать выделенных Административных соединений [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] проверки подлинности.  
    
2.  Диспетчер драйверов UnixODBC возвращает "Недопустимый идентификатор атрибута или параметра" для всех атрибутов инструкции, когда они передаются через SQLSetConnectAttr. В Windows когда SQLSetConnectAttr получает значение атрибута инструкции заставляет драйвер установить это значение для всех активных инструкций, которые являются дочерними элементами дескриптора соединения.  

## <a name="see-also"></a>См. также  
[Часто задаваемые вопросы](../../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)

[Известные проблемы в данной версии драйвера](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)

[Заметки о выпуске](../../../connect/odbc/linux-mac/release-notes.md)
