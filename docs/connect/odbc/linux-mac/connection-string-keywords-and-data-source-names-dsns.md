---
title: Подключение к SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data source names
- connection string keywords
- DSNs
ms.assetid: f95cdbce-e7c2-4e56-a9f7-8fa3a920a125
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d323481aaf3e12da9786a3b02f21f47c3c98f7cf
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924532"
---
# <a name="connecting-to-sql-server"></a>Подключение к SQL Server
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

В этой статье описывается, как можно создать подключение к базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="connection-properties"></a>Свойства подключения  

Ключевые слова и атрибуты строки подключения и имени DSN, поддерживаемые в Linux и Mac, можно найти [здесь](../../../connect/odbc/dsn-connection-string-attribute.md).

> [!IMPORTANT]  
> При подключении к базе данных, которая использует зеркальное отображение базы данных (имеет партнера по обеспечению отработки отказа), не указывайте имя базы данных в строке подключения. Вместо этого отправьте команду **use**_имя_базы_данных_, чтобы подключиться к базе данных перед выполнением запросов.  
  
Значение, передаваемое в ключевое слово **Driver**, может быть одним из следующих:  
  
-   именем, использованным при установке драйвера;

-   путем к библиотеке драйвера, которая была указана в INI-файле шаблона, используемого для установки драйвера.  

Чтобы создать имя DSN, создайте (при необходимости) и измените файл **~/.odbc.ini** (`.odbc.ini` в домашнем каталоге) для имени DSN пользователя, доступного только для текущего пользователя, или `/etc/odbc.ini` для системного имени DSN (требуются права администратора). Ниже приведен пример файла, который показывает минимальное количество необходимых записей для имени DSN:  

```  
[MSSQLTest]  
Driver = ODBC Driver 13 for SQL Server  
Server = [protocol:]server[,port]  
#   
# Note:  
# Port is not a valid keyword in the odbc.ini file  
# for the Microsoft ODBC driver on Linux or macOS
#  
```  

При необходимости можно указать протокол и порт для подключения к серверу. Например, **Server = tcp:** _имя_сервера_ **,12345**. Обратите внимание, что единственным протоколом, поддерживаемым драйверами Linux и macOS, является `tcp`.

Чтобы подключиться к именованному экземпляру через статический порт, используйте <b>Server=</b>*имя_сервера*,**номер_порта**. Подключение к динамическому порту не поддерживается в версиях ниже 17.4.

Кроме того, можно добавить сведения о DSN в файл шаблона и выполнить следующую команду, чтобы добавить его в `~/.odbc.ini`:
 - **odbcinst -i -s -f** _файл_шаблона_  
 
Можно проверить, что драйвер работает, используя `isql` для проверки подключения или следующую команду:
 - **bcp master.INFORMATION_SCHEMA.TABLES out OutFile.dat -S <server> -U <name> -P <password>**  

