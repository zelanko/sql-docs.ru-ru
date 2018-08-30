---
title: Параметры соединения | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6d1ea295-8e34-438e-8468-4bbc0f76192c
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 319ada38e07a30fa936608adce4e5c091ba098ec
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "42787080"
---
# <a name="connection-options"></a>Параметры соединения
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Этот раздел содержит перечень параметров, которые допускаются в ассоциативном массиве (при использовании [sqlsrv_connect](../../connect/php/sqlsrv-connect.md) в драйвере SQLSRV), и ключевых слов, которые допускаются в имени источника данных (dsn, при использовании [PDO::__construct](../../connect/php/pdo-construct.md) в драйвере PDO_SQLSRV).  

## <a name="table-of-connection-options"></a>Таблица параметров подключения
|Key|Значение|Описание|По умолчанию|  
|-------|---------|---------------|-----------|  
|APP|String|Указывает имя приложения, используемое для трассировки.|Значение не задано.|  
|ApplicationIntent|String|Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможными значениями являются ReadOnly и ReadWrite.<br /><br />Дополнительные сведения о [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] поддержка [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], см. в разделе [Поддержка высокой доступности и аварийного восстановления](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|ReadWrite|  
|AttachDBFileName|String|Указывает, какой файл базы данных сервер должен присоединить.|Значение не задано.|  
|Проверка подлинности|Одна из следующих строк:<br /><br />"SqlPassword"<br /><br />"ActiveDirectoryPassword"|Указывает режим проверки подлинности.|Не задано.|  
|CharacterSet<br /><br />(не поддерживается в драйвере PDO_SQLSRV)|String|Задает кодировку, используемую для отправки данных на сервер.<br /><br />Возможными значениями являются SQLSRV_ENC_CHAR и UTF-8. Дополнительные сведения см. в статье [How to: Send and Retrieve UTF-8 Data Using Built-In UTF-8 Support](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md).|SQLSRV_ENC_CHAR|  
|ColumnEncryption|**Enabled** (Включено) или **Disabled** (Отключено)|Указывает, включена ли функция Always Encrypted, или нет. |Выключено|  
|ConnectionPooling|1 или **true** для включения организации пулов соединений.<br /><br />0 или **false** для отключения организации пулов соединений.|Указывает, назначено ли соединение из пула соединений (1 или **true**) или нет (0 или **false**) <sup>1</sup>.|**true** (1)|  
|ConnectRetryCount|Целое число от 0 до 255 (включительно)|Максимальное количество попыток восстановления прерванного разорванное соединение перед прекращением. По умолчанию единый предпринимается попытка восстановить подключение, если нечитаемым. Значение 0 означает, что будет выполняться без повторного подключения.|1|  
|ConnectRetryInterval|Целое число от 1 до 60 (включительно)|Время в секундах между попытками создания потерянного подключения. Приложение будет пытаться сразу же повторно подключиться при обнаружении разорванное соединение и затем будет ожидать ConnectRetryInterval секунд перед повторной попыткой. Это ключевое слово учитывается, если ConnectRetryCount равно 0.|1|  
|База данных|String|Указывает имя базы данных, используемой для устанавливаемого соединения <sup>2</sup>.|База данных по умолчанию для используемого имени входа.|  
|Драйвер|String|Задает драйвер Microsoft ODBC, используемого для взаимодействия с SQL Server.<br /><br />Возможны следующие значения:<br />ODBC Driver 17 for SQL Server<br />ODBC Driver 13 for SQL Server<br />Драйвер ODBC 11 для SQL Server (только Windows).|Если не указано ключевое слово Driver, драйверы Майкрософт для PHP для SQL Server, пытаются найти поддерживаемые драйверы Microsoft ODBC в системе, начиная с последней версии ODBC и т. д.|  
|Шифрование|1 или **true** для включения шифрования.<br /><br />0 или **false** для отключения шифрования.|Указывает, выполняется ли шифрование обмена данными с SQL Server (1 или **true**) или нет (0 или **false**) <sup>3</sup>.|**false** (0)|  
|Failover_Partner|String|Указывает сервер и экземпляр зеркала базы данных (если они включены и настроены), используемые при недоступности сервера-источника.<br /><br />На использование Failover_Partner с MultiSubnetFailover налагаются определенные ограничения. Дополнительные сведения см. в разделе [Поддержка высокой доступности и аварийного восстановления](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|Значение не задано.|  
|keyStoreAuthentication|**KeyVaultPassword**<br /><br />**KeyVaultClientSecret**|Метод проверки подлинности для доступа к Azure Key Vault. Определяет, какие учетные данные используются с KeyStorePrincipalId и KeyStoreSecret. Дополнительные сведения см. в разделе [с помощью хранилища ключей Azure](../../connect/php/using-always-encrypted-php-drivers.md###using-azure-key-vault).|Не задано.|
|KeyStorePrincipalId|String|Идентификатор учетной записи требуется доступ к хранилищу ключей Azure. <br /><br />Если KeyStoreAuthentication **KeyVaultPassword**, это должно быть имя пользователя Azure Active Directory. <br /><br />Если KeyStoreAuthentication **KeyVaultClientSecret**, это должен быть идентификатор клиента приложения.|Не задано.|
|keyStoreSecret|String|Секретные учетные данные для учетной записи требуется доступ к хранилищу ключей Azure. <br /><br />Если KeyStoreAuthentication **KeyVaultPassword**, это должен быть пароль с Azure Active Directory. <br /><br />Если KeyStoreAuthentication **KeyVaultClientSecret**, это должен быть секрет клиента приложения.|Не задано.|
|LoginTimeout|Целое число (драйвер SQLSRV)<br /><br />Строка (драйвер PDO_SQLSRV)|Указывает количество секунд ожидания перед неудачным завершением соединения.|Время ожидания отсутствует.|  
|MultipleActiveResultSets|1 или **true** для использования множественных активных результирующих наборов.<br /><br />0 или **false** для отключения множественных активных результирующих наборов.|Отключает или явным образом включает поддержку множественных активных результирующих наборов (MARS).<br /><br />Дополнительные сведения см. в статье [Практическое руководство. Отключение множественных активных результирующих наборов &#40;функция MARS&#41;](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md).|true (1)|  
|MultiSubnetFailover|String|Всегда задавайте **multiSubnetFailover=Yes** при подключении к прослушивателю группы доступности [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] или экземпляру отказоустойчивого кластера [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. **multiSubnetFailover=yes** настраивает [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] на более быстрое обнаружение активного (в данный момент) сервера и подключение к нему. Возможными значениями являются Yes и No.<br /><br />Дополнительные сведения о [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] поддержка [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], см. в разделе [Поддержка высокой доступности и аварийного восстановления](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|нет|  
|PWD<br /><br />(не поддерживается в драйвере PDO_SQLSRV)|String|Указывает пароль, связанный с идентификатором пользователя, применяемый при подключении с использованием проверки подлинности SQL Server <sup>4</sup>.|Значение не задано.|  
|QuotedId|1 или **true** для использования правил SQL-92.<br /><br />0 или **false** для использования устаревших правил.|Указывает, следует ли использовать правила SQL-92 для нестандартных идентификаторов (1 или **true**) или устаревшие правила Transact-SQL (0 или **false**).|**true** (1)|  
|ReturnDatesAsStrings<br /><br />(не поддерживается в драйвере PDO_SQLSRV)|1 или **true** для возврата типов даты и времени в виде строк.<br /><br />0 или **false** для возврата типов даты и времени в виде типов **DateTime** PHP.|Извлекает типы даты и времени (datetime, date, time, datetime2 и datetimeoffset) в виде строк или типов PHP. При использовании драйвера PDO_SQLSRV даты возвращается в виде строк. Драйвер PDO_SQLSRV не включает тип **datetime**.<br /><br />Дополнительные сведения см. в статье [Практическое руководство. Получение типа даты и времени в виде строк с помощью драйвера SQLSRV](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md).|**false**|  
|Прокручиваемые курсоры|String|"Буферизовано" означает, что требуется клиентский (буферизированный) курсор, который позволяет кэшировать весь результирующий набор в памяти. Дополнительные сведения см. в статье [Типы курсоров &#40;драйвер SQLSRV&#41;](../../connect/php/cursor-types-sqlsrv-driver.md).|Курсор последовательного доступа|  
|Сервер<br /><br />(не поддерживается в драйвере SQLSRV)|String|Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для соединения.<br /><br />Вы также можете указать имя виртуальной сети для подключения к группе доступности AlwaysOn. Дополнительные сведения о [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] поддержка [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], см. в разделе [Поддержка высокой доступности и аварийного восстановления](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|Server является обязательным ключевым словом (хотя оно не обязательно должно стоять на первом месте в строке подключения). Если имя сервера не передается в ключевое слово, предпринимается попытка подключиться к локальному экземпляру.<br /><br />Значением, передаваемым в ключевое слово Server, может быть имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или IP-адрес экземпляра. Вы можете дополнительно указать номер порта (например, `sqlsrv:server=(local),1033`).<br /><br />Начиная с версии 3.0 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] , можно также указать экземпляр LocalDB с `server=(localdb)\instancename`. Дополнительные сведения см. в разделе [поддержка LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).|  
|TraceFile|String|Указывает путь для файла, используемый для трассировки данных.|Значение не задано.|  
|TraceOn|1 или **true** для включения трассировки.<br /><br />0 или **false** для отключения трассировки.|Указывает, включена (1 или **true**) или отключена (0 или **false**) трассировка ODBC для устанавливаемого соединения.|**false** (0)|  
|TransactionIsolation|Драйвер SQLSRV использует следующие значения:<br /><br />SQLSRV_TXN_READ_UNCOMMITTED<br /><br />SQLSRV_TXN_READ_COMMITTED<br /><br />SQLSRV_TXN_REPEATABLE_READ<br /><br />SQLSRV_TXN_SNAPSHOT<br /><br />SQLSRV_TXN_SERIALIZABLE<br /><br />Драйвер PDO_SQLSRV использует следующие значения:<br /><br />PDO::SQLSRV_TXN_READ_UNCOMMITTED<br /><br />PDO::SQLSRV_TXN_READ_COMMITTED<br /><br />PDO::SQLSRV_TXN_REPEATABLE_READ<br /><br />PDO::SQLSRV_TXN_SNAPSHOT<br /><br />PDO::SQLSRV_TXN_SERIALIZABLE|Указывает уровень изоляции транзакции.<br /><br />Дополнительные сведения об изоляции транзакций см. в статье [SET TRANSACTION ISOLATION LEVEL](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md) в документации по SQL Server.|SQLSRV_TXN_READ_COMMITTED<br /><br />или диспетчер конфигурации служб<br /><br />PDO::SQLSRV_TXN_READ_COMMITTED|  
|transparentNetworkIPResolution|**Enabled** (Включено) или **Disabled** (Отключено)|Влияет на последовательность соединения, устраняется первый IP-адрес имени узла не отвечает, и существует несколько IP-адресов, связанный с имени узла.<br /><br />Он взаимодействует с MultiSubnetFailover для предоставления последовательностей другое подключение. Дополнительные сведения см. в разделе [разрешение IP-адресов прозрачной сети](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md) или [с помощью прозрачного разрешение IP-адресов сети](https://docs.microsoft.com/sql/connect/odbc/using-transparent-network-ip-resolution).|Активировано|
|TrustServerCertificate|1 или **true** , чтобы доверять сертификату.<br /><br />0 или **false** , чтобы не доверять сертификату.|Указывает, должен ли клиент доверять самозаверяющему сертификату сервера (1 или **true**) или отклонить его (0 или **false**).|**false** (0)|  
|UID<br /><br />(не поддерживается в драйвере PDO_SQLSRV)|String|Указывает идентификатор пользователя, применяемый при подключении с использованием проверки подлинности SQL Server <sup>4</sup>.|Значение не задано.|  
|WSID|String|Задает имя компьютера для выполнения трассировки.|Значение не задано.|  

1. `ConnectionPooling` Атрибут не может использоваться для включения или отключения организация пулов соединений в Linux и Mac. См. [Организация пулов соединений (драйверы Майкрософт для PHP для SQL Server)](../../connect/php/connection-pooling-microsoft-drivers-for-php-for-sql-server.md).

2. Все запросы, выполняемые в рамках установленного подключения, направляются базе данных, заданной атрибутом *Database*. Однако если у пользователя есть соответствующие разрешения, возможен доступ к данным в других базах с помощью полного доменного имени. Например, если база данных *master* задана атрибутом подключения *Database*, полное доменное имя позволяет выполнить запрос Transact-SQL к таблице *AdventureWorks.HumanResources.Employee*.  

3. Включение *Encryption* может негативно повлиять на производительность некоторых приложений из-за необходимости выполнять дополнительные вычисления для шифрования данных.  

4. Экземпляр *UID* и *PWD* должны быть заданы при соединении с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  

Многие поддерживаемые ключи являются атрибутами строк подключения ODBC. Дополнительные сведения о строках подключения ODBC см. в статье [Использование ключевых слов строки подключения с SQL Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).

## <a name="see-also"></a>См. также:  
[Подключение к серверу](../../connect/php/connecting-to-the-server.md)  
