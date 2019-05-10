---
title: Требования для веб-приложений (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9455d3cf-c1b7-4d48-8aff-7dc636ed5dc3
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 15b394c836cb24229944f4e0775dfccad847a32b
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65482887"
---
# <a name="web-application-requirements-master-data-services"></a>Требования веб-приложений (службы Master Data Services)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] — это веб-приложение, размещенное в службах IIS. [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] работает только в Internet Explorer (IE) 7 или более поздней версии. Internet Explorer 7 и более ранние версии, а также Microsoft Edge и Chrome не поддерживаются.  
  
 С помощью программы [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] создайте и настройте веб-приложение для размещения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] . [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] настраивает службы IIS на локальном компьютере, поэтому она лучше всего подходит для начальных задач веб-конфигурации. Например, можно настроить службы [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] с одним веб-приложением [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] или первое веб-приложение в конфигурации с масштабным развертыванием служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. С помощью средств IIS выполняются более сложные задачи, например настройка нескольких веб-серверов в конфигурации с масштабным развертыванием.  
  
> [!NOTE]  
>  Любой компьютер, на котором устанавливаются компоненты [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , должен иметь соответствующие лицензии. Дополнительные сведения см. в лицензионном соглашении.  
  
## <a name="requirements"></a>Требования  
  
### <a name="operating-system"></a>Операционная система  
 В следующие операционные системы Windows входят компоненты служб IIS, необходимые для веб-приложения и веб-службы [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .  
  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer Edition x64 (64-разрядная версия)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise x64 (64-разрядная версия)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Business Intelligence x64 (64-разрядная версия)|  
|-------------------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------|  
|[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] с пакетом обновления 2 (SP2)<br /><br /> Windows Server 2008 R2 с пакетом обновления 1 (SP1)<br /><br /> Windows 7 Профессиональная, Корпоративная и Максимальная<br /><br /> Windows 8.0 Профессиональная, Корпоративная и Максимальная|[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] с пакетом обновления 2 (SP2)<br /><br /> Windows Server 2008 R2 с пакетом обновления 1 (SP1)<br /><br /> Windows Server 2012|[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] с пакетом обновления 2 (SP2)<br /><br /> Windows Server 2008 R2 с пакетом обновления 1 (SP1)<br /><br /> Windows Server 2012|  
  
 Полный список операционных систем Windows, которые поддерживаются для конкретных выпусков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [оборудованию и программному обеспечению для установки SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
### <a name="microsoft-silverlight"></a>Microsoft Silverlight  
 Для работы в веб-приложении [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] на клиентском компьютере необходимо установить Silverlight 5. Если требуемая версия Silverlight отсутствует, то при переходе к той части веб-приложения, которая использует Silverlight, программа предложит установить Silverlight. Вы можете установить Silverlight 5 [с этой веб-страницы](https://go.microsoft.com/fwlink/?LinkId=243096).  
  
### <a name="role-and-role-services-windows-server-2008-or-windows-server-2008-r2-windows-7-operating-systems"></a>Роль и службы ролей (операционные системы Windows Server 2008 или Windows Server 2008 R2, Windows 7)  
 В Windows Server 2008 R2 можно использовать **Диспетчер сервера**, доступный в консоли управления (MMC), для установки роли **Веб-сервер (IIS)** и следующих необходимых служб ролей.  
  
> [!NOTE]  
>  В [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] и Windows 7 для включения этих параметров в диалоговом окне **Компоненты Windows** используйте компонент **Программы и компоненты** на панели управления.  
  
||  
|-|  
|Веб-сервер<br /><br /> Общие функции HTTP<br /><br /> Статическое содержимое<br /><br /> Документ по умолчанию<br /><br /> Обзор каталога<br /><br /> Ошибки HTTP<br /><br /> Разработка приложений<br /><br /> ASP.NET<br /><br /> Расширяемость платформы .NET<br /><br /> Расширения ISAPI<br /><br /> Фильтры ISAPI<br /><br /> Исправность и диагностика<br /><br /> Ведение журнала служб HTTP<br /><br /> Монитор запросов<br /><br /> безопасность<br /><br /> Проверка подлинности Windows<br /><br /> Фильтрация запросов<br /><br /> Производительность<br /><br /> Сжатие статического содержимого<br /><br /> Средства управления<br /><br /> Консоль управления (IIS)|  
  
### <a name="role-and-role-services-windows-server-2012-or-windows-8-operating-systems"></a>Роль и службы ролей (операционные системы Windows Server 2012 или Windows 8)  
 В Windows Server 2012 можно использовать **Диспетчер сервера**, доступный в консоли управления (MMC), для установки роли **Веб-сервер (IIS)** и следующих необходимых служб ролей.  
  
> [!NOTE]  
>  В операционной системе Windows 8 воспользуйтесь компонентом **Программы и компоненты** на панели управления для включения этих параметров в диалоговом окне **Компоненты Windows** .  
  
||  
|-|  
|Службы IIS<br /><br /> Средства управления веб-сайтом<br /><br /> Консоль управления (IIS)<br /><br /> Веб-службы Интернета<br /><br /> Разработка приложений<br /><br /> Расширяемость платформы .NET версии 3.5<br /><br /> Расширяемость платформы .NET версии 4.5<br /><br /> ASP.NET 3.5<br /><br /> ASP.NET 4.5<br /><br /> Расширения ISAPI<br /><br /> Фильтры ISAPI<br /><br /> Общие функции HTTP<br /><br /> Документ по умолчанию<br /><br /> Обзор каталога<br /><br /> Ошибки HTTP<br /><br /> Статическое содержимое<br /><br /> [Примечание: Не устанавливайте протокол публикации WebDAV]<br /><br /> Исправность и диагностика<br /><br /> Ведение журнала служб HTTP<br /><br /> Монитор запросов<br /><br /> Производительность<br /><br /> Сжатие статического содержимого<br /><br /> безопасность<br /><br /> Фильтрация запросов<br /><br /> Проверка подлинности Windows|  
  
### <a name="features-windows-server-2008-or-windows-server-2008-r2-windows-7-operating-systems"></a>Компоненты (операционные системы Windows Server 2008 или Windows Server 2008 R2, Windows 7)  
 В [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] или Windows Server 2008 R2 приведенные ниже компоненты можно установить с помощью **Диспетчера сервера** .  
  
> [!NOTE]  
>  В [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] и Windows 7 для включения этих параметров в диалоговом окне **Компоненты Windows** используйте компонент **Программы и компоненты** на панели управления.  
  
||  
|-|  
|Компоненты платформы .NET Framework 3.0.<br /><br /> Активация WCF<br /><br /> Активация HTTP<br /><br /> Не-HTTP активация<br /><br /> Служба активации Windows<br /><br /> Модель процесса<br /><br /> Среда .NET<br /><br /> API-интерфейсы конфигурации|  
  
### <a name="features-windows-server-2012-or-windows-8-operating-systems"></a>Компоненты (операционные системы Windows Server 2012 или Windows 8)  
 В Windows Server 2012 приведенные ниже компоненты можно установить с помощью **Диспетчера сервера** .  
  
> [!NOTE]  
>  В операционной системе Windows 8 воспользуйтесь компонентом **Программы и компоненты** на панели управления для включения этих параметров в диалоговом окне **Компоненты Windows** .  
  
||  
|-|  
|.NET Framework 3.5 (включая .NET 2.0 и 3.0)<br /><br /> Дополнительные службы .NET Framework 4.5 Advanced Services<br /><br /> ASP.NET 4.5<br /><br /> Службы WCF<br /><br /> Активация HTTP [Примечание: Это необходимо.]<br /><br /> Совместное использование TCP-порта<br /><br /> Служба активации Windows<br /><br /> Модель процесса<br /><br /> Среда .NET<br /><br /> API-интерфейсы конфигурации|  
  
### <a name="accounts-and-permissions"></a>Учетные записи и разрешения  
  
|Тип|Описание|  
|----------|-----------------|  
|Учетная запись Windows|Выполнять вход на компьютер веб-сервера необходимо с учетной записью Windows, которая имеет разрешения на настройку ролей Windows, служб ролей и компонентов, а также на создание пулов приложений, веб-сайтов и веб-приложений в службах IIS на локальном компьютере и управление ими.|  
|Учетная запись службы|При создании веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] в программе [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]необходимо указать удостоверение для пула приложений, в котором оно выполняется. Эта учетная запись может отличаться от учетной записи службы, которая была указана при создании базы данных служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .<br /><br /> Данное удостоверение должно быть учетной записью пользователя домена, оно добавляется к роли базы данных mds_exec в базе данных служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] для доступа к ней. Дополнительные сведения см. в разделе [Имена входа, пользователи и роли базы данных (службы Master Data Services)](../database-logins-users-and-roles-master-data-services.md). Данная учетная запись также добавляется в группу Windows [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], **MDS_ServiceAccounts**, которой предоставляется разрешение на доступ к временному каталогу компиляции **MDSTempDir** в файловой системе. Дополнительные сведения см. в разделе [Разрешения для папок и файлов (службы Master Data Services)](../folder-and-file-permissions-master-data-services.md).<br /><br /> Учетной записи пула приложений требуется разрешение VIEW SERVER STATE, чтобы исключить ошибки сервера. Например, команда MDS Validate Version завершается неудачно с ошибкой сервера. Дополнительные сведения см. в статье [Неудачное завершение команды MDS Validate Version с ошибкой сервера в SQL Server 2012 и SQL Server 2014](https://go.microsoft.com/fwlink/p/?LinkId=526304).|  
  
## <a name="see-also"></a>См. также  
 [Установка служб Master Data Services](install-master-data-services.md)   
 [Создание веб-приложения мастера основных данных (службы Master Data Services)](create-a-master-data-manager-web-application-master-data-services.md)   
 [Страница "Веб-конфигурация" (диспетчер конфигурации Master Data Services)](../web-configuration-page-master-data-services-configuration-manager.md)  
  
  
