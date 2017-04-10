---
title: "Настройка контактной зоны | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "сокращение уязвимой контактной зоны"
  - "обновление SQL Server, безопасность"
  - "настройка контактной зоны [SQL Server]"
  - "настройка контактной зоны [SQL Server], о контактной зоне"
  - "уязвимая контактная зона [SQL Server]"
  - "установка SQL Server, безопасность"
ms.assetid: f741169c-1453-4ad2-830b-bf2be27d712f
caps.latest.revision: 79
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 79
---
# Настройка контактной зоны
  В конфигурации по умолчанию для новых установок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]многие из функций отключены. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выборочно устанавливает и запускает только ключевые службы и функции, чтобы свести к минимуму количество функций, которые могут подвергнуться атаке злоумышленника. Системный администратор может изменить эти значения по умолчанию в ходе установки, а также включать или отключать функции работающего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]по своему выбору. Кроме того, при подключении с других компьютеров определенные компоненты могут быть недоступны до настройки протоколов.  
  
> [!NOTE]  
>  В отличие от новых установок, во время обновления существующие службы или функции не отключаются, но после его завершения могут быть применены дополнительные параметры конфигурации контактной зоны.  
  
## Протоколы, соединение и параметры запуска  
 С помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно запускать и останавливать службы, настраивать параметры запуска и включать протоколы и другие параметры соединения.  
  
#### Запуск диспетчера конфигурации SQL Server  
  
1.  В меню **Пуск** последовательно выберите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и щелкните **Диспетчер конфигурации SQL Server**.  
  
    -   Для запуска компонентов и настройки автоматического запуска используйте область **Службы SQL Server** диспетчера конфигурации.  
  
    -   Используйте область **Сетевая конфигурация SQL Server** для включения протоколов и параметров соединения, таких как фиксированные порты TCP/IP или принудительное шифрование.  
  
 Дополнительные сведения см. в разделе [SQL Server Configuration Manager](../../relational-databases/sql-server-configuration-manager.md). Возможность удаленного подключения также зависит от правильной настройки брандмауэра. Дополнительные сведения см. в статье [Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
## Включение и отключение функций  
 Включение и отключение функций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно настроить с помощью аспектов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### Настройка контактной зоны с помощью аспектов  
  
1.  В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] выполните соединение с компонентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Аспекты**.  
  
3.  В диалоговом окне **Просмотр аспектов** разверните список **Аспекты**, выберите соответствующий аспект **Настройка контактной зоны** (**Настройка контактной зоны**, **Настройка контактной зоны для служб Analysis Services** или **Настройка контактной зоны для служб Reporting Services**).  
  
4.  В области **Свойства аспектов** выберите необходимые значения для всех свойств.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 Для периодической проверки конфигурации аспекта используйте управление на основе политик. Дополнительные сведения об управлении на основе политик см. в статье [Администрирование серверов с помощью управления на основе политик](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md).  
  
 Также можно задать параметры компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] при помощи хранимой процедуры **sp_configure**. Дополнительные сведения см. в статье [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
 Чтобы изменить свойство **Включить встроенную безопасность** [!INCLUDE[ssRS](../../includes/ssrs-md.md)], используйте настройки свойств в службах [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Чтобы изменить свойство **Планирование событий и доставка отчетов** и свойство **Доступ к веб-службам и HTTP** , измените файл конфигурации **RSReportServer.config** .  
  
## Параметры командной строки  
 Используйте командлет PowerShell **Invoke-PolicyEvaluation**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для вызова политик конфигурации контактной зоны. Дополнительные сведения см. в разделе [Использование командлетов компонента Database Engine](../../relational-databases/scripting/use-the-database-engine-cmdlets.md).  
  
## Конечные точки SOAP и Service Broker  
 Для отключения конечных точек используйте управление на основе политик. Для создания и изменения свойств конечных точек используйте инструкции [CREATE ENDPOINT (Transact-SQL)](../../t-sql/statements/create-endpoint-transact-sql.md) и [ALTER ENDPOINT (Transact-SQL)](../../t-sql/statements/alter-endpoint-transact-sql.md).  
  
## См. также  
 [Центр обеспечения безопасности для базы данных Azure SQL и SQL Server Database Engine](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  