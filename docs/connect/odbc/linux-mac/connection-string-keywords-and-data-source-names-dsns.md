---
title: "Ключевые слова строки подключения и источника данных (DSN) имена | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data source names
- connection string keywords
- DSNs
ms.assetid: f95cdbce-e7c2-4e56-a9f7-8fa3a920a125
caps.latest.revision: 41
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 508fcb62b7cf9ccd78c04b869add7acccb14f258
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="connection-string-keywords-and-data-source-names-dsns"></a>Ключевые слова строки подключения и имена источников данных (DSN)
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

В этом разделе обсуждается, как можно создать подключение к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных.  
  
## <a name="connection-properties"></a>Свойства соединения  
Для этого выпуска [!INCLUDE[msCoName](../../../includes/msconame_md.md)] драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] на Linux или macOS, можно использовать следующие ключевые слова соединения:  
  
||||||  
|-|-|-|-|-|  
|`Addr`|`Address`|`ApplicationIntent`|`AutoTranslate`|`Database`|
|`Driver`|`DSN`|`Encrypt`|`FileDSN`|`MARS_Connection`|  
|`MultiSubnetFailover`|`PWD`|`Server`|`Trusted_Connection`|`TrustServerCertificate`|  
|`UID`|`WSID`|`ColumnEncryption`|`TransparentNetworkIPResolution`||  

> [!IMPORTANT]  
> При подключении к базе данных, которая использует зеркальное отображение базы данных (имеет партнера по обеспечению отработки отказа), не указывайте имя базы данных в строке подключения. Вместо этого отправить **использовать** *имя_базы_данных* команду, чтобы подключиться к базе данных перед выполнением запросов.  
  
Дополнительные сведения об этих ключевых словах см. в разделе ODBC статьи [Использование ключевых слов строки подключения с SQL Server Native Client](http://go.microsoft.com/fwlink/?LinkID=126696).  
  
Значение, передаваемое **драйвер** ключевое слово может принимать одно из следующих действий:  
  
-   именем, использованным при установке драйвера;

-   Путь к библиотеке драйвер, который был указан в INI-файле шаблона, используемый для установки драйвера.  

Чтобы создать имя DSN, создайте (при необходимости) и измените файл **~/.odbc.ini** (`.odbc.ini` в домашнем каталоге) для имени DSN пользователя, доступной только для текущего пользователя или `/etc/odbc.ini` для системный DSN (административные привилегии, необходимые.) Ниже приведен пример файла, который показывает минимальные необходимые записи для имени DSN:  

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

При необходимости можно указать протокол и порт для подключения к серверу. Например **Server = tcp:***servername***, 12345**. Обратите внимание, что драйвер Linux и macOS поддерживают только протокол `tcp`.

Чтобы подключиться к именованному экземпляру через статический порт, используйте <b>Server =</b>*servername*,**Номер_порта**. Подключение к динамическому порту не поддерживается.  

Кроме того, можно добавить сведения об имени DSN в файл шаблона и выполните следующую команду, чтобы добавить его в `~/.odbc.ini` :
 - **Odbcinst -i -f -s** *template_file*  
 
Убедитесь, что драйвер работает с помощью `isql` для проверки соединения, или можно использовать эту команду:
 - **master.INFORMATION_SCHEMA.TABLES bcp out файл OutFile.dat -S <server> - U <name> - P<password>**  

## <a name="using-secure-sockets-layer-ssl"></a>Использование протокола SSL  
Secure Sockets Layer (SSL) можно использовать для шифрования соединения с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. SSL защищает [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] имен пользователей и паролей по сети. Кроме того, SSL проверяет идентификатор сервера для защиты от атак "злоумышленник в середине".  

Включение шифрования повышает безопасность за счет снижения производительности.

Дополнительные сведения см. в разделе [шифрование соединений с SQL Server](http://go.microsoft.com/fwlink/?LinkId=220900) и [использование шифрования без проверки](https://docs.microsoft.com/en-us/sql/relational-databases/native-client/features/using-encryption-without-validation).

Независимо от параметров для **Encrypt** и **TrustServerCertificate**учетные данные входа на сервер (имя пользователя и пароль) всегда шифруются. Следующая таблица показывает эффект от параметров **Encrypt** и **TrustServerCertificate** .  

||**TrustServerCertificate = нет**|**TrustServerCertificate = yes**|  
|-|-------------------------------------|------------------------------------|  
|**Шифрование = нет**|Сертификат сервера не проверяется.<br /><br />Данные, передаваемые между клиентом и сервером, не шифруются.|Сертификат сервера не проверяется.<br /><br />Данные, передаваемые между клиентом и сервером, не шифруются.|  
|**Шифрование = Да**|Сертификат сервера проверяется.<br /><br />Данные, передаваемые между клиентом и сервером, шифруются.<br /><br />Имя (или IP-адрес) в общее имя субъекта (CN) или альтернативное имя субъекта (SAN) в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] SSL-сертификат должен совпадать с сервера имя (или IP-адрес) указан в строке подключения.|Сертификат сервера не проверяется.<br /><br />Данные, передаваемые между клиентом и сервером, шифруются.|  

По умолчанию зашифрованные соединения всегда проверяют сертификат сервера. Однако при подключении к серверу, имеет сертификат с собственной подписью, также добавить `TrustServerCertificate` возможность пропускать проверки сертификата со списком доверенных ЦС:  

```  
Driver={ODBC Driver 13 for SQL Server};Server=ServerNameHere;Encrypt=YES;TrustServerCertificate=YES  
```  
  
SSL использует библиотеку OpenSSL. Следующая таблица содержит минимально поддерживаемые версии OpenSSL, а также расположения хранилища доверия сертификатов по умолчанию для каждой платформы:

|Платформа|Минимальная версия OpenSSL|Расположение хранилища доверия сертификатов по умолчанию|  
|------------|---------------------------|--------------------------------------------|
|Debian 8.71 |1.0.1t|/etc/ssl/certs|
|macOS 10.12|1.0.2k|/usr/local/etc/OpenSSL/certs|
|OS X 10.11|1.0.2j|/usr/local/etc/OpenSSL/certs|
|Red Hat Enterprise Linux 6|1.0.0-10|/etc/pki/tls/cert.pem|  
|Red Hat Enterprise Linux 7|1.0.1E|/etc/pki/tls/cert.pem|
|SuSE Linux Enterprise 12 |1.0.1I|/etc/ssl/certs|
|Ubuntu 15.10 |1.0.2D|/etc/ssl/certs|
|Ubuntu 16.04 |1.0.2g|/etc/ssl/certs|
|Ubuntu 16.10 |1.0.2g|/etc/ssl/certs|
  
Шифрование можно также указать в строке подключения, используя `Encrypt` параметр при использовании **SQLDriverConnect** для подключения.

## <a name="see-also"></a>См. также:  
[Установка Microsoft ODBC Driver for SQL Server для Linux и macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)  
[Указания по программированию](../../../connect/odbc/linux-mac/programming-guidelines.md)

