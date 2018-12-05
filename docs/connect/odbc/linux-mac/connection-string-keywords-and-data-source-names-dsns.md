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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c07b0bb4659f9b1b05573bf952842486f9ec72e
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52420455"
---
# <a name="connecting-to-sql-server"></a>Подключение к SQL Server
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

В этой статье описывается, как можно создать подключение к базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="connection-properties"></a>Свойства соединения  

См. в разделе [DSN и ключевых слов строки подключения и атрибуты](../../../connect/odbc/dsn-connection-string-attribute.md) для всех ключевых слов строки подключения и атрибуты, поддерживаемые в Linux и Mac

> [!IMPORTANT]  
> При подключении к базе данных, которая использует зеркальное отображение базы данных (имеет партнера по обеспечению отработки отказа), не указывайте имя базы данных в строке подключения. Вместо этого отправьте команду **use** *имя_базы_данных*, чтобы подключиться к базе данных перед выполнением запросов.  
  
Значение, передаваемое **драйвер** ключевое слово может принимать одно из следующих:  
  
-   именем, использованным при установке драйвера;

-   путем к библиотеке драйвера, которая была указана в INI-файле шаблона, используемого для установки драйвера.  

Чтобы создать имя DSN, создайте (при необходимости) и измените файл **~/.odbc.ini** (`.odbc.ini` в домашнем каталоге) для имени DSN пользователя доступна только для текущего пользователя, или `/etc/odbc.ini` для имени DSN системы (необходимые административные привилегии.) Ниже приведен пример файла, который показывает соответствующие записи для имени DSN:  

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

При необходимости можно указать протокол и порт для подключения к серверу. Например **Server = tcp:***servername***, 12345**. Обратите внимание, что единственный протокол, поддерживаемый драйверы Linux и macOS `tcp`.

Чтобы подключиться к именованному экземпляру через статический порт, используйте <b>Server=</b>*имя_сервера*,**номер_порта**. Подключение к динамическому порту не поддерживается.  

Кроме того, можно добавить сведения о DSN в файл шаблона и выполнить следующую команду, чтобы добавить его в `~/.odbc.ini`:
 - **Odbcinst -i -s -f** *template_file*  
 
Убедитесь, что драйвер работает с помощью `isql` для тестирования соединения, или можно использовать эту команду:
 - **master.INFORMATION_SCHEMA.TABLES bcp out файл OutFile.dat -S <server> - U <name> - P <password>**  

## <a name="using-secure-sockets-layer-ssl"></a>Использование протокола SSL  
Можно использовать протокол SSL для шифрования соединения с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. SSL защищает имена пользователей и пароли [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по сети. Кроме того, SSL проверяет идентификатор сервера для защиты от атак "злоумышленник в середине".  

Включение шифрования повышает безопасность за счет снижения производительности.

Дополнительные сведения см. в разделе [шифрование соединений с SQL Server](https://go.microsoft.com/fwlink/?LinkId=220900) и [использование шифрования без проверки](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation).

Независимо от параметров для **Encrypt** и **TrustServerCertificate**учетные данные входа на сервер (имя пользователя и пароль) всегда шифруются. Следующая таблица показывает эффект от параметров **Encrypt** и **TrustServerCertificate** .  

||**TrustServerCertificate = нет**|**TrustServerCertificate = yes**|  
|-|-------------------------------------|------------------------------------|  
|**Encrypt=no**|Сертификат сервера не проверяется.<br /><br />Данные, передаваемые между клиентом и сервером, не шифруются.|Сертификат сервера не проверяется.<br /><br />Данные, передаваемые между клиентом и сервером, не шифруются.|  
|**Encrypt=yes**|Сертификат сервера проверяется.<br /><br />Данные, передаваемые между клиентом и сервером, шифруются.<br /><br />Имя (или IP-адрес) в общем имени субъекта (CN) или альтернативном имени субъекта (SAN) в SSL-сертификате [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должно точно совпадать с именем сервера (или IP-адресом), указанным в строке подключения.|Сертификат сервера не проверяется.<br /><br />Данные, передаваемые между клиентом и сервером, шифруются.|  

По умолчанию зашифрованные соединения всегда проверяют сертификат сервера. Тем не менее, при подключении к серверу с самозаверяющий сертификат, также добавьте `TrustServerCertificate` параметр для обхода проверки сертификата со списком доверенных центров сертификации:  

```  
Driver={ODBC Driver 13 for SQL Server};Server=ServerNameHere;Encrypt=YES;TrustServerCertificate=YES  
```  
  
SSL использует библиотеку OpenSSL. Следующая таблица содержит минимально поддерживаемые версии OpenSSL, а также расположения хранилища доверия сертификатов по умолчанию для каждой платформы:

|Платформа|Минимальная версия OpenSSL|Расположение хранилища доверия сертификатов по умолчанию|  
|------------|---------------------------|--------------------------------------------|
|Debian 9|1.1.0|/etc/ssl/certs|
|Debian 8.71 |1.0.1|/etc/ssl/certs|
|macOS 10.13|1.0.2|/usr/local/etc/OpenSSL/certs|
|macOS 10.12|1.0.2|/usr/local/etc/OpenSSL/certs|
|OS X 10.11|1.0.2|/usr/local/etc/OpenSSL/certs|
|Red Hat Enterprise Linux 7|1.0.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 6|1.0.0-10|/etc/pki/tls/cert.pem|
|SuSE Linux Enterprise 12 |1.0.1|/etc/ssl/certs|
|SuSE Linux Enterprise 11 |0.9.8|/etc/ssl/certs|
|Ubuntu 17.10 |1.0.2|/etc/ssl/certs|
|Ubuntu 16.10 |1.0.2|/etc/ssl/certs|
|Ubuntu 16.04 |1.0.2|/etc/ssl/certs|
  
Можно также указать шифрование в строке подключения в `Encrypt` параметр при использовании **SQLDriverConnect** для подключения.

## <a name="see-also"></a>См. также:  
[Установка Microsoft ODBC Driver for SQL Server в Linux и macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)  
[Указания по программированию](../../../connect/odbc/linux-mac/programming-guidelines.md)
