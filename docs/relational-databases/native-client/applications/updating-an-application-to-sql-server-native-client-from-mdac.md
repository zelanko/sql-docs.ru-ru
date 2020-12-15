---
title: Обновление из MDAC
description: Обновите компоненты доступа к данным Windows до SQL Server Native Client, которые предоставляют новые функции SQL Server 2005 с обратной совместимостью.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- SQLNCLI, vs. MDAC
- SQL Server Native Client, vs. MDAC
- data access [SQL Server Native Client], vs. MDAC
- SQL Server Native Client, updating applications
ms.assetid: 2860efdd-c59a-4deb-8a0e-5124a8f4e6dd
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fb360bbc4f874af32b720ea024f9322aa02dea24
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97469225"
---
# <a name="updating-an-application-to-sql-server-native-client-from-mdac"></a>Обновление приложения с переходом от компонентов MDAC к собственному клиенту SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Между собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и компонентами доступа к данным MDAC существует несколько различий; начиная с Windows Vista, компоненты доступа к данным стали называться компонентами доступа к данным Windows, или Windows DAC. Хотя обе программы реализуют собственный доступ к базам данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует новые функции [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] особым образом, обеспечивая в то же время обратную совместимость с ранними версиями.  
  
 Приведенные в этом разделе сведения помогут вам обновить приложения компонентов MDAC (или выделенное административное соединение Windows) до текущей версии собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], который входит в состав [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Сведения о том, как обеспечить актуальность этого приложения с помощью версии [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, поставляемой в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , см. в разделе [обновление приложения с SQL Server 2005 Native Client](../../../relational-databases/native-client/applications/updating-an-application-from-sql-server-2005-native-client.md).  
  
 Кроме того, в компоненты MDAC входят компоненты для использования OLE DB, ODBC и объектов ADO, а собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] реализует только интерфейсы OLE DB и ODBC (хотя объекты ADO могут использовать функции собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).  
  
 Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и компоненты MDAC различаются также в следующих областях.  
  
-   Пользователи, использующие объекты ADO для доступа к поставщику собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], могут иметь в своем распоряжении меньше функций фильтрации, чем при доступе к поставщику SQL OLE DB.  
  
-   Если в приложении ADO используется собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и предпринимается попытка обновить вычисляемый столбец, то появляется сообщение об ошибке. При использовании компонентов MDAC обновление было бы принято, но пропущено.  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] является одним автономным файлом DLL. Количество интерфейсов с открытым доступом сведено к минимуму, чтобы упростить распространение, а также повысить уровень безопасности.  
  
-   Поддерживаются только интерфейсы OLE DB и ODBC.  
  
-   Поставщик OLE DB и драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] имеют имена, отличные от тех, которые используются в компонентах MDAC.  
  
-   Доступные для пользователя функции, предоставляемые компонентами MDAC, можно использовать при работе с собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. К ним помимо прочего относится создание пулов соединений, поддержка ADO и поддержка клиентских курсоров. При использовании любой из этих функций собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] обеспечивает только связь с базой данных. Компоненты MDAC предоставляют такие функции, как трассировка, элементы управления в интерфейсе управления и счетчики производительности.  
  
-   Приложения могут использовать основные службы OLE DB в сочетании с собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], однако при использовании ядра курсора OLE DB в них должен быть установлен параметр совместимости типов данных во избежание потенциальных проблем, которые могут возникнуть в связи с тем, что в ядре курсора отсутствуют сведения о новых типах данных [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает доступ к базам данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предыдущих версий.  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не содержит средств интеграции с XML. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Собственный клиент поддерживает SELECT... ДЛЯ запросов FOR XML, но не поддерживает другие функции XML. Однако [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент поддерживает тип данных **XML** , представленный в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] .  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает настройку сетевых библиотек на стороне клиента с использованием только атрибутов строки соединения. Если требуется провести более сложную настройку сетевых библиотек, необходимо использовать диспетчер конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] несовместим с odbcbcp.dll. Приложения, использующие API ODBC и **bcp** , должны быть перестроены для связи с sqlncli11. lib, чтобы использовать [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент.  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не поддерживается из поставщика Microsoft OLE DB для ODBC (MSDASQL). При использовании драйвера MDAC SQLODBC вместе с MSDASQL или драйвера MDAC SQLODBC вместе с ADO используйте OLE DB в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Строки подключения компонентов MDAC позволяют использовать логическое значение (**true**) для ключевого слова **Trusted_Connection**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Строка подключения собственного клиента должна иметь **значение Yes** или **No**.  
  
-   Незначительные изменения внесены в предупреждения и ошибки. Теперь в передаваемых собственному клиенту [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предупреждениях и ошибках, которые возвращаются сервером, сохраняется такая же степень серьезности. Следует тщательно протестировать приложение, если его работа зависит от перехвата определенных предупреждений и ошибок.  
  
-   Проверка ошибок в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] строже, чем в компонентах MDAC, а это означает, что некоторые приложения, которые не полностью соответствуют спецификациям ODBC и OLE DB, могут работать по-разному. Например, поставщик SQLOLEDB не применяет правило, в соответствии с которым имена параметров должны начинаться с " \@ " для параметров результата, но [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент OLE DB поставщика.  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и компоненты MDAC по-разному реагируют на разрыв соединения. Например, компоненты MDAC возвращают кэшированные значения свойств разорванного соединения, тогда как собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] сообщает вызывающему приложению об ошибке.  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не формирует события Visual Studio Analyzer, вместо них он формирует события трассировки Windows.  
  
-   Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] невозможно использовать с системным монитором. Системный монитор — это средство Windows, которое можно использовать только для файлов DSN, которые используют драйвер MDAC SQLODBC, входящий в Windows.  
  
