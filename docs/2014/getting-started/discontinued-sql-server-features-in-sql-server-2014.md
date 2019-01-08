---
title: Неподдерживаемые функции SQL Server в SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 0678bfbc-5d3f-44f4-89c0-13e8e52404da
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 028d14230f0f48f04bd94f327c1e46c5bee42b56
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53351017"
---
# <a name="discontinued-sql-server-features-in-sql-server-2014"></a>Функции SQL Server, больше не поддерживаемые в SQL Server 2014
  В этом разделе описаны функции, которые становятся недоступными после обновления до [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
## <a name="discontinued-features-in-includesssql14includessssql14-mdmd"></a>Неподдерживаемые функции в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 В [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] нет неподдерживаемых функций.  
  
## <a name="discontinued-features-in-includesssql11includessssql11-mdmd"></a>Неподдерживаемые функции в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="discontinued-active-directory-helper-service"></a>Неподдерживаемая служба поддержки Active Directory  
 Служба поддержки Active Directory больше не поддерживается, а связанные с ней компоненты удалены. В следующей таблице перечислены связанные компоненты, которые были удалены.  
  
|Категория|Неподдерживаемая функция|Замена|  
|--------------|--------------------------|-----------------|  
|Системные хранимые процедуры|sp_ActiveDirectory_Obj<br /><br /> sp_ActiveDirectory_SCP<br /><br /> sp_ActiveDirectory_Start|Замена отсутствует|  
  
## <a name="discontinued-features-in-sql-server-2008-r2"></a>Функции, неподдерживаемые в SQL Server 2008 R2  
  
### <a name="64-bit-platform-support-in-reporting-services"></a>Поддержка 64-разрядной платформы в службах Reporting Services  
 Начиная с выпуска [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] компонент служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] не поддерживает серверы на основе процессоров Itanium под управлением Windows Server 2003 или Windows Server 2003 R2. Службы [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] по-прежнему поддерживают другие 64-разрядные ОС, в том числе Windows Server 2008 и Windows Server 2008 R2 для систем на основе процессоров Itanium. Чтобы обновить установленный экземпляр [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] со службами [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], работающий под управлением Windows Server 2003 или Windows Server 2003 R2 для систем на основе процессоров Itanium, до выпуска [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], необходимо предварительно обновить операционную систему.  
  
## <a name="discontinued-features-in-sql-server-2008"></a>Функции, неподдерживаемые в SQL Server 2008  
  
### <a name="discontinued-sql-dmo-from-sql-server-express-installation"></a>Неподдерживаемые функции SQL-DMO при установке SQL Server Express  
 Распределенные управляющие объекты SQL (SQL-DMO) для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] были удалены из [!INCLUDE[ssExpressEd10](../includes/ssexpressed10-md.md)]. Рекомендуется как можно скорее внести изменения в приложения, которые пользуют эти компоненты. Если требуется поддержка объектов SQL-DMO для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] необходима, установите компоненты обратной совместимости из [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] пакета возможностей [центра загрузки Майкрософт](https://go.microsoft.com/fwlink/?LinkID=51230). В дальнейшем для разработки пользуйтесь объектами SMO ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Objects).  
  
### <a name="discontinued-option-for-web-assistant"></a>Неподдерживаемый параметр для помощника Web Assistant  
 Параметр `sp_configure` для включения помощника Web Assistant удален из [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]. Вместо этого рекомендуется использовать [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
### <a name="surface-area-configuration-tool"></a>Средство настройки контактной зоны  
 Поддержка средства настройки контактной зоны в [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] прекращена. В следующей таблице показаны средства, с помощью которых можно настраивать параметры и функции компонентов в этой версии.  
  
|Параметры замены и функции компонентов|Порядок настройки|  
|-------------------------------------------------|----------------------|  
|Протоколы, соединение и параметры запуска|Используйте диспетчер конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|  
|Функции служб [!INCLUDE[ssDE](../includes/ssde-md.md)]|Используйте управление на уровне политик, значения свойств в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] или хранимую процедуру sp_Configure.|  
|Функции служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|Используйте значения свойств в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Свойство включить встроенную безопасность|Используйте значения свойств в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -«Планирование событий и доставка отчетов» и «Веб-службы и доступ по HTTP»|Измените файл конфигурации RSReportServer.config.|  
|Параметры командной строки|В этой версии не поддерживается.|  
|Конечные точки SOAP и [!INCLUDE[ssSB](../includes/sssb-md.md)]|Используйте [CREATE ENDPOINT](/sql/t-sql/statements/create-endpoint-transact-sql)и [ALTER ENDPOINT](/sql/t-sql/statements/alter-endpoint-transact-sql).|  
  
### <a name="discontinued-command-prompt-parameters-for-sql-server-setup"></a>Неподдерживаемые параметры командной строки для программы установки SQL Server  
 В следующей таблице перечислены параметры командной строки из предыдущих версий [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], которые не поддерживаются в [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].  
  
|Неподдерживаемый параметр|Параметр замены|  
|----------------------------|---------------------------|  
|ADDLOCAL|/ACTION=Uninstall и /FEATURES|  
|DISABLENETWORKPROTOCOLS|/ TCPENABLED для TCP/IP<sup>1</sup>|  
|DISABLENETWORKPROTOCOLS|/ NPENABLED для именованных каналов<sup>1</sup>|  
|INSTALLSQLDATADIR|/SQLUSERDBDIR<br /><br /> /SQLUSERDBLOGDIR<br /><br /> /SQLBACKUPDIR<br /><br /> /SQLTEMPDBDIR<br /><br /> /SQLTEMPDBLOGDIR|  
|REINSTALL|Нет эквивалента в этой версии.|  
|REINSTALLMODE|Нет эквивалента в этой версии.|  
|REMOVE|/ACTION=Uninstall и /FEATURES|  
|SAMPLEDATABASE|Нет эквивалента в этой версии.|  
|SAVESYSDB|Нет эквивалента в этой версии.|  
|SKUUPGRADE<sup>2</sup>|Нет эквивалента в этой версии.|  
|UPGRADE|/ACTION=Upgrade и /FEATURES|  
|USESYSDB|Нет эквивалента в этой версии.|  
  
 <sup>1</sup>эти параметры допустимы только для установки.  
  
 <sup>2</sup>запуск [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], задайте параметр/Action = EditionUpgrade, для обновления существующего выпуска [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] до другого выпуска без использования исходном установочном носителе. Дополнительные сведения о поддерживаемой версии и обновлении выпуском см. в разделе [Supported Version and Edition Upgrades](../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
 Дополнительные сведения см. в статье [Установка SQL Server 2014 из командной строки](../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
  
