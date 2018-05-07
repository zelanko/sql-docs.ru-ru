---
title: Подключение к базе данных Azure SQL | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 49645b1f-39b1-4757-bda1-c51ebc375c34
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 183cd9c749cac8b1af3d97a9830d4d4288fd464f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-to-an-azure-sql-database"></a>Подключение к базе данных SQL Azure
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В этом разделе обсуждаются проблемы при использовании [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] для подключения к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]. Дополнительные сведения о подключении к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], см.:  
  
-   [SQL Azure Database](http://go.microsoft.com/fwlink/?LinkID=202490)  
  
-   [Как: подключение к SQL Azure с помощью JDBC](http://msdn.microsoft.com/library/gg715284.aspx)  
  
-   [Использование SQL Azure в Java](http://msdn.microsoft.com/library/windowsazure/hh749029(VS.103).aspx)

-   [Соединение с использованием проверки подлинности Azure Active Directory](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md)  
  
## <a name="details"></a>Сведения  
 При подключении к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], необходимо подключиться к базе данных master для вызова **SQLServerDatabaseMetaData.getCatalogs**.  
 [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] не поддерживает возврат всего набора каталогов из пользовательской базы данных. **SQLServerDatabaseMetaData.getCatalogs** использует для получения каталогов представление sys.databases. См. обсуждение разрешений в [sys.databases (база данных SQL Azure)](http://go.microsoft.com/fwlink/?LinkId=217396) для понимания **SQLServerDatabaseMetaData.getCatalogs** поведение на [!INCLUDE[ssAzure](../../includes/ssazure_md.md)].  
  
 Прерванные соединения  
 При подключении к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], неактивных соединений могут быть разорваны сетевым компонентом (например, брандмауэром) после периода отсутствия активности. В данном контексте существует два типа бездействующих соединений.  
  
-   Бездействующие на уровне TCP, которые сбрасываются многими сетевыми устройствами.  
  
-   Бездействующие на уровне шлюза SQL Azure, где TCP **keepalive** вероятно (что делает соединение небездействующим TCP), но не выполняющие активных запросов в течение 30 минут. В этом случае шлюз определит, что соединение TDS бездействует в течение 30 минут, и прервет его.  
  
 Чтобы избежать разрыва связи простаивающих соединений сетевыми компонентами, необходимо задать следующие параметры в реестре операционной системе, в которой загружается драйвер (или их аналоги для операционных систем, отличных от Windows):  
  
|Параметр реестра|Рекомендуемое значение|  
|----------------------|-----------------------|  
|HKEY_LOCAL_MACHINE \ системы \ CurrentControlSet \ служб \ Tcpip \ параметры \ KeepAliveTime|30 000|  
|HKEY_LOCAL_MACHINE \ системы \ CurrentControlSet \ служб \ Tcpip \ параметры \ KeepAliveInterval|1000|  
|HKEY_LOCAL_MACHINE \ системы \ CurrentControlSet \ служб \ Tcpip \ параметры \ TcpMaxDataRetransmissions|10|  
  
 После этого необходимо перезагрузить компьютер, чтобы новые параметры вступили в силу.  
  
 Чтобы эта операция выполнялась при запуске Windows Azure, создайте выполняемую при запуске задачу, которая будет добавлять значения в реестр.  Например, в файл определения службы добавьте следующую задачу, выполняемую при запуске.  
  
```  
<Startup>  
    <Task commandLine="AddKeepAlive.cmd" executionContext="elevated" taskType="simple">  
    </Task>  
</Startup>  
```  
  
 Затем добавьте файл AddKeepAlive.cmd в проект. Выберите для параметра "Копировать в выходной каталог" значение "Всегда копировать". Ниже приведен образец файла AddKeepAlive.cmd.  
  
```  
if exist keepalive.txt goto done  
time /t > keepalive.txt  
REM Workaround for JDBC keep alive on SQL Azure  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v KeepAliveTime /t REG_DWORD /d 30000 >> keepalive.txt  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v KeepAliveInterval /t REG_DWORD /d 1000 >> keepalive.txt  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v TcpMaxDataRetransmissions /t REG_DWORD /d 10 >> keepalive.txt  
shutdown /r /t 1  
:done  
```  
  
 Добавление имени сервера к идентификатору пользователя UserId в строке подключения  
 До версии 4.0 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], при подключении к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], требовалось Добавление имени сервера к параметру UserId в строке подключения. Например, user@servername. Начиная с версии 4.0 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], нет необходимости для добавления @servername к параметру UserId в строке подключения.  
  
 Для использования шифрования необходимо задать hostNameInCertificate  
 При подключении к [!INCLUDE[ssAzure](../../includes/ssazure_md.md)], следует указать **hostNameInCertificate** при указании **шифрования = true**. (Если имя сервера в строке подключения указано *shortName*. *имя_домена*, задайте **hostNameInCertificate** свойства \*. *имя_домена*.)  
  
 Например:  
  
```  
jdbc:sqlserver://abcd.int.mscds.com;databaseName= myDatabase;user=myName;password=myPassword;encrypt=true;hostNameInCertificate= *.int.mscds.com;  
```  
  
## <a name="see-also"></a>См. также  
 [Соединение с SQL Server с помощью драйвера JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
