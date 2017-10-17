---
title: "Рекомендации по программированию | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2e3aac41bd87f52998edf366d7c3da2326de3f26
ms.contentlocale: ru-ru
ms.lasthandoff: 10/10/2017

---
# <a name="programming-guidelines"></a>Указания по программированию
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)] Функции программирования [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 и 13.1 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] на macOS и Linux основаны на ODBC в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Native Client ([собственного клиента SQL Server (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Native Client основан на ODBC в компонентах доступа к данным Windows ([справочнике программиста ODBC](http://go.microsoft.com/fwlink/?LinkID=45250)).  

Приложение ODBC может использовать несколько активные результирующие наборы (MARS) и других [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] конкретные компоненты, включая `/usr/local/include/msodbcsql.h` после включения заголовков unixODBC (`sql.h`, `sqlext.h`, `sqltypes.h`, и `sqlucode.h`). Затем используйте те же символьные имена для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]-определенных элементов, которые обычно выполняются в приложениях Windows ODBC.  

## <a name="available-features"></a>Доступные функции  
В следующих разделах из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] документации Native Client для ODBC ([собственного клиента SQL Server (ODBC)](http://go.microsoft.com/fwlink/?LinkID=134151)) при использовании драйвера ODBC в macOS и Linux:  

-   [Взаимодействие с SQL Server (ODBC)](http://msdn.microsoft.com/library/ms131692.aspx)  
-   [Поддержка времени ожидания соединения и запроса](http://msdn.microsoft.com/library/ms130822.aspx)  
-   [Курсоры](http://msdn.microsoft.com/library/ms130794(SQL.110).aspx)  
-   [Дата и время усовершенствования (ODBC)](http://msdn.microsoft.com/library/bb677319.aspx)  
-   [Выполнение запросов (ODBC)](http://msdn.microsoft.com/library/ms131677.aspx)  
-   [Обработка ошибок и сообщений](http://msdn.microsoft.com/library/ms131289.aspx)  
-   [Проверка подлинности Kerberos](http://msdn.microsoft.com/library/cc280459.aspx)  
-   [Определяемые пользователем типы больших значений CLR (ODBC)](http://msdn.microsoft.com/library/bb677316.aspx)  
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
-   [Разрешение IP-адресов для прозрачной сети](https://docs.microsoft.com/en-us/sql/connect/odbc/linux/using-transparent-network-ip-resolution)
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

Клиент кодировка может быть одним из следующих:
  -  UTF-8
  -  ISO-8859-1
  -  ISO-8859-2
  -  ISO-8859-3
  -  ISO-8859-4
  -  ISO-8859-5
  -  ISO-8859-6
  -  ISO-8859-7
  -  ISO-8859-8
  -  ISO-8859-9
  -  ISO-8859-13
  -  ISO-8859-15
  
Данные SQLCHAR должны иметь один из поддерживаемых кодировок. Данные SQLWCHAR должны иметь кодировку UTF-16LE (прямой порядок байтов).  

Если SQLDescribeParameter не указывает тип SQL на сервере, драйвер использует тип SQL, указанный в параметре *ParameterType* функции SQLBindParameter. Если в SQLBindParameter указан узкосимвольный тип SQL, такой как SQL_VARCHAR, драйвер преобразует предоставленные данные из кодовой страницы клиента по умолчанию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] кодовую страницу. (Значение по умолчанию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] обычно используется кодовая страница 1252.) Если кодовая страница клиента не поддерживается, оно будет присвоено UTF-8. В этом случае драйвер затем преобразует данные UTF-8 в кодовую страницу по умолчанию. Однако при этом возможна потеря данных. Если кодовая страница 1252 не позволяет представить символ, драйвер преобразует его в знак вопроса ("?"). Чтобы избежать такой потери данных, укажите тип символа SQL Юникода, например SQL_NVARCHAR, в SQLBindParameter. В этом случае драйвер преобразует предоставленные данные Юникода в кодировке UTF-8 в UTF-16 без потери данных.

Есть разница преобразование кодировки текста между Windows и библиотекой iconv в Linux и macOS несколько версий. Текстовые данные, закодированные в кодовой странице 1255 (иврит) имеют одну кодовую точку (0xCA), ведет себя по-разному при преобразовании. Преобразование этот символ в кодировке Юникод в Windows создает кодовую точку UTF-16 0x05BA. Преобразование в Юникод в macOS и Linux с libiconv версии более ранней, чем 1.15 создает кодовую точку UTF-16 0x00CA.

Когда многобайтовые символы UTF-8 или суррогаты UTF-16 распределяются между буферами SQLPutData, это приводит к повреждению данных. Для потоковой передачи SQLPutData используйте буферы, которые не заканчиваются на частичные кодировки символов.  

## <a name="additional-notes"></a>Дополнительные замечания  

1.  Можно сделать выделенное административное соединение (DAC) с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] проверки подлинности и **узел, порт**. Члену роли Sysadmin сначала нужно сначала обнаружить порт выделенного административного соединения. В разделе [диагностическое соединение для администраторов баз данных](https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/diagnostic-connection-for-database-administrators#dac-port) для обнаружения как. Например, если порт выделенного административного Соединения 33000, может к ним можно подключиться с `sqlcmd` следующим образом:  

    ```
    sqlcmd –U <user> -P <pwd> -S <host>,33000
    ```

    > [!NOTE]  
    > Необходимо использовать выделенных Административных соединений [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] проверки подлинности.  
    
2.  Диспетчер драйверов UnixODBC возвращает "Недопустимый идентификатор атрибута или параметра" для всех атрибутов инструкции, когда они передаются через SQLSetConnectAttr. В Windows когда SQLSetConnectAttr получает значение атрибута инструкции заставляет драйвер установить это значение для всех активных инструкций, которые являются дочерними элементами дескриптора соединения.  

## <a name="see-also"></a>См. также:  
[Часто задаваемые вопросы](../../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)

[Известные проблемы в данной версии драйвера](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)

[Заметки о выпуске](../../../connect/odbc/linux-mac/release-notes.md)

