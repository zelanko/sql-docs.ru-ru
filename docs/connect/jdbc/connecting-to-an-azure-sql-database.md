---
title: Подключение к базе данных Azure SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 49645b1f-39b1-4757-bda1-c51ebc375c34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e120762a84929ed58d163efb26faa6f28eb50dc3
ms.sourcegitcommit: 7d4a3fc0f2622cbc6930d792be4a9b3fcac4c4b6
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2019
ms.locfileid: "58306132"
---
# <a name="connecting-to-an-azure-sql-database"></a>Подключение к базе данных SQL Azure

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В этой статье обсуждаются проблемы, которые могут возникнуть при использовании [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] для соединения с [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]. Дополнительные сведения о соединении с [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] см. в разделах:  
  
- [База данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)  
  
- [Как подключиться к SQL Azure с помощью JDBC](https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-java)  

- [Соединение с использованием проверки подлинности Azure Active Directory](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md)  
  
## <a name="details"></a>Сведения

При подключении к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], следует подключиться к базе данных master для вызова **SQLServerDatabaseMetaData.getCatalogs**.  
[!INCLUDE[ssAzure](../../includes/ssazure_md.md)] не поддерживает возврат всего набора каталогов из пользовательских баз данных. **SQLServerDatabaseMetaData.getCatalogs** использовать для получения каталогов представление sys.databases. См. обсуждение разрешений в [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) для понимания **SQLServerDatabaseMetaData.getCatalogs** поведение на [!INCLUDE[ssAzure](../../includes/ssazure_md.md)].  
  
## <a name="connections-dropped"></a>Прерванные соединения

При установлении соединения с [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] простаивающие соединения по истечении определенного времени бездействия могут быть разорваны сетевым компонентом (например, брандмауэром). В данном контексте существует два типа бездействующих соединений.  

- Бездействующие на уровне TCP, которые сбрасываются многими сетевыми устройствами.  

- Бездействующие на уровне шлюза SQL Azure, где, вероятно, отправляются TCP-сообщения **keepalive** (что делает соединение небездействующим на уровне TCP), не выполняющие активных запросов в течение 30 минут. В этом случае шлюз определит, что соединение TDS бездействует в течение 30 минут, и прервет его.  
  
Чтобы избежать разрыва связи простаивающих соединений сетевыми компонентами, необходимо задать следующие параметры в реестре операционной системе, в которой загружается драйвер (или их аналоги для операционных систем, отличных от Windows):  
  
|Параметр реестра|Рекомендуемое значение|  
|----------------------|-----------------------|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ служб \ Tcpip \ параметры \ KeepAliveTime|30 000|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ служб \ Tcpip \ параметры \ KeepAliveInterval|1000|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ служб \ Tcpip \ параметры \ TcpMaxDataRetransmissions|10|  
  
Перезагрузите компьютер, чтобы новые параметры вступили в силу.  

Чтобы эта операция выполнялась при запуске Windows Azure, создайте выполняемую при запуске задачу, которая будет добавлять значения в реестр.  Например, в файл определения службы добавьте следующую задачу, выполняемую при запуске.  

```xml
<Startup>  
    <Task commandLine="AddKeepAlive.cmd" executionContext="elevated" taskType="simple">  
    </Task>  
</Startup>  
```

Затем добавьте файл AddKeepAlive.cmd в проект. Выберите для параметра "Копировать в выходной каталог" значение "Всегда копировать". Ниже приведен образец файла AddKeepAlive.cmd.  

```bat
if exist keepalive.txt goto done  
time /t > keepalive.txt  
REM Workaround for JDBC keep alive on SQL Azure  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v KeepAliveTime /t REG_DWORD /d 30000 >> keepalive.txt  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v KeepAliveInterval /t REG_DWORD /d 1000 >> keepalive.txt  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v TcpMaxDataRetransmissions /t REG_DWORD /d 10 >> keepalive.txt  
shutdown /r /t 1  
:done  
```

## <a name="appending-the-server-name-to-the-userid-in-the-connection-string"></a>Добавление имени сервера к идентификатору пользователя UserId в строке подключения  

До [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] версии 4.0 при установлении соединения с базой данных [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] требовалось добавление имени сервера к параметру UserId в строке подключения. Например, user@servername. Начиная с версии 4.0 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] добавление компонента @servername к параметру UserId в строке подключения не требуется.  

## <a name="using-encryption-requires-setting-hostnameincertificate"></a>Для использования шифрования необходимо задать hostNameInCertificate

До версии 7.2 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], при подключении к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], следует указать **hostNameInCertificate** при указании **шифрования = true** (если имя сервера в соединении Строка является *shortName*. *domainName*, задайте **hostNameInCertificate** свойства \*. *domainName*.). Это свойство является необязательным, начиная с версии 7.2 драйвера.

Пример:

```java
jdbc:sqlserver://abcd.int.mscds.com;databaseName=myDatabase;user=myName;password=myPassword;encrypt=true;hostNameInCertificate=*.int.mscds.com;
```

## <a name="see-also"></a>См. также:

[Соединение с SQL Server с помощью драйвера JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
