---
title: "Поддерживаемые обновления версий и выпусков | Microsoft Docs"
ms.custom: ""
ms.date: "08/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "компоненты [SQL Server], дополнение к существующим установкам"
  - "версии [SQL Server], обновление"
  - "обновление SQL Server, поддерживаются обновления"
  - "поддержка версий на разных языках"
ms.assetid: 702359c4-6ca9-42a8-860c-a95a802898a1
caps.latest.revision: 148
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 147
---
# Поддерживаемые обновления версий и выпусков
  Можно обновить версии [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]и [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. В этом разделе приведены поддерживаемые пути обновления данных версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и поддерживаемые обновления выпусков [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## Контрольный список действий перед обновлением  
  
-   Перед началом обновления выпуска [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] до новой версии проверьте, поддерживаются ли используемые функции в версии, до которой производится обновление.  
  
-   Перед обновлением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]включите проверку подлинности Windows для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и проверьте необходимые настройки конфигурации по умолчанию: является ли учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] членом группы системных администраторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Для обновления до версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] необходимо наличие поддерживаемой операционной системы. Дополнительные сведения см. в разделе [Требования к оборудованию и программному обеспечению для установки SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md).  
  
-   Обновление будет заблокировано, если компьютер ожидает перезагрузки.  
  
-   Обновление будет заблокировано, если не запущена служба установщика Windows.  
  
## Неподдерживаемые сценарии  
  
-   Многоверсионные экземпляры в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] не поддерживаются. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)], а также службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] должны иметь один и тот же номер версии для одного экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   SQL Server 2016 доступен только для 64-разрядных платформ. Межплатформенное обновление не поддерживается. Невозможно обновить 32-разрядный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до стандартного 64-разрядного при помощи программы установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Но можно создать резервную копию или отсоединить базы данных от 32-разрядного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а затем восстановить их или присоединить к новому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (64-разрядная версия), если базы данных не опубликованы в репликации. Необходимо повторно создать имена входа и другие объекты пользователя в системных базах данных master, msdb и model.  
  
-   Добавить новые компоненты в процессе обновления существующего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нельзя. После обновления экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] добавить новые компоненты можно при помощи программы установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Дополнительные сведения см. в разделе [Добавление компонентов в экземпляр SQL Server 2016 (программа установки)](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md).  
 
-   Кластеры отработки отказа не поддерживаются в режиме WOW.  
  
-   Обновление с выпуска Evaluation предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживается.  
  
## Обновление ранних версий до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 
SQL Server 2016 поддерживает обновление со следующих версий SQL Server:
 
- SQL Server 2008 с пакетом обновления 3 (SP3) или более поздней версии;
- SQL Server 2008 R2 с пакетом обновления 2 (SP2) или более поздней версии;
- SQL Server 2012 с пакетом обновления 2 (SP2) или более поздней версии;
- SQL Server 2014 или более поздней версии. 
 

  
> [!NOTE]  
>  Инструкции по обновлению баз данных в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] см. в разделе [Поддержка версии 2005](#SupportFor2005).  
  
 В таблице, представленной ниже, перечислены поддерживаемые сценарии обновления предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
|Исходная версия|Поддерживаемые варианты обновления|  
|------------------|----------------------------|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Enterprise с пакетом обновления 3 (SP3)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Developer с пакетом обновления 3 (SP3)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Standard с пакетом обновления 3 (SP3)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Small Business|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Web с пакетом обновления 3 (SP3)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Workgroup с пакетом обновления 3 (SP3)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Express с пакетом обновления 3 (SP3) |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Datacenter с пакетом обновления 2 (SP2)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise с пакетом обновления 2 (SP2)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Developer с пакетом обновления 2 (SP2)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Small Business с пакетом обновления 2 (SP2)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Standard с пакетом обновления 2 (SP2)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Web с пакетом обновления 2 (SP2)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Workgroup с пакетом обновления 2 (SP2)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Express с пакетом обновления 2 (SP2) |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Enterprise с пакетом обновления 2 (SP2)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Developer с пакетом обновления 2 (SP2)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Разработчик <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Standard с пакетом обновления 2 (SP2)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Web с пакетом обновления 1 (SP1)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web Edition|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Express с пакетом обновления 2 (SP2) |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express <br/> <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Business Intelligence с пакетом обновления 2 (SP2)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Evaluation с пакетом обновления 2 (SP2)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Ознакомительная версия <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Разработчик|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard Edition|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/> |  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Ознакомительная версия|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Evaluation <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Разработчик|  
|[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] версия-кандидат * |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise |  
|[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] Разработчик |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise | 

 \* Предоставляемая корпорацией Майкрософт поддержка обновления с версий-кандидатов предназначена для клиентов, участвовавших в программе адаптации технологий (TAP). 

   
###  <a name="SupportFor2005"></a> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Поддержка [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
 В этом разделе описывается поддержка [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] вы сможете выполнить следующие действия.  
  
-   Присоединить базу данных служб [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (файлы MDF и LDF) к экземпляру [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] компонента Database Engine.  
  
-   Восстановить базу данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] в экземпляре [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] компонента Database Engine.  
  
-   Создать резервную копию куба [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] и восстановить его в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Когда база данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] обновляется до версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], уровень совместимости базы данных будет изменен с 90 на 100. (В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] допустимыми значениями уровня совместимости базы данных являются 100, 110, 120 и 130.) В разделе [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../Topic/ALTER%20DATABASE%20Compatibility%20Level%20\(Transact-SQL\).md) представлены сведения о том, как изменение уровня совместимости может повлиять на приложения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Все сценарии, не указанные в списке выше, не поддерживаются, включая в том числе следующие:  
  
-   Установка [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] на одном компьютере (параллельно).  
  
-   Использование экземпляра [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] в качестве члена топологии репликации, включающего экземпляр [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   Зеркальное отображение базы данных между экземплярами [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .  
  
-   Резервное копирование журнала транзакций с доставкой журналов между экземплярами [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .  
  
-   Настройка связанных серверов между экземплярами [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .  
  
-   Управление экземпляром [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] из среды [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Management Studio.  
  
-   Подключение куба [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Management Studio.  
  
-   Подключение к [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Management Studio.  
  
-   Управление службами [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Management Studio.  
  
-   Поддержка компонентов служб Integration Services [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] сторонних разработчиков, например выполнение и обновление.  
  
## [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Обновление выпуска  
 В следующей таблице перечислены поддерживаемые сценарии обновлений в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Пошаговые инструкции по обновлению выпуска см. в разделе [Обновление до другого выпуска SQL Server 2016 (программа установки)](../../database-engine/install-windows/upgrade-to-a-different-edition-of-sql-server-2016-setup.md).  
  
|Исходная версия|Обновленная версия|  
|------------------|----------------|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (лицензия Server+CAL и Core) **|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise |  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Evaluation Enterprise **|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (лицензия Server+CAL или Core) <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web Edition <br/> <br/> Обновление с переходом от Evaluation (бесплатного выпуска) на любой из платных выпусков поддерживается для изолированных, но не поддерживается для кластеризованных установок.|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard **|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (лицензия Server+CAL или Core)|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer **|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (лицензия Server+CAL или Core) <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web Edition <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web Edition|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (лицензия Server+CAL или Core) <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard Edition|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Express *|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (лицензия Server+CAL или Core) <br/><br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Разработчик <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard <br/> <br/> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Web Edition|  
  
 Кроме того, можно выполнить обновление выпуска между выпусками [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (лицензия Server+CAL) и [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (лицензия Core).  
  
|Обновление выпуска c|Обновление выпуска до|  
|--------------------------|------------------------|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (лицензия Server+CAL) **|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (лицензия Core)|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (лицензия Core)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise (лицензия Server+CAL)|  
  
 \* Также относится к [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], экспресс-выпуск с инструментами и [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], экспресс-выпуск с дополнительными службами.  
  
 ** При смене выпуска для отказоустойчивого кластера [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] действуют определенные ограничения. Следующие сценарии не поддерживаются для кластеров отработки отказа [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer, Standard или Evaluation.  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard или Evaluation.  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Evaluation.  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Evaluation до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Standard.  
  
## См. также:  
 [Возможности, поддерживаемые различными выпусками SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)   
 [Требования к оборудованию и программному обеспечению для установки SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)   
 [Обновление до SQL Server 2016](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)  
  
  