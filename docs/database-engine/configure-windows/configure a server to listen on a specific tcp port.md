---
title: "Настройка сервера для прослушивания указанного TCP-порта (диспетчер конфигурации SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "фиксированный порт"
  - "статические порты"
  - "порты [SQL Server], назначение номеров"
  - "назначение номеров портов"
  - "динамические порты [SQL Server]"
  - "TCP/IP [SQL Server], номера портов"
ms.assetid: 2276a5ed-ae3f-4855-96d8-f5bf01890640
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Настройка сервера для прослушивания указанного TCP-порта (диспетчер конфигурации SQL Server)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В этом разделе описано, как настроить экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] для прослушивания определенного фиксированного порта с помощью диспетчера конфигурации SQL Server. Если прослушивание включено, то экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] по умолчанию прослушивает TCP-порт 1433. Именованные экземпляры [!INCLUDE[ssDE](../../includes/ssde-md.md)] и [!INCLUDE[ssEW](../../includes/ssew-md.md)] настроены для использования [динамических портов](https://msdn.microsoft.com/library/dd981060). Это означает, что при запуске службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для них выбирается свободный порт. При соединении с именованным экземпляром через брандмауэр необходимо настроить компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] на прослушивание определенного порта. Это позволит открыть в брандмауэре необходимый порт.  
  
 Дополнительные сведения о настройках брандмауэра Windows по умолчанию и описание портов TCP, влияющих на компонент Database Engine, службы Analysis Services, службы Reporting Services и службы Integration Services, см. в разделе [Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
> [!TIP]  
>  При выборе номера порта руководствуйтесь приведенным по адресу [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers) списком номеров портов, которые назначаются конкретным приложениям. Выберите незанятый номер порта. Дополнительные сведения см. в разделе [Предусмотренный по умолчанию динамический диапазон портов для TCP/IP, который изменился в Windows Vista и Windows Server 2008](http://support.microsoft.com/kb/929851).  
  
> [!WARNING]  
>  Компонент Database Engine начнет прослушивание нового порта после перезапуска. Однако служба браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отслеживает реестр и возвращает новый номер порта, как только будет изменена конфигурация, даже если компонент Database Engine его не использует. Перезапустите компонент Database Engine, чтобы обеспечить согласованность и избежать ошибок соединения.  
  
 **В этом разделе**  
  
-   **Настройка сервера для прослушивания определенного TCP-порта с помощью:**  
  
     [Диспетчер конфигурации SQL Server](#SSMSProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### Назначение ядру СУБД SQL Server порта TCP/IP  
  
1.  В области консоли диспетчера конфигурации SQL Server разверните узел **Сетевая конфигурация SQL Server**, **Протоколы для \<имя экземпляра>\>**, а затем дважды щелкните **TCP/IP**.  
  
    > [!NOTE]  
    >  Если возникают проблемы при открытии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, см. статью [Диспетчер конфигурации SQL Server](../../relational-databases/sql-server-configuration-manager.md).  
  
2.  В диалоговом окне **Свойства TCP/IP** на вкладке **IP-адреса** появится несколько IP-адресов в формате **IP1**, **IP2** до **IPAll**. Одним из приведенных IP-адресов является адрес адаптера заглушки 127.0.0.1. Для каждого IP-адреса на компьютере появляются дополнительные IP-адреса. (Возможно, вы увидите IP-адреса как версии 4, так и версии 6.) Чтобы определить настраиваемый IP-адрес, щелкните правой кнопкой мыши каждый адрес и выберите пункт **Свойства**.  
  
3.  Если в диалоговом окне **Динамические порты TCP** содержится значение **0**, означающее прослушивание компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] динамических портов, удалите его.  
  
     ![TCP_ports](../../database-engine/configure-windows/media/tcp-ports.png "TCP_ports")  
  
4.  В области окна **Свойства***IP* **n** в поле **Порт TCP** введите номер порта, который необходимо прослушивать по данному IP-адресу и нажмите кнопку **ОК**.  
  
5.  В области консоли выберите **Службы SQL Server**.  
  
6.  В области сведений щелкните правой кнопкой мыши **SQL Server (**\<имя экземпляра>\>**)**, а затем нажмите кнопку **Перезагрузка**, чтобы остановить и перезагрузить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 После настройки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на прослушивание определенного порта установить соединение с ним с помощью клиентского приложения можно тремя способами:  
  
-   Запустите службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на сервере для подключения к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] по имени.  
  
-   Создайте псевдоним на клиенте, указав номер порта.  
  
-   Настройте клиент на использование пользовательской строки подключения.  
  
## См. также:  
 [Создание или удаление псевдонима сервера для использования клиентом (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/create or delete a server alias for use by a client.md)   
 [Служба браузера SQL Server](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  