---
title: "Шифрование соединений с SQL Server в Linux | Документы Microsoft"
description: "В этом разделе описывается шифрование соединений с SQL Server в Linux."
author: tmullaney
ms.date: 06/14/2017
ms.author: thmullan;rickbyh
manager: jhubbard
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
helpviewer_keywords:
- Linux, encrypted connections
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 47a15701730019aaf166743c47c606aa2059b7fe
ms.contentlocale: ru-ru
ms.lasthandoff: 08/28/2017

---
# <a name="encrypting-connections-to-sql-server-on-linux"></a>Шифрование соединений с SQL Server в Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]в Linux используется Transport Layer Security (TLS) для шифрования данных, передаваемых по сети между клиентским приложением и экземпляром [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]поддерживает такие же протоколы TLS в Windows и Linux: TLS 1.0, 1.1 и 1.2. Тем не менее, действия по настройке TLS относятся к операционной системе, на котором [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] запущена.  
 
## <a name="typical-scenario"></a>Типичный сценарий 
TLS используется для шифрования подключения из клиентского приложения для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. При правильной настройке TLS обеспечивает конфиденциальность и целостность данных для обмена данными между клиентом и сервером.  
Следующие шаги описывают типичный сценарий:  

1. Администратор базы данных создает закрытый ключ и сертификат подписи запроса (CSR). Общее имя CSR должен соответствовать имени сервера, клиент указал в своей строке подключения SQL Server. Это общее имя обычно является полное доменное имя [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] узла. Чтобы использовать тот же сертификат для нескольких серверов, можно использовать подстановочный знак в общее имя (например, `"*.contoso.com"` вместо `"node1.contoso.com"`).   
2. CSR отправляется сертификата в центр сертификации (ЦС) для подписи. ЦС должен быть доверенным все клиентские компьютеры, которые подключаются к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. ЦС вернет подписанный сертификат администратору базы данных.   
3. Базы данных администратор настраивает [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для использования закрытого ключа и подписанного сертификата для TLS-подключения.   
4. Укажите клиентов `"Encrypt=True"` и `"TrustServerCertificate=False"` в строке соединения. (Имена определенных параметров может отличаться в зависимости от используемого драйвера). Клиенты теперь попытка шифрования соединения с SQL Server и проверьте действительность сертификата SQL Server для предотвращения атак в середине.  
 
## <a name="configuring-tls-on-linux"></a>Настройка TLS в Linux  

Используйте `mssql-conf` Настройка TLS для экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] под управлением Linux. Поддерживаются следующие параметры:  

