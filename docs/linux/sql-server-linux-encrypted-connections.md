---
title: "Шифрование соединений с SQL Server в Linux | Документы Microsoft"
description: "В этом разделе описывается шифрование соединений с SQL Server в Linux."
author: tmullaney
ms.date: 10/02/2017
ms.author: meetb;rickbyh
manager: jhubbard
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
helpviewer_keywords:
- Linux, encrypted connections
ms.translationtype: MT
ms.sourcegitcommit: 41c2caf816ca412e4a6048713dc66f97da5155ae
ms.openlocfilehash: d6beb6350c0d48d35cb3153c2df8eebaec0e4f34
ms.contentlocale: ru-ru
ms.lasthandoff: 10/07/2017

---
# <a name="encrypting-connections-to-sql-server-on-linux"></a>Шифрование соединений с SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]в Linux используется Transport Layer Security (TLS) для шифрования данных, передаваемых по сети между клиентским приложением и экземпляром [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]поддерживает такие же протоколы TLS в Windows и Linux: TLS 1.0, 1.1 и 1.2. Тем не менее, действия по настройке TLS относятся к операционной системе, на котором [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] запущена.  

## <a name="requirements-for-certificates"></a>Требования к сертификатам 
Прежде чем начать, необходимо убедитесь, что ваши сертификаты соответствовать следующим требованиям:
- Текущее системное время должен быть после действителен свойства сертификата и перед допустимо для свойства сертификата.
- Сертификат должен быть предназначен для проверки подлинности сервера. Для этого необходимо свойство расширенного использования ключа сертификата, чтобы использовать проверку подлинности сервера (1.3.6.1.5.5.7.3.1).
- Сертификат должен создаваться с помощью параметра KeySpec AT_KEYEXCHANGE. Как правило свойство использования ключа сертификата (KEY_USAGE) также будет содержать шифрование ключей (CERT_KEY_ENCIPHERMENT_KEY_USAGE).
- Свойство субъекта сертификата необходимо указать, что общее имя (CN) совпадает имя узла или полное доменное имя (FQDN) сервера. Примечание: поддерживаются знаки подстановки сертификаты. 

## <a name="overview"></a>Обзор
TLS используется для шифрования подключения из клиентского приложения для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. При правильной настройке TLS обеспечивает конфиденциальность и целостность данных для обмена данными между клиентом и сервером.  TLS-подключения может быть клиент initited intiated или сервера. 


## <a name="client-initiated-encryption"></a>Шифрование, инициированное клиентом 
- **Создание сертификата** (/ CN должен соответствовать полное доменное имя узла сервера SQL)

> [!NOTE]
> В этом примере, что мы используем самозаверяющего сертификата это не будет использовать для рабочих сценариев. Следует использовать сертификаты ЦС. 

        openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
        sudo chown mssql:mssql mssql.pem mssql.key 
        sudo chmod 600 mssql.pem mssql.key   
        sudo mv mssql.pem /etc/ssl/certs/ 
        sudo mv mssql.key /etc/ssl/private/ 

- **Настройка SQL Server**

        systemctl stop mssql-server 
        cat /var/opt/mssql/mssql.conf 
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssqlfqdn.pem 
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssqlfqdn.key 
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 0 

- **Регистрация сертификата на клиентском компьютере (Windows, Linux или macOS)**

    -   При использовании сертификата, подписанного ЦС, вам необходимо скопировать сертификат центра сертификации (ЦС) вместо сертификата пользователя на клиентском компьютере. 
    -   Если используется самозаверяющий сертификат, просто скопируйте PEM-файл следующие папки, соответствующей для распространения и выполнять команды для их включения 
        - **Ubuntu** : копирование сертификатов ```/usr/share/ca-certificates/``` расширение переименования .crt используйте сертификаты ЦС dpkg reconfigure для его включения как системный ЦС сертификат. 
        - **RHEL** : копирование сертификатов ```/etc/pki/ca-trust/source/anchors/``` использовать ```update-ca-trust``` включить, то в качестве системы ЦС сертификата.
        - **SUSE** : копирование сертификатов ```/usr/share/pki/trust/anchors/``` использовать ```update-ca-certificates``` для включения его как системный ЦС сертификат.
        - **Windows**: Импорт PEM-файл в качестве сертификата в папке current user "->" Доверенные корневые центры сертификации -> сертификаты
        - **macOS**: 
           - Скопируйте сертификат для```/usr/local/etc/openssl/certs```
           - Выполните следующую команду, чтобы получить хэш-значение:```/usr/local/Cellar/openssql/1.0.2l/openssql x509 -hash -in mssql.pem -noout```
           - Переименуйте cert значение. Например: ```mv mssql.pem dc2dd900.0```. Убедитесь, что возможности dc2dd900.0```/usr/local/etc/openssl/certs```
    
-   **Примеры строк подключения** 

    - **[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)]**   
  ![Диалоговое окно соединения SSMS](media/sql-server-linux-encrypted-connections/ssms-encrypt-connection.png "диалогового окна соединения в среде SSMS")  
  
    - **ПРОГРАММА SQLCMD** 

            sqlcmd  -S <sqlhostname> -N -U sa -P '<YourPassword>' 
    - **ADO.NET** 

            "Encrypt=True; TrustServerCertificate=False;" 
    - **ODBC** 

            "Encrypt=Yes; TrustServerCertificate=no;" 
    - **JDBC** 
    
            "encrypt=true; trustServerCertificate=false;" 

## <a name="server-initiated-encryption"></a>Инициированные сервером шифрования 

- **Создание сертификата** (/ CN должен соответствовать полное доменное имя узла сервера SQL)
        
        openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
        sudo chown mssql:mssql mssql.pem mssql.key 
        sudo chmod 600 mssql.pem mssql.key   
        sudo mv mssql.pem /etc/ssl/certs/ 
        sudo mv mssql.key /etc/ssl/private/ 

- **Настройка SQL Server**

        systemctl stop mssql-server 
        cat /var/opt/mssql/mssql.conf 
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssqlfqdn.pem 
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssqlfqdn.key 
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 1 
        
-   **Примеры строк подключения** 

    - **ПРОГРАММА SQLCMD**

            sqlcmd  -S <sqlhostname> -U sa -P '<YourPassword>' 
    - **ADO.NET** 

            "Encrypt=False; TrustServerCertificate=False;" 
    - **ODBC** 

            "Encrypt=no; TrustServerCertificate=no;"  
    - **JDBC** 
    
            "encrypt=false; trustServerCertificate=false;" 
            
> [!NOTE]
> Задать **TrustServerCertificate** значение True, если клиенту не удается подключиться к ЦС для проверки подлинности сертификата

## <a name="common-connection-errors"></a>Распространенные ошибки подключения  

|Сообщение об ошибке |Fix |
|--- |--- |
|Цепочка сертификатов был выдан центром сертификации, не является доверенным.  |Эта ошибка возникает, когда клиенты не смогут проверить подпись сертификата, предоставляемого SQL Server во время подтверждения TLS. Убедитесь, что клиент доверяет либо [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] сертификата непосредственно или ЦС, который подписал сертификат сервера SQL. |
|Неверное имя целевого субъекта.  |Убедитесь, что соответствие поля Общее имя сертификата SQL Server имя сервера, указанное в строке подключения клиента. |  
|существующее соединение было принудительно завершено удаленным узлом. |Эта ошибка может возникать, когда клиент не поддерживает версию протокола TLS, необходимые для SQL Server. Например если [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] настроен на требуется TLS 1.2, убедитесь, что ваши клиенты также поддерживают протокол TLS 1.2. |
| | |   