-   Если собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] подключен к [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] и более поздних версий, то возврат ошибки сервера 16947 осуществляется в виде SQL_ERROR. Эта ошибка возникает, если при выполнении позиционированного обновления или удаления не удается обновить или удалить строку. При использовании компонентов MDAC для соединения с любой версией [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ошибка сервера 16947 возвращается в виде предупреждения (SQL_SUCCESS_WITH_INFO).  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Собственный клиент реализует интерфейс **идбдатасаурцеадмин** , который является необязательным OLE DB интерфейсом, который ранее не был реализован, но реализуется только метод **креатедатасаурце** этого необязательного интерфейса. [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
-   Поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращает синонимы в наборах строк схемы TABLES и TABLE_INFO, при этом параметру TABLE_TYPE присваивается значение SYNONYM.  
  
-   Возвращаемые значения типов данных **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **XML**, **UDT** и других типов больших объектов не могут возвращаться в клиентские версии, предшествующие [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] . Если эти типы должны служить в качестве возвращаемых значений, необходимо использовать собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Компоненты MDAC позволяют выполнять следующие инструкции при запуске ручных или неявных транзакций, а собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] — нет. Они должны выполняться в режиме автоматической фиксации.  
  
    -   Все полнотекстовые операции (операции DDL с индексом и каталогом)  
  
    -   Все операции с базой данных (создание базы данных, изменение базы данных, удаление базы данных)  
  
    -   Перенастройка  
  
    -   Shutdown  
  
    -   Завершить  
  
    -   Резервное копирование  
  
-   При подключении приложений MDAC к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типы данных, представленные в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], будут отображаться как типы данных, совместимые с [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)], как показано в следующей таблице.  
  
    |Тип SQL Server 2005|Тип SQL Server 2000|  
    |--------------------------|--------------------------|  
    |**varchar(max)**|**text**|  
    |**nvarchar(max)**|**ntext**|  
    |**varbinary(max)**|**image**|  
    |**udt**|**varbinary**|  
    |**xml**|**ntext**|  
  
     Это сопоставление типов затрагивает значения, возвращаемые для метаданных столбцов. Например, максимальный размер **текстового** столбца — 2 147 483 647, но [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент ODBC сообщает максимальный размер столбцов **varchar (max)** как SQL_SS_LENGTH_UNLIMITED, а [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный клиент OLE DB сообщает максимальный размер столбцов **varchar (max)** в виде 2 147 483 647 или-1 в зависимости от платформы.  
  
-   В собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в целях обеспечения обратной совместимости допускается неоднозначность в строках соединений (например, некоторые ключевые слова могут быть указаны несколько раз, а также может допускаться использование конфликтующих ключевых слов; при этом разрешение конфликтов происходит с учетом позиции или приоритета). В следующих версиях собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] неоднозначность в строках соединения может стать недопустимой. При изменении приложения для работы с собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] необходимо предусмотреть устранение любых зависимостей от неоднозначности строки соединения.  
  
-   При запуске транзакций с помощью вызова ODBC или OLE DB собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и компоненты MDAC ведут себя по-разному; при работе с собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] транзакции запускаются немедленно, а при использовании компонентов MDAC запуск транзакций происходит только после первого доступа к базе данных. Это может повлиять на поведение хранимых процедур и пакетов, так как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] требует \@ \@ , чтобы значение TRANCOUNT совпадало после завершения выполнения пакета или хранимой процедуры, как это было при запуске пакета или хранимой процедуры.  
  
-   При использовании [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента ITransactionLocal:: BeginTransaction приведет к немедленному запуску транзакции. При использовании компонентов MDAC запуск транзакции задерживается до выполнения приложением инструкции, которой требуется транзакция в неявном режиме. Дополнительные сведения см. в разделе [SET IMPLICIT_TRANSACTIONS (Transact-SQL)](../../../t-sql/statements/set-implicit-transactions-transact-sql.md).  
  
-   При использовании [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] драйвера собственного клиента с System. Data. ODBC могут возникнуть ошибки, чтобы получить доступ к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] серверу, предоставляющему новые, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] специфичные типы данных или функции. System. Data. ODBC предоставляет универсальную реализацию ODBC и впоследствии не предоставляет функции или расширения, относящиеся к поставщику. (Элемент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Драйвер собственного клиента обновляется для встроенной поддержки новейших [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] функций.) Чтобы обойти эту проблему, можно либо вернуться к компоненту MDAC, либо перейти на System. Data. SqlClient.  
  
 Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и MDAC поддерживают уровень изоляции транзакций read committed при использовании управления версиями строк, однако изоляцию транзакций моментальных снимков поддерживает только собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. (С точки зрения программирования уровень изоляции транзакций READ COMMITTED с управлением версиями строк представляет собой то же, что и транзакция READ COMMITTED.)  
  
## <a name="see-also"></a>См. также:  
 [Построение приложений с использованием SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