|Параметр |Description |
|--- |--- |
|`network.forceencryption` |Если значение равно 1, затем [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] заставляет все соединения, должны быть зашифрованы. По умолчанию этого параметра равно 0. |  
|`network.tlscert` |Абсолютный путь к сертификату файла, который [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использует для TLS. Пример: `/etc/ssl/certs/mssql.pem` файл сертификата должен быть доступен для учетной записи mssql. Корпорация Майкрософт рекомендует ограничения доступа к файлу с помощью `chown mssql:mssql <file>; chmod 400 <file>`. |  
|`network.tlskey` |Абсолютный путь к закрытому ключу файла, который [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использует для TLS. Пример: `/etc/ssl/private/mssql.key` файл сертификата должен быть доступен для учетной записи mssql. Корпорация Майкрософт рекомендует ограничения доступа к файлу с помощью `chown mssql:mssql <file>; chmod 400 <file>`. | 
|`network.tlsprotocols` |Список разделенных запятыми из какой TLS протоколы допускаемым сервером SQL Server. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]всегда пытается согласовать надежный протокол разрешенных. Если клиент не поддерживает любой допустимый протокол [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] отклоняет попытки подключения.  Для обеспечения совместимости по умолчанию (1.2, 1.1, 1.0) разрешены все поддерживаемые протоколы.  Если клиенты поддерживает TLS 1.2, корпорация Майкрософт рекомендует, позволяя только TLS 1.2. |  
|`network.tlsciphers` |Указывает, какие шифры допускаемых [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для TLS. Эта строка должен быть отформатирован в [OpenSSL в формате списка шифра](https://www.openssl.org/docs/man1.0.2/apps/ciphers.html). Как правило нет необходимости менять этот параметр. <br /> По умолчанию допускаются следующие шифров: <br /> `ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA` |   
| | |
 
## <a name="example"></a>Пример 
В этом примере используется самозаверяющий сертификат. В обычных рабочих сценариев сертификат будет подписан центром сертификации, которому доверяют все клиенты.  
 
### <a name="step-1-generate-private-key-and-certificate"></a>Шаг 1: Создание закрытый ключ и сертификат 
Откройте команду на компьютере Linux терминалов где [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] запущена. Выполните следующие команды:  

- Создайте самозаверяющий сертификат. Убедитесь, что / CN соответствующее полного доменного имени узла SQL Server. При необходимости может использовать подстановочные знаки, например `'/CN=*.contoso.com'`.    
   ```  
   openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
   ```  

- Ограничение доступа к`mssql`  
   ```  
   sudo chown mssql:mssql mssql.pem mssql.key 
   sudo chmod 600 mssql.pem mssql.key 
   ```  
 
- Переместить системные каталоги SSL (необязательно)  
   ```  
   sudo mv mssql.pem /etc/ssl/certs/ 
   sudo mv mssql.key /etc/ssl/private/ 
   ```  
 
### <a name="step-2-configure--includessnoversionincludesssnoversion-mdmd"></a>Шаг 2: Настройка[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
Используйте `mssql-conf` Настройка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для использования сертификата и ключа для TLS. Для повышения безопасности можно также назначить TLS 1.2 единственный разрешенный протокол и принудительно все клиенты на использование зашифрованных соединений.  

```  
sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssql.pem 
sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssql.key 
sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
sudo /opt/mssql/bin/mssql-conf set network.forceencryption 1 
```
 
### <a name="step-3-restart-includessnoversionincludesssnoversion-mdmd"></a>Шаг 3: перезапуск[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 
[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]необходимо перезапустить эти изменения вступили в силу.  
`sudo systemctl restart mssql-server`  
 
### <a name="step-4-copy-self-signed-certificate-to-client-machines"></a>Шаг 4: Копирование самозаверяющего сертификата на клиентских компьютерах 
Так как в этом примере используется самозаверяющий сертификат [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] узел, сертификат (не закрытый ключ), которые необходимо скопировать и установить в качестве доверенного корневого сертификата на всех клиентских компьютерах, которые подключаются к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Если сертификат подписан центром сертификации, которому уже доверяют все клиенты, этот шаг необязателен. 
 
### <a name="step-5-connect-from-clients-using-tls"></a>Шаг 5: Подключения клиентов с использованием TLS 
Подключиться к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] из клиента с включенным шифрованием и `TrustServerCertificate` значение `False` в строке подключения. Вот несколько примеров того, как эти параметры задаются с помощью различных средств и драйверов. 

sqlcmd  
`sqlcmd -N -C -S mssql.contoso.com -U sa -P '<YourPassword>'`  

[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)]   
  ![Диалоговое окно соединения SSMS](media/sql-server-linux-encrypted-connections/ssms-encrypt-connection.png "диалогового окна соединения в среде SSMS")  
  
ADO.NET  
`"Encrypt=true; TrustServerCertificate=true;"`  

интерфейс ODBC   
`"Encrypt=yes; TrustServerCertificate=no;"`  

JDBC  
`"encrypt=true; trustServerCertificate=false;" `

 
## <a name="common-connection-errors"></a>Распространенные ошибки подключения  

|Сообщение об ошибке |Fix |
|--- |--- |
|Цепочка сертификатов был выдан центром сертификации, не является доверенным.  |Эта ошибка возникает, когда клиенты не смогут проверить подпись сертификата, предоставляемого SQL Server во время подтверждения TLS. Убедитесь, что клиент доверяет либо [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] сертификата непосредственно или ЦС, который подписал сертификат сервера SQL. |
|Неверное имя целевого субъекта.  |Убедитесь, что соответствие поля Общее имя сертификата SQL Server имя сервера, указанное в строке подключения клиента. |  
|существующее соединение было принудительно завершено удаленным узлом. |Эта ошибка может возникать, когда клиент не поддерживает версию протокола TLS, необходимые для SQL Server. Например если [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] настроен на требуется TLS 1.2, убедитесь, что ваши клиенты также поддерживают протокол TLS 1.2. |
| | |   


