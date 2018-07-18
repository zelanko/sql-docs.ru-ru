---
title: Настройка брандмауэра Windows для доступа к службам SSIS | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- security [Integration Services], firewalls
- Windows Firewall [Integration Services]
- unauthorized access [Integration Services]
- Integration Services service, firewalls
- firewall systems [Integration Services]
- SQL Server Integration Services, firewalls
- SSIS, firewalls
ms.assetid: 39975cf2-c351-4205-8c39-27a0fadfb010
caps.latest.revision: 42
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 67a1206afe217ce2f0e358c56ee4df2b16691b8c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163005"
---
# <a name="configure-a-windows-firewall-for-access-to-the-ssis-service"></a>Настройка параметров брандмауэра Windows для доступа к службам SSIS
    
> [!IMPORTANT]  
>  В данном разделе описывается компонент [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] — служба Windows для управления пакетами служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] поддерживает эту службу для обеспечения обратной совместимости с более ранними версиями служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Начиная с [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], на сервере служб Integration Services можно управлять пакетами.  
  
 Система брандмауэров Windows предотвращает несанкционированный доступ к ресурсам компьютера через сетевое подключение. Чтобы получить доступ к службам [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] через этот брандмауэр, необходимо настроить брандмауэр для разрешения доступа.  
  
> [!IMPORTANT]  
>  Чтобы управлять пакетами, которые хранятся на удаленном сервере, не нужно соединятся с экземпляром службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на этом удаленном сервере. Вместо этого измените файл конфигурации для службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] таким образом, чтобы среда [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] отображала пакеты, хранимые на удаленном сервере. Дополнительные сведения см. в разделе [Configuring the Integration Services Service &#40;SSIS Service&#41;](configuring-the-integration-services-service-ssis-service.md).  
  
 Служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] использует протокол DCOM. Дополнительные сведения о работе протокола DCOM с брандмауэром см. в статье[Использование протокола DСОМ с брандмауэрами](http://go.microsoft.com/fwlink/?LinkId=12490)библиотеки MSDN.  
  
 Существует множество систем брандмауэров. При запуске другого брандмауэра обратитесь к конкретной документации используемого брандмауэра.  
  
 Если брандмауэр поддерживает фильтрацию на уровне приложения, то можно использовать пользовательский интерфейс, предоставляемый Windows для указания исключений, которым разрешается доступ через брандмауэр, например программам и службам. Иначе необходимо установить настройки DCOM, ограничивающие количество портов TCP. Ссылка на веб-сайт Майкрософт в прошлом включала сведения о том, как указать TCP-порты для использования.  
  
 Служба Integration Services использует порт 135, который не может быть изменен. Для доступа к диспетчеру управления службами (SCM) необходимо открыть TCP-порт 135. SCM выполняет такие задачи, как запуск и остановка служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , а также передачу управляющих запросов выполняемой службе.  
  
 Сведения в следующем разделе относятся к брандмауэру Windows. Можно настроить систему брандмауэра Windows, введя команду в командной строке или установив свойства в диалоговом окне брандмауэра Windows.  
  
 Дополнительные сведения о настройках брандмауэра Windows по умолчанию и описание портов TCP, влияющих на ядро СУБД, службы Analysis Services, службы Reporting Services и службы Integration Services, см. в разделе [Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
## <a name="configuring-a-windowsfirewall"></a>Настройка брандмауэра Windows  
 Можно использовать следующие команды для открытия TCP-порта 135, добавления в список исключения MsDtsSrvr.exe и указания области доступа, предоставляемого брандмауэром.  
  
#### <a name="to-configure-a-windowsfirewall-using-the-command-prompt-window"></a>Настройка брандмауэра Windows с помощью окна командной строки  
  
1.  Выполните команду: `netsh firewall add portopening protocol=TCP port=135 name="RPC (TCP/135)" mode=ENABLE scope=SUBNET`  
  
2.  Выполните команду: `netsh firewall add allowedprogram program="%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn\MsDtsSrvr.exe" name="SSIS Service" scope=SUBNET`  
  
    > [!NOTE]  
    >  Чтобы включить брандмауэр для всех компьютеров, в том числе в сети Интернет, замените предложение «scope=SUBNET» на «scope=ALL».  
  
 Следующая процедура описывает, как использовать пользовательский интерфейс Windows для открытия TCP-порта 135, добавления в список исключения MsDtsSrvr.exe и указания области доступа, предоставляемой брандмауэром.  
  
#### <a name="to-configure-a-firewall-using-the-windowsfirewall-dialog-box"></a>Настройка брандмауэра Windows с помощью диалогового окна  
  
1.  На панели управления дважды щелкните элемент **Брандмауэр Windows**.  
  
2.  В диалоговом окне **Брандмауэр Windows** перейдите на вкладку **Исключения** , затем нажмите кнопку **Добавить программу**.  
  
3.  В диалоговом окне **Добавление программы** нажмите кнопку **Обзор**, найдите папку Program Files\Microsoft SQL Server\100\DTS\Binn, выберите файл MsDtsSrvr.exe и нажмите кнопку **Открыть**. Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **Добавить программу** .  
  
4.  На вкладке **Исключения** нажмите кнопку **Добавить порт**.  
  
5.  В диалоговом окне **Добавить порт** введите **RPC(TCP/135)** или другое описательное имя в поле **Имя**, введите **135** в поле **Номер порта** и выберите **TCP**.  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] всегда использует порт 135. Другой порт указать нельзя.  
  
6.  В диалоговом окне **Добавить порт** можно нажать кнопку **Изменить область** , чтобы изменить область по умолчанию.  
  
7.  В диалоговом окне **Изменить область** выберите **Только локальная сеть (подсеть)** или введите пользовательский список и нажмите кнопку **ОК**.  
  
8.  Чтобы закрыть диалоговое окно **Добавить порт** , нажмите кнопку **ОК**.  
  
9. Чтобы закрыть диалоговое окно **Брандмауэр Windows** , нажмите кнопку **ОК**.  
  
    > [!NOTE]  
    >  Для настройки брандмауэра Windows эта процедура использует элемент **Брандмауэр Windows** на панели управления. Элемент **Брандмауэр Windows** настраивает брандмауэр только для текущего сетевого профиля. Брандмауэр Windows также можно настроить с помощью программы командной строки **netsh** или оснастки консоли управления [!INCLUDE[msCoName](../includes/msconame-md.md)] (MMC) "Брандмауэр Windows в режиме повышенной безопасности". Дополнительные сведения об этих средствах см. в разделе [Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
## <a name="see-also"></a>См. также  
 [Настройка интеграции службы служб &#40;службы SSIS&#41;](service/integration-services-service-ssis-service.md)   
 [Службы Integration Services (службы SSIS)](service/integration-services-service-ssis-service.md)  
  
  
