---
title: Шифрование подключений к SQL Server в Linux
description: В этой статье описывается шифрование соединений с SQL Server в Linux.
ms.date: 01/30/2018
author: vin-yu
ms.author: vinsonyu
ms.reviewer: vanto
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
helpviewer_keywords:
- Linux, encrypted connections
ms.openlocfilehash: 3f658ba8723b142f37763ea8b4f0c8f7b0c5d0e1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68077288"
---
# <a name="encrypting-connections-to-sql-server-on-linux"></a>Шифрование подключений к SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux безопасности транспортного уровня (TLS) для шифрования можно использовать данные, передаваемые по сети между клиентским приложением и экземпляром [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поддерживает те же протоколы TLS в Windows и Linux: TLS 1.2, 1.1 и 1.0. Тем не менее, действия по настройке TLS относящиеся к операционной системе, на котором [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] запущена.  

## <a name="requirements-for-certificates"></a>Требования к сертификатам 
Перед началом работы необходимо убедиться, что сертификаты соответствовать следующим требованиям:
- Текущее системное время должен быть после действителен с свойства сертификата и перед допустимо для свойства сертификата.
- Сертификат должен быть предназначен для проверки подлинности сервера. Для этого требуется свойство расширенного использования ключа сертификата, проверку подлинности сервера (1.3.6.1.5.5.7.3.1).
- Сертификат должен быть создан с помощью параметра KeySpec AT_KEYEXCHANGE. Как правило свойство использования ключа сертификата (KEY_USAGE) также включает шифрование ключей (CERT_KEY_ENCIPHERMENT_KEY_USAGE).
- Свойство субъекта сертификата должно указывать, что общее имя (CN) совпадает с именем узла или полное доменное имя (FQDN) сервера. Примечание. Поддерживаются групповые сертификаты.

## <a name="configuring-the-openssl-libraries-for-use-optional"></a>Настройка библиотеки OpenSSL для использования (необязательно)
Можно создать символические ссылки в `/opt/mssql/lib/` каталог, который ссылается `libcrypto.so` и `libssl.so` библиотек следует использовать для шифрования. Это полезно, если нужно, чтобы SQL Server для использования определенной версии OpenSSL используемый по умолчанию, предоставляемые системой. Если эти символических ссылок не существуют, SQL Server будет загружать библиотеки OpenSSL по умолчанию, настроенного в системе.

Эти символические ссылки должен быть назван `libcrypto.so` и `libssl.so` и помещено в `/opt/mssql/lib/` каталога.

## <a name="overview"></a>Обзор
TLS используется для шифрования подключения из клиентского приложения к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. При правильной настройке TLS обеспечивает конфиденциальность и целостность данных для обмена данными между клиентом и сервером.  TLS-подключения может быть клиент или сервер инициировал. 

## <a name="client-initiated-encryption"></a>Клиент инициировал шифрования 
- **Создание сертификата** (/ CN должны соответствовать вашей полное доменное имя узла SQL Server)

> [!NOTE]
> Например, мы используем самозаверяющего сертификата это не следует в рабочей среде. Следует использовать сертификаты ЦС. 

        openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
        sudo chown mssql:mssql mssql.pem mssql.key 
        sudo chmod 600 mssql.pem mssql.key   
        sudo mv mssql.pem /etc/ssl/certs/ 
        sudo mv mssql.key /etc/ssl/private/ 

- **Настройка SQL Server**

        systemctl stop mssql-server 
        cat /var/opt/mssql/mssql.conf 
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssql.pem 
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssql.key 
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 0 

- **Регистрация сертификата на клиентском компьютере (Windows, Linux или macOS)**

    -   Если вы используете подписанный сертификат ЦС, необходимо скопировать сертификат центра сертификации (ЦС) вместо сертификата пользователя на клиентском компьютере. 
    -   Если вы используете самозаверяющий сертификат, просто скопируйте PEM-файл в следующие папки, соответствующей для распространения и выполните команды, чтобы включить их 
        - **Ubuntu**: Копирование сертификатов ```/usr/share/ca-certificates/``` переименования расширение на CRT использовать сертификаты ЦС dpkg reconfigure для включения его как системный ЦС сертификат. 
        - **RHEL**: Копирование сертификатов ```/etc/pki/ca-trust/source/anchors/``` использовать ```update-ca-trust``` для включения его как системный ЦС сертификат.
        - **SUSE**: Копирование сертификатов ```/usr/share/pki/trust/anchors/``` использовать ```update-ca-certificates``` для включения его как системный ЦС сертификат.
        - **Windows**:  Импорта PEM-файл в качестве сертификата учетной записью текущего пользователя "->" Доверенные корневые центры сертификации "->" сертификаты
        - **macOS**: 
           - Копирование сертификатов ```/usr/local/etc/openssl/certs```
           - Выполните следующую команду, чтобы получить хэш-значение: ```/usr/local/Cellar/openssql/1.0.2l/openssql x509 -hash -in mssql.pem -noout```
           - Переименуйте cert значению. Например: ```mv mssql.pem dc2dd900.0```. Убедитесь, что dc2dd900.0 находится в ```/usr/local/etc/openssl/certs```
    
-   **Примеры строк подключения** 

    - **[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)]**   
  ![Диалоговое окно подключения SSMS](media/sql-server-linux-encrypted-connections/ssms-encrypt-connection.png "диалоговое окно подключения SSMS")  
  
    - **SQLCMD** 

            sqlcmd  -S <sqlhostname> -N -U sa -P '<YourPassword>' 
    - **ADO.NET** 

            "Encrypt=True; TrustServerCertificate=False;" 
    - **интерфейс ODBC** 

            "Encrypt=Yes; TrustServerCertificate=no;" 
    - **JDBC** 
    
            "encrypt=true; trustServerCertificate=false;" 

## <a name="server-initiated-encryption"></a>Инициированные сервером шифрования 

- **Создание сертификата** (/ CN должно совпадать полное доменное имя узла сервера SQL)
        
        openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
        sudo chown mssql:mssql mssql.pem mssql.key 
        sudo chmod 600 mssql.pem mssql.key   
        sudo mv mssql.pem /etc/ssl/certs/ 
        sudo mv mssql.key /etc/ssl/private/ 

- **Настройка SQL Server**

        systemctl stop mssql-server 
        cat /var/opt/mssql/mssql.conf 
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssql.pem 
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssql.key 
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 1 
        
-   **Примеры строк подключения** 

    - **SQLCMD**

            sqlcmd  -S <sqlhostname> -U sa -P '<YourPassword>' 
    - **ADO.NET** 

            "Encrypt=False; TrustServerCertificate=False;" 
    - **интерфейс ODBC** 

            "Encrypt=no; TrustServerCertificate=no;"  
    - **JDBC** 
    
            "encrypt=false; trustServerCertificate=false;" 
            
> [!NOTE]
> Задайте **TrustServerCertificate** значение true, если клиент не может подключиться к ЦС для проверки подлинности сертификата

## <a name="common-connection-errors"></a>Распространенные ошибки подключения  

|Сообщение об ошибке |Fix |
|--- |--- |
|Цепочка сертификатов выпущена центром сертификации, не является доверенным.  |Эта ошибка возникает, когда клиенты не смогут проверить подпись сертификата, предоставленного SQL Server во время подтверждения TLS. Убедитесь, что клиент доверяет либо [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] сертификат непосредственно или ЦС, который подписал сертификат сервера SQL. |
|Указано неверное имя целевого участника.  |Убедитесь, что поле общего имени сертификата SQL Server соответствует имени сервера, указанного в строке подключения клиента. |  
|существующее соединение было принудительно завершено удаленным узлом. |Эта ошибка может возникать, когда клиент не поддерживает версию протокола TLS, требуется SQL Server. Например если [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] должен требовать TLS 1.2, убедитесь, что ваши клиенты также поддерживают протокол TLS 1.2. |
| | |   
