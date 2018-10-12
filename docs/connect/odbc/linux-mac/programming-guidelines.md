---
title: Указания по программированию (драйвер ODBC для SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 01/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5030124775a8016fe5ddb716524276365aa47be7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47613089"
---
# <a name="programming-guidelines"></a>Указания по программированию

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Функции программирования [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] на платформах macOS и Linux основаны на ODBC в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ([SQL Server Native Client (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client основан на ODBC в компонентах доступа к данным Windows DAC ([Справочник по программированию ODBC](http://go.microsoft.com/fwlink/?LinkID=45250)).  

Приложение ODBC может использовать несколько активных результирующих наборов (MARS) и другие [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] конкретные компоненты, включая `/usr/local/include/msodbcsql.h` после включения заголовков unixODBC (`sql.h`, `sqlext.h`, `sqltypes.h`, и `sqlucode.h`). Затем используйте те же символьные имена для элементов, связанных с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], которые вы бы стали использовать в приложениях ODBC Windows.

## <a name="available-features"></a>Доступные функции  
Следующие разделы документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client для ODBC ([SQL Server Native Client (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)) применяются при использовании драйвера ODBC в macOS и Linux:  

-   [Взаимодействие с SQL Server (ODBC)](http://msdn.microsoft.com/library/ms131692.aspx)  
-   [Поддержка времени ожидания соединения и запроса](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
-   [Курсоры](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
-   [Улучшенная обработка даты и времени (ODBC)](http://msdn.microsoft.com/library/bb677319.aspx)  
-   [Выполнение запросов (ODBC)](http://msdn.microsoft.com/library/ms131677.aspx)  
-   [Обработка ошибок и сообщений](../../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
-   [Проверка подлинности Kerberos](../../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md)  
-   [Определяемые пользователем типы данных больших значений CLR (ODBC)](http://msdn.microsoft.com/library/bb677316.aspx)  
-   [Выполнение транзакций (ODBC) (за исключением распределенных транзакций)](http://msdn.microsoft.com/library/ms131706.aspx)  
-   [Обработка результатов (ODBC)](http://msdn.microsoft.com/library/ms130812.aspx)  
-   [Выполнение хранимых процедур](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)
-   [Поддержка разреженных столбцов (ODBC)](http://msdn.microsoft.com/library/cc280357.aspx)
-   [SSL-шифрование](../../../relational-databases/native-client/features/using-encryption-without-validation.md)
-   [Возвращающие табличные значения параметры](https://docs.microsoft.com/sql/relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc)
-   [UTF-8 и UTF-16 для команд и API данных](http://msdn.microsoft.com/library/ff878241.aspx)
-   [Использование функций каталога](../../../relational-databases/native-client/odbc/using-catalog-functions.md)  

## <a name="unsupported-features"></a>Неподдерживаемые функции

Для правильной работы в этой версии драйвера ODBC в macOS и Linux не были проверены следующие функции:

-   Подключение к кластеру отработки отказа
-   [Разрешение IP-адресов прозрачной сети](https://docs.microsoft.com/sql/connect/odbc/linux/using-transparent-network-ip-resolution) (перед ODBC Driver 17)
-   [Трассировка дополнительного драйвера](https://blogs.msdn.microsoft.com/mattn/2012/05/15/enabling-advanced-driver-tracing-for-the-sql-native-client-odbc-drivers/)

Следующие функции недоступны в этой версии драйвера ODBC на платформах macOS и Linux: 

-   Распределенные транзакции (атрибут SQL_ATTR_ENLIST_IN_DTC не поддерживается)  
-   Зеркальное отображение базы данных  
-   FILESTREAM  
-   Профилирование производительности драйвера ODBC, рассматриваемое в статье [SQLSetConnectAttr](http://go.microsoft.com/fwlink/?LinkId=234099), и следующие атрибуты соединения, связанные с производительностью:  
    -   SQL_COPT_SS_PERF_DATA  
    -   SQL_COPT_SS_PERF_DATA_LOG  
    -   SQL_COPT_SS_PERF_DATA_LOG_NOW  
    -   SQL_COPT_SS_PERF_QUERY  
    -   SQL_COPT_SS_PERF_QUERY_INTERVAL  
    -   SQL_COPT_SS_PERF_QUERY_LOG  
-   SQLBrowseConnect  
-   Типы интервалов C, такие как SQL_C_INTERVAL_YEAR_TO_MONTH (задокументированы в статье [Идентификаторы и дескрипторы типов данных](http://msdn.microsoft.com/library/ms716351(VS.85).aspx))
-   Значение SQL_CUR_USE_ODBC атрибута SQL_ATTR_ODBC_CURSORS функции SQLSetConnectAttr.

## <a name="character-set-support"></a>Поддержка набор символов

ODBC Driver 13 и 13.1 данные SQLCHAR должны иметь UTF-8. Другие кодировки не поддерживаются.

Для ODBC Driver 17 поддерживается данных SQLCHAR в одном из следующих наборов/следующие кодировки символов:

|Имя|Описание|
|-|-|
|UTF-8|Юникод|
|CP437|Латиница MS-DOS США|
|CP850|MS-DOS латиница 1|
|CP874|Латиница/тайский|
|CP932|Японская Shift-JIS|
|CP936|Китайский (упрощенный), GBK|
|CP949|Корейский, EUC-KR|
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
|ISO-8859-6|Арабское Latin|
|ISO-8859-7|Латинский и греческий|
|ISO-8859-8 / CP1255|Иврит|
|ISO-8859-9 / CP1254|Турецкий|
|ISO-8859-13|Латиница-7|
|ISO-8859-15|Латиница 9|

При подключении драйвер обнаруживает процесса, который загружается в текущий языковой стандарт. Если он использует одну из кодировок выше, драйвер использует эту кодировку для данных SQLCHAR (обычными символами); в противном случае по умолчанию используется UTF-8. Поскольку все процессы запуск в языковом стандарте «C», по умолчанию (и, таким образом привести к драйверу по умолчанию UTF-8), если приложению требуется использовать одну из кодировок выше, следует использовать **setlocale** функцию для задания языкового стандарта, соответствующим образом перед подключение; явное указание нужного языкового стандарта, или используя пустую строку, например `setlocale(LC_ALL, "")` использовать параметры языкового стандарта среды.

Таким образом в обычной среде Linux или Mac где кодировки является UTF-8, пользователи ODBC Driver 17 обновления из 13 или 13.1 не будет наблюдать все различия. Тем не менее, приложения, использующие кодировку отличные от UTF-8 в приведенном выше списке, с помощью `setlocale()` нужно использовать эту кодировку данными с драйвером, а не UTF-8.

Данные SQLWCHAR должны иметь кодировку UTF-16LE (прямой порядок байтов).

При привязке входных параметров с SQLBindParameter, если тип SQL узких символов, например указан SQL_VARCHAR, драйвер преобразует предоставленные данные от клиента, кодировку по умолчанию (обычно кодовая страница 1252) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] кодирования. Для выходных параметров драйвер преобразует кодировку, заданную в сведения о параметрах сортировки, связанное с данными для кодирования клиента. Тем не менее, возможна потеря данных---преобразует символы в кодировке источника не может быть представлен в целевой кодировке в знак вопроса ("?").

Чтобы избежать такой потери данных при привязке входных параметров, укажите тип символа SQL Юникода, например SQL_NVARCHAR. В этом случае драйвер преобразует от клиента, кодировка UTF-16, которые могут представлять все символы Юникода. Более того, целевого столбца или параметра на сервере должен также быть типом Юникода (**nchar**, **nvarchar**, **ntext**) или один из параметров сортировки/кодировка данных, который можно представления всех символов исходный источник данных. Для предотвращения потери данных с выходными параметрами, укажите тип SQL Юникода и либо Юникода C типом (SQL_C_WCHAR), приводит к драйверу возвращать данные в виде UTF-16. или узкий C введите команду и убедитесь, что клиент кодирование может представлять все символы из источника данных (это всегда возможно с помощью UTF-8.)

Дополнительные сведения о параметрах сортировки и кодирования см. в разделе [Поддержка параметров сортировки и Юникода](../../../relational-databases/collations/collation-and-unicode-support.md).

Существуют некоторые кодировки преобразование различия между Windows и несколько версий библиотекой iconv в Linux и macOS. Текстовые данные в кодовой странице 1255 (иврит) имеют одну кодовую точку (0xCA), ведет себя по-разному, при преобразовании в Юникод. В Windows этот символ преобразует позицию кода UTF-16 0x05BA. В macOS и Linux с помощью libiconv версий более ранних, чем 1.15 он преобразует 0x00CA. В Linux с использованием iconv библиотек, которые не поддерживают версии 2003 Big5/CP950 (с именем `BIG5-2003`), знаков, добавленных с помощью этого исправления не будут правильно преобразовать. В кодовой странице 932 (японский, Shift-JIS) результат декодирование символов, не определенный в кодировке отличается. Например байт 0x80 преобразует U + 0080 на Windows, но может стать 30FB U + в Linux и macOS, в зависимости от версии iconv.

Когда в ODBC Driver 13 и 13.1 многобайтовые символы UTF-8 или суррогаты UTF-16 распределяются между буферами SQLPutData, это приводит к повреждению данных. Для потоковой передачи SQLPutData используйте буферы, которые не заканчиваются на частичные кодировки символов. Это ограничение было снято с ODBC Driver 17.

## <a name="additional-notes"></a>Дополнительные замечания  

1.  Вы можете создать выделенное административное соединение с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и комбинации **узел,порт**. Члену роли Sysadmin сначала нужно сначала обнаружить порт выделенного административного соединения. См. в разделе [диагностическое соединение для администраторов баз данных](https://docs.microsoft.com/sql/database-engine/configure-windows/diagnostic-connection-for-database-administrators#dac-port) для обнаружения как. Например, если бы порт выделенного административного соединения имел значение 33000, вы могли бы подключиться к нему с помощью `sqlcmd` следующим образом:  

    ```
    sqlcmd –U <user> -P <pwd> -S <host>,33000
    ```

    > [!NOTE]  
    > Выделенные административные соединения должны использовать проверку подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
    
2.  Диспетчер драйверов UnixODBC возвращает "Недопустимый идентификатор атрибута или параметра" для всех атрибутов инструкции, когда они передаются через SQLSetConnectAttr. Когда в Windows SQLSetConnectAttr получает значение атрибута инструкции, он заставляет драйвер установить это значение для всех активных инструкций, являющихся дочерними элементами дескриптора соединения.  

## <a name="see-also"></a>См. также:  
[Часто задаваемые вопросы](../../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)

[Известные проблемы в данной версии драйвера](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)

[Заметки о выпуске](../../../connect/odbc/linux-mac/release-notes.md)
