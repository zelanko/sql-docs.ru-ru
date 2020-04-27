---
title: Настройка контактной зоны | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- reducing attackable surface area
- upgrading SQL Server, security
- surface area configuration [SQL Server]
- surface area configuration [SQL Server], about surface area configuration
- attackable surface area [SQL Server]
- installing SQL Server, security
ms.assetid: f741169c-1453-4ad2-830b-bf2be27d712f
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 811db11aecb5e6c0f4c68d272040aea3f8e38ca4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63184535"
---
# <a name="surface-area-configuration"></a>Настройка контактной зоны
  В конфигурации по умолчанию для новых установок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]многие из функций отключены. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выборочно устанавливает и запускает только ключевые службы и функции, чтобы свести к минимуму количество функций, которые могут подвергнуться атаке злоумышленника. Системный администратор может изменить эти значения по умолчанию в ходе установки, а также включать или отключать функции работающего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]по своему выбору. Кроме того, при подключении с других компьютеров определенные компоненты могут быть недоступны до настройки протоколов.  
  
> [!NOTE]  
>  В отличие от новых установок, во время обновления существующие службы или функции не отключаются, но после его завершения могут быть применены дополнительные параметры конфигурации контактной зоны.  
  
## <a name="protocols-connection-and-startup-options"></a>Протоколы, соединение и параметры запуска  
 С помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно запускать и останавливать службы, настраивать параметры запуска и включать протоколы и другие параметры соединения.  
  
#### <a name="to-start-sql-server-configuration-manager"></a>Запуск диспетчера конфигурации SQL Server  
  
1.  В меню **Пуск** последовательно выберите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и щелкните **Диспетчер конфигурации SQL Server**.  
  
    -   Для запуска компонентов и настройки автоматического запуска используйте область **Службы SQL Server** диспетчера конфигурации.  
  
    -   Используйте область **Сетевая конфигурация SQL Server** для включения протоколов и параметров соединения, таких как фиксированные порты TCP/IP или принудительное шифрование.  
  
 Дополнительные сведения см. в разделе [SQL Server Configuration Manager](../sql-server-configuration-manager.md). Возможность удаленного подключения также зависит от правильной настройки брандмауэра. Дополнительные сведения см. в статье [Настройка брандмауэра Windows для разрешения доступа к SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
## <a name="enabling-and-disabling-features"></a>Включение и отключение функций  
 Включение и отключение функций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно настроить с помощью аспектов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-configure-surface-area-using-facets"></a>Настройка контактной зоны с помощью аспектов  
  
1.  В [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] выполните соединение с компонентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Аспекты**.  
  
3.  В диалоговом окне **Просмотр аспектов** разверните список **Аспекты** , выберите соответствующий аспект **Настройка контактной зоны** (**Настройка контактной зоны**, **Настройка контактной зоны для служб Analysis Services**или **Настройка контактной зоны для служб Reporting Services**).  
  
4.  В области **Свойства аспектов** выберите необходимые значения для всех свойств.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 Для периодической проверки конфигурации аспекта используйте управление на основе политик. Дополнительные сведения об управлении на основе политик см. в статье [Администрирование серверов с помощью управления на основе политик](../policy-based-management/administer-servers-by-using-policy-based-management.md).  
  
 Также можно задать параметры компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] при помощи хранимой процедуры `sp_configure`. Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
 Чтобы изменить свойство **Включить встроенную безопасность**[!INCLUDE[ssRS](../../includes/ssrs.md)], используйте настройки свойств в службах [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Чтобы изменить свойство **Планирование событий и доставка отчетов** и свойство **Доступ к веб-службам и HTTP** , измените файл конфигурации **RSReportServer.config** .  
  
## <a name="command-prompt-options"></a>Параметры командной строки  
 Используйте командлет PowerShell **Invoke-PolicyEvaluation**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для вызова политик конфигурации контактной зоны. Дополнительные сведения см. в разделе [Использование командлетов компонента Database Engine](../../database-engine/use-the-database-engine-cmdlets.md).  
  
## <a name="soap-and-service-broker-endpoints"></a>Конечные точки SOAP и Service Broker  
 Для отключения конечных точек используйте управление на основе политик. Для создания и изменения свойств конечных точек используйте инструкции [CREATE ENDPOINT (Transact-SQL)](/sql/t-sql/statements/create-endpoint-transact-sql) и [ALTER ENDPOINT (Transact-SQL)](/sql/t-sql/statements/alter-endpoint-transact-sql).  
  
## <a name="related-content"></a>См. также  
 [Центр безопасности для ядра СУБД SQL Server и Базы данных Azure SQL](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
