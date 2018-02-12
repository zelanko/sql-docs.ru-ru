---
title: "Подключение к SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data source names
- connection string keywords
- DSNs
ms.assetid: f95cdbce-e7c2-4e56-a9f7-8fa3a920a125
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: b6ad6278da1a3e325356058df51238dc34018bf0
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2018
---
# <a name="connecting-to-sql-server"></a>Подключение к SQL Server
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

В этом разделе обсуждается, как можно создать подключение к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных.  
  
## <a name="connection-properties"></a>Свойства соединения  

В разделе [DSN и ключевых слов строки подключения и атрибуты](../../../connect/odbc/dsn-connection-string-attribute.md) для всех ключевых слов строки подключения и атрибуты, поддерживаемые на Mac и Linux

> [!IMPORTANT]  
> При подключении к базе данных, которая использует зеркальное отображение базы данных (имеет партнера по обеспечению отработки отказа), не указывайте имя базы данных в строке подключения. Вместо этого отправить **использовать** *имя_базы_данных* команду, чтобы подключиться к базе данных перед выполнением запросов.  
  
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

||**TrustServerCertificate=no**|**TrustServerCertificate = yes**|  
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
|Debian 9|1.1.0|/etc/ssl/certs|
|Debian 8.71 |1.0.1|/etc/ssl/certs|
|macOS 10.13|1.0.2|/usr/local/etc/openssl/certs|
|macOS 10.12|1.0.2|/usr/local/etc/openssl/certs|
|OS X 10.11|1.0.2|/usr/local/etc/openssl/certs|
|Red Hat Enterprise Linux 7|1.0.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 6|1.0.0-10|/etc/pki/tls/cert.pem|
|SuSE Linux Enterprise 12 |1.0.1|/etc/ssl/certs|
|SuSE Linux Enterprise 11 |0.9.8|/etc/ssl/certs|
|Ubuntu 17.10 |1.0.2|/etc/ssl/certs|
|Ubuntu 16.10 |1.0.2|/etc/ssl/certs|
|Ubuntu 16.04 |1.0.2|/etc/ssl/certs|
  
Шифрование можно также указать в строке подключения, используя `Encrypt` параметр при использовании **SQLDriverConnect** для подключения.

## <a name="see-also"></a>См. также  
[Установка Microsoft ODBC Driver for SQL Server для Linux и macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)  
[Указания по программированию](../../../connect/odbc/linux-mac/programming-guidelines.md)
