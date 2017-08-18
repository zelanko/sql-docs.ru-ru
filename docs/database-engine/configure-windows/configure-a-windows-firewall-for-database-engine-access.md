---
title: "Настройка брандмауэра Windows для доступа к компоненту Database Engine | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connections [SQL Server], firewall systems
- firewall systems, [Database Engine]
- security [SQL Server], firewalls
ms.assetid: 0093b43c-c6b5-4574-9b30-3a0e91e1a1f9
caps.latest.revision: 57
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 7d79f9d00344dceb2559d66f7f6f4450597c79f7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="configure-a-windows-firewall-for-database-engine-access"></a>Настройка брандмауэра Windows для доступа к компоненту Database Engine

 > Материалы по предыдущим версиям SQL Server см. в разделе [Настройка брандмауэра Windows для доступа к компоненту Database Engine](https://msdn.microsoft.com/en-US/library/ms175043(SQL.120).aspx).


  В данном разделе описывается, как настроить брандмауэр Windows для доступа к компоненту Database Engine в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью диспетчера конфигурации SQL Server. Системы брандмауэров предотвращают несанкционированный доступ к ресурсам компьютера. Чтобы обращаться к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] через брандмауэр, необходимо разрешить такой доступ в настройках брандмауэра на компьютере с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Дополнительные сведения о настройках брандмауэра Windows по умолчанию и описание портов TCP, влияющих на компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)], службы Analysis Services, службы Reporting Services и службы Integration Services, см. в разделе [Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md). Существует множество систем брандмауэров. За сведениями о конкретном брандмауэре следует обратиться к документации по этому брандмауэру.  
  
 Основные шаги для разрешения доступа.  
  
1.  Настройка компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] для использования конкретного порта TCP/IP. Экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] по умолчанию использует порт 1433. Порт можно изменить. Порт, используемый компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] , указывается в журнале ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Экземпляры [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], [!INCLUDE[ssEW](../../includes/ssew-md.md)] и именованные экземпляры компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] используют динамические порты. Сведения по настройке этих экземпляров для использования конкретного порта см. в разделе [Настройка сервера для прослушивания указанного TCP-порта (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md).  
  
2.  Настройка брандмауэра, чтобы разрешить доступ к порту для авторизованных пользователей или компьютеров.  
  
> [!NOTE]  
>  Служба браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет пользователям подключаться к экземплярам компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , которые не прослушивают порт 1433, не зная номера порта. Для использования браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо открыть UDP-порт 1434. Чтобы поддерживать наиболее безопасную среду, остановите службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и настройте клиенты для подключения с помощью номера порта.  
  
> [!NOTE]  
>  По умолчанию в [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows включен брандмауэр Windows, который закрывает порт 1433, чтобы защитить экземпляр по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютера от входящих соединений из Интернета. Соединения с экземпляром по умолчанию по протоколу TCP/IP невозможны, пока порт 1433 не будет открыт. Основные шаги настройки брандмауэра Windows приведены в следующих процедурах. Дополнительные сведения см. в документации по Windows.  
  
 Как вариант, вместо настройки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на прослушивание определенного порта и открытия порта можно включить исполняемый объект [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (Sqlservr.exe) в список исключений заблокированных программ. Используйте этот метод, чтобы продолжить использовать динамические порты. Таким методом можно получить доступ только к одному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Безопасность](#Security)  
  
-   **Настройка брандмауэра Windows для доступа к компоненту Database Engine с помощью:**  
  
     [Диспетчер конфигурации SQL Server](#SSMSProcedure)  
  
## <a name="before-you-begin"></a>Перед началом  
  
###  <a name="Security"></a> Безопасность  
 Открытие портов на брандмауэре может привести к незащищенности сервера от вредоносных атак. Перед открытием портов убедитесь в том, что знаете принципы работы брандмауэров. Дополнительные сведения см. в разделе [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md).  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
 Относится к Windows Vista, Windows 7 и Windows Server 2008  
  
 В следующих процедурах выполняется настройка брандмауэра Windows с помощью оснастки «Брандмауэр Windows в режиме повышенной безопасности» консоли управления (MMC). В оснастке «Брандмауэр Windows в режиме повышенной безопасности» выполняется настройка только текущего профиля. Дополнительные сведения о брандмауэре Windows в режиме повышенной безопасности см. в разделе [Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
#### <a name="to-open-a-port-in-the-windows-firewall-for-tcp-access"></a>Открытие порта в брандмауэре Windows для доступа TCP  
  
1.  В меню **Пуск** выберите команду **Выполнить**, введите **WF.msc**и нажмите кнопку **ОК**.  
  
2.  На левой панели **Брандмауэр Windows в режиме повышенной безопасности**щелкните правой кнопкой мыши раздел **Правила для входящих подключений**и выберите на панели действий пункт **Создать правило** .  
  
3.  В диалоговом окне **Тип правила** выберите **Порт**и нажмите кнопку **Далее**.  
  
4.  В диалоговом окне **Протокол и порты** выберите протокол **TCP**. Выберите пункт **Определенные локальные порты**и введите номер порта для экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], например **1433** для экземпляра по умолчанию. Нажмите кнопку **Далее**.  
  
5.  В диалоговом окне **Действие** выберите **Разрешить соединение**и нажмите кнопку **Далее**.  
  
6.  В диалоговом окне **Профиль** выберите профили, описывающие среду соединения компьютеров, который нужно подключить к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)], и нажмите кнопку **Далее**.  
  
7.  В диалоговом окне **Имя** введите имя и описание для этого правила, а затем нажмите кнопку **Готово**.  
  
#### <a name="to-open-access-to-sql-server-when-using-dynamic-ports"></a>Открытие доступа к SQL Server при использовании динамических портов  
  
1.  В меню **Пуск** выберите команду **Выполнить**, введите **WF.msc**и нажмите кнопку **ОК**.  
  
2.  На левой панели **Брандмауэр Windows в режиме повышенной безопасности**щелкните правой кнопкой мыши раздел **Правила для входящих подключений**и выберите на панели действий пункт **Создать правило** .  
  
3.  В диалоговом окне **Тип правила** выберите **Программа**и нажмите кнопку **Далее**.  
  
4.  В диалоговом окне **Программа** выберите пункт **Путь программы**. Нажмите кнопку **Обзор**, найдите и выберите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , к которому необходим доступ через брандмауэр, а затем нажмите кнопку **Открыть**. По умолчанию исполняемым файлом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является **C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe**. Нажмите кнопку **Далее**.  
  
5.  В диалоговом окне **Действие** выберите **Разрешить соединение**и нажмите кнопку **Далее**.  
  
6.  В диалоговом окне **Профиль** выберите профили, описывающие среду соединения компьютеров, который нужно подключить к компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)], и нажмите кнопку **Далее**.  
  
7.  В диалоговом окне **Имя** введите имя и описание для этого правила, а затем нажмите кнопку **Готово**.  
  
## <a name="see-also"></a>См. также:  
 [Практическое руководство. Настройка параметров брандмауэра для базы данных SQL с помощью портала Azure](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)  
  
  
