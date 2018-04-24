---
title: Настройка компонента Database Engine на прослушивание нескольких портов TCP | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: configure-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ports [SQL Server], multiple
- TDS
- listen on multiple ports
- endpoints [SQL Server], TDS
- adding ports
- tabular data stream
- multiple ports
ms.assetid: 8e955033-06ef-403f-b813-3d8241b62f1f
caps.latest.revision: 26
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7181881b40e7a06d8f8ef11ec7670eeec961e4b7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="configure-the-database-engine-to-listen-on-multiple-tcp-ports"></a>Настройка компонента Database Engine на прослушивание нескольких портов TCP
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этой теме описан процесс настройки компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] для прослушивания нескольких портов на [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью диспетчера конфигурации SQL Server. При включении TCP/IP для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] будет прослушивать входящие соединения в точке соединения по IP-адресу и номеру порта TCP. В результате выполнения следующих процедур будет создана конечная точка потока табличных данных (TDS), чтобы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мог прослушивать соединения на дополнительном порту TCP.  
  
 Ниже перечислены возможные причины создания второй конечной точки TDS.  
  
-   Усиление безопасности путем настройки брандмауэра для предоставления доступа к конечной точке по умолчанию только локальным клиентским компьютерам в определенной подсети. Обеспечьте доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из Интернета для команды поддержки путем создания новой конечной точки, которую брандмауэр делает видимой из Интернета, и предоставьте права на соединение с этой конечной точкой только команде поддержки сервера.  
  
-   Установка соответствия соединений определенным процессорам при использовании технологии доступа к неоднородной памяти (NUMA).  
  
 Настройка конечной точки TDS включает в себя следующие шаги, которые могут быть выполнены в любом порядке.  
  
-   Создайте конечную точку TDS для порта TCP и восстановите доступ к конечной точке по умолчанию, если необходимо.  
  
-   Предоставьте необходимым участникам на уровне сервера доступ к конечной точке.  
  
-   Укажите номер порта TCP для выбранного IP-адреса.  
  
 Дополнительные сведения о настройках брандмауэра Windows по умолчанию и описание портов TCP, влияющих на компонент Database Engine, службы Analysis Services, службы Reporting Services и службы Integration Services, см. в разделе [Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-create-a-tds-endpoint"></a>Создание конечной точки TDS  
  
-   Выполните следующую инструкцию, чтобы создать конечную точку с именем **CustomConnection** для порта 1500 на всех доступных адресах TCP сервера.  
  
    ```  
    USE master;  
    GO  
    CREATE ENDPOINT [CustomConnection]  
    STATE = STARTED  
    AS TCP  
       (LISTENER_PORT = 1500, LISTENER_IP =ALL)  
    FOR TSQL() ;  
    GO  
    ```  
  
 При создании новой конечной точки [!INCLUDE[tsql](../../includes/tsql-md.md)] разрешения на соединение с конечной точкой потока табличных данных по умолчанию для группы **public** отменяются. Если группе **public** требуется доступ к конечной точке по умолчанию, то ей необходимо предоставить это разрешение, выполнив инструкцию `GRANT CONNECT ON ENDPOINT::[TSQL Default TCP] to [public];` .  
  
#### <a name="to-grant-access-to-the-endpoint"></a>Предоставление доступа к конечной точке  
  
-   Выполните следующую инструкцию, чтобы предоставить группе SQLSupport домена corp доступ к конечной точке **CustomConnection** .  
  
    ```  
    GRANT CONNECT ON ENDPOINT::[CustomConnection] to [corp\SQLSupport] ;  
    GO  
    ```  
  
#### <a name="to-configure-the-sql-server-database-engine-to-listen-on-an-additional-tcp-port"></a>Настройка компонента SQL Server Database Engine на прослушивание дополнительного порта TCP  
  
1.  В диспетчере конфигурации SQL Server разверните узел **Сетевая конфигурация SQL Server** и щелкните элемент **Протоколы для***<имя_экземпляра>*.  
  
2.  Разверните узел **Протоколы для***<имя_экземпляра>* и щелкните **TCP/IP**.  
  
3.  В правой панели щелкните правой кнопкой мыши отключенный IP-адрес, который необходимо включить, и выберите **Включить**.  
  
4.  Щелкните правой кнопкой мыши **IPAll**и выберите пункт **Свойства**.  
  
5.  В поле **TCP-порт** введите номера портов, которые должны прослушиваться компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] , разделяя их запятыми. В нашем примере: если прослушивается порт по умолчанию 1433, введите **,1500** , чтобы поле содержало строку **1433,1500**, и нажмите кнопку **OK**.  
  
    > [!NOTE]  
    >  Если порт включается не для всех IP-адресов, настройте дополнительный порт в окне свойств только для необходимого адреса. Затем на панели консоли щелкните правой кнопкой мыши **TCP/IP**, выберите пункт **Свойства**и в поле **Прослушивать все** выберите **Нет**.  
  
6.  На левой панели щелкните **Службы SQL Server**.  
  
7.  На правой панели щелкните правой кнопкой мыши **SQL Server***<имя_экземпляра>* и выберите **Перезагрузка**.  
  
     После перезагрузки компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] журнал ошибок будет содержать список портов, прослушиваемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
#### <a name="to-connect-to-the-new-endpoint"></a>Подключение к новой конечной точке  
  
-   Выполните следующую инструкцию, чтобы подключиться к конечной точке **CustomConnection** экземпляра SQL Server по умолчанию на сервере с именем ACCT, используя доверительное соединение, предполагая, что пользователь является членом группы [corp\SQLSupport].  
  
    ```  
    sqlcmd -SACCT,1500  
    ```  
  
## <a name="see-also"></a>См. также:  
 [CREATE ENDPOINT (Transact-SQL)](../../t-sql/statements/create-endpoint-transact-sql.md)   
 [DROP ENDPOINT (Transact-SQL)](../../t-sql/statements/drop-endpoint-transact-sql.md)   
 [GRANT, предоставление разрешений конечной точке (Transact-SQL)](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md)   
 [Сопоставление портов TCP/IP с узлами NUMA (SQL Server)](../../database-engine/configure-windows/map-tcp-ip-ports-to-numa-nodes-sql-server.md)  
  
  