## <a name="using-secure-sockets-layer-ssl"></a>Использование протокола SSL  
Для шифрования подключений к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] можно использовать протокол SSL. SSL защищает имена пользователей и пароли [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по сети. Кроме того, SSL проверяет идентификатор сервера для защиты от атак "злоумышленник в середине".  

Включение шифрования повышает безопасность за счет снижения производительности.

См. сведения о [шифровании подключений в SQL Server](https://go.microsoft.com/fwlink/?LinkId=220900) и [использовании шифрования без проверки](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation).

Независимо от параметров для **Encrypt** и **TrustServerCertificate**учетные данные входа на сервер (имя пользователя и пароль) всегда шифруются. Следующая таблица показывает эффект от параметров **Encrypt** и **TrustServerCertificate** .  

||**TrustServerCertificate=no**|**TrustServerCertificate=yes**|  
|-|-------------------------------------|------------------------------------|  
|**Encrypt=no**|Сертификат сервера не проверяется.<br /><br />Данные, передаваемые между клиентом и сервером, не шифруются.|Сертификат сервера не проверяется.<br /><br />Данные, передаваемые между клиентом и сервером, не шифруются.|  
|**Encrypt=yes**|Сертификат сервера проверяется.<br /><br />Данные, передаваемые между клиентом и сервером, шифруются.<br /><br />Имя (или IP-адрес) в общем имени субъекта (CN) или альтернативном имени субъекта (SAN) в SSL-сертификате [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должно точно совпадать с именем (или IP-адресом) сервера, указанным в строке подключения.|Сертификат сервера не проверяется.<br /><br />Данные, передаваемые между клиентом и сервером, шифруются.|  

По умолчанию зашифрованные соединения всегда проверяют сертификат сервера. Однако при подключении к серверу с самозаверяющим сертификатом также добавьте параметр `TrustServerCertificate`, чтобы обойти проверку сертификата по списку доверенных центров сертификации:  

```  
Driver={ODBC Driver 13 for SQL Server};Server=ServerNameHere;Encrypt=YES;TrustServerCertificate=YES  
```  
  
SSL использует библиотеку OpenSSL. Следующая таблица содержит минимально поддерживаемые версии OpenSSL, а также расположения хранилища доверия сертификатов по умолчанию для каждой платформы:

|Платформа|Минимальная версия OpenSSL|Расположение хранилища доверия сертификатов по умолчанию|  
|------------|---------------------------|--------------------------------------------|
|Debian 10|1.1.1|/etc/ssl/certs|
|Debian 9|1.1.0|/etc/ssl/certs|
|Debian 8.71|1.0.1|/etc/ssl/certs|
|OS X 10.11, macOS 10.12, 10.13, 10.14|1.0.2|/usr/local/etc/openssl/certs|
|Red Hat Enterprise Linux 8|1.1.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 7|1.0.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 6|1.0.0-10|/etc/pki/tls/cert.pem|
|SUSE Linux Enterprise 15|1.1.0|/etc/ssl/certs|
|SUSE Linux Enterprise 11, 12|1.0.1|/etc/ssl/certs|
|Ubuntu 18.10, 19.04|1.1.1|/etc/ssl/certs|
|Ubuntu 18.04|1.1.0|/etc/ssl/certs|
|Ubuntu 16.04, 16.10, 17.10|1.0.2|/etc/ssl/certs|
|Ubuntu 14.04|1.0.1|/etc/ssl/certs|

Можно также указать шифрование в строке подключения с помощью параметра `Encrypt` при использовании **SQLDriverConnect** для подключения.

## <a name="adjusting-the-tcp-keep-alive-settings"></a>Настройка параметров поддержания активности TCP

Начиная с ODBC Driver версии 17.4, можно настроить частоту отправки драйвером пакетов проверки активности и их пересылки, если ответ не получен.
Чтобы настроить, добавьте следующие параметры в раздел драйвера в `odbcinst.ini` или в раздел имени DSN в `odbc.ini`. При подключении с помощью имени DSN драйвер будет использовать параметры в разделе имени DSN, если они есть. В противном случае или если подключение выполняется только со строкой подключения, драйвер будет использовать параметры из раздела драйвера в `odbcinst.ini`. Если параметр отсутствует в обоих расположениях, драйвер использует значение по умолчанию.

- `KeepAlive=<integer>` управляет частотой попыток протокола TCP проверить работоспособность неактивного подключения путем отправки пакета keep-alive. Значение по умолчанию — **30** секунд.

- `KeepAliveInterval=<integer>` определяет интервал, разделяющий повторные передачи пакета keep-alive, пока не происходит получение ответа.  Значение по умолчанию составляет **15** секунд.

## <a name="see-also"></a>См. также:

- [Установка Microsoft ODBC Driver for SQL Server в Linux](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Установка Microsoft ODBC Driver for SQL Server в macOS](../../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md)
- [Указания по программированию](../../../connect/odbc/linux-mac/programming-guidelines.md)
