---
title: Обновление служб Master Data Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 9c3543f3-3eb9-455d-a9bf-f17e9506ad21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1d60defaef135a87669b9f87257e0856f0c1dca2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079679"
---
# <a name="upgrade-master-data-services"></a>Обновление служб Master Data Services
  Существует четыре варианта обновления до Microsoft [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2. Выберите тот из них, который лучше всего подходит в конкретной ситуации.  
  
-   [Обновление без обновления компонента Database Engine](#noengine)  
  
-   [Обновление с обновлением компонента Database Engine](#engine)  
  
-   [Обновление при использовании двух компьютеров](#twocomputer)  
  
-   [Обновление с восстановлением базы данных из резервной копии](#restore)  
  
> [!IMPORTANT]  
>  -   Не поддерживается обновление с версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP1 в версии CTP2.  
> -   Создайте резервную копию базы данных перед выполнением каких-либо обновлений.  
> -   В процессе обновления повторно создаются хранимые процедуры, а также обновляются таблицы, используемые в [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. Любая настройка какого-либо из этих компонентов может быть потеряна после обновления.  
> -   Пакеты развертывания модели можно использовать только в выпуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в котором они были созданы. Невозможно развернуть пакеты развертывания модели, созданные в [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] / [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
> -   Вы можете продолжать использовать [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] версии с пакетом обновления 1 из образца данных службы надстройки для Excel после обновления службы Master Data Services и Data Quality Services до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2. Однако любая более ранняя версия надстройки служб Master Data Services для Excel перестанет работать после обновления до версии SQL Server 2014 CTP2. Вы можете скачать [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] версии с пакетом обновления 1 из образца данных службы надстройки для Excel из [здесь](http://go.microsoft.com/fwlink/?LinkId=328664).  
  
##  <a name="noengine"></a> Обновление без обновления компонента Database Engine  
 Этот вариант можно рассматривать как side-by-side установку, поскольку оба [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] / [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] устанавливаются параллельно на одном компьютере или разных компьютерах.  
  
 В этом случае можно продолжить использовать [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] для размещения базы данных служб MDS. Однако схему базы данных служб MDS необходимо обновить, после чего для доступа к ней необходимо будет создать веб-приложение [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . База данных служб MDS больше не доступна с помощью веб-приложения [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
 Если вы решили установить [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и более ранней версии SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]/[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) на одном компьютере, это можно сделать так, как файлы устанавливаются в другом месте.  
  
-   По умолчанию в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]файлы устанавливаются в каталог *диск*:\Program Files\Microsoft SQL Server\120\Master Data Services.  
  
-   По умолчанию в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]файлы устанавливаются в каталог *диск*:\Program Files\Microsoft SQL Server\110\Master Data Services.  
  
-   По умолчанию в [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]файлы устанавливаются в каталог *диск*:\Program Files\Microsoft SQL Server\Master Data Services.  
  
 Чтобы выполнить эту задачу, требуются следующие действия.  
  
1.  Установите службы [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] и любые другие требуемые компоненты.  
  
    1.  Откройте мастер установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
    2.  На панели слева щелкните **Установка**.  
  
    3.  На панели справа щелкните **Новая установка изолированного экземпляра SQL Server или добавление компонентов к существующей установке**.  
  
    4.  На странице **Выбор компонентов** выберите службы **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** и любые другие компоненты, которые необходимо установить.  
  
    5.  Завершите работу мастера.  
  
2.  По завершении установки обновите схему базы данных служб MDS.  
  
    1.  Откройте версию [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
        > [!IMPORTANT]  
        >  Чтобы обновить схему базы данных служб MDS, необходимо выполнить вход с учетной записью администратора, указанной при создании базы данных служб MDS. В базе данных служб MDS, в таблице mdm.tblUser, этот пользователь имеет свойство **ID** со значением **1**. Дополнительные сведения об изменении этого пользователя, см. в разделе [изменить учетную запись системного администратора &#40;службы Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
    2.  На панели слева щелкните **Конфигурация базы данных**.  
  
    3.  В области справа щелкните **Выбор базы данных** и укажите сведения для вашего [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] экземпляр базы данных.  
  
    4.  Нажмите кнопку **Обновить базу данных** , чтобы запустить **мастер обновления баз данных**. Дополнительные сведения см. в разделе [Мастер обновления баз данных (диспетчер конфигурации служб Master Data Services)](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).  
  
3.  После завершения обновления создайте веб-приложение [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    1.  Откройте версию [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
    2.  На панели слева щелкните элемент **Веб-конфигурация**.  
  
    3.  На панели справа в списке **Веб-сайт** выберите один из следующих вариантов.  
  
        -   **Веб-сайт по умолчанию**и щелкните **Создать приложение**.  
  
        -   **Создать новый сайт**. При создании нового веб-сайта автоматически создается новое веб-приложение.  
  
        > [!IMPORTANT]  
        >  На существующей веб-приложением MDS с более ранней версии SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) для выбора доступны в выпуске SQL Server 2014 диспетчер конфигурации служб Master Data Services. Не следует выбрать существующее веб-приложение, и вместо этого следует создать веб-приложение [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для MDS. В противном случае произойдет ошибка при попытке связать веб-приложение обновленной базы данных MDS, которые были запрашиваемая страница недоступна из-за неверной конфигурации данных для этой страницы.  
        >   
        >  Если необходимо использовать одинаковые имена (псевдонимы) для веб-приложением MDS, где будет находиться существующих ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) веб-приложения, необходимо сначала удалить веб-приложения и пул приложений, связанный с IIS, а затем создать веб-приложение с тем же именем в версии SQL Server 2014 диспетчер конфигурации служб Master Data Services. Дополнительные сведения об удалении веб-приложения и пулов приложений из служб IIS см. в разделах [Удаление приложения (IIS)](http://go.microsoft.com/fwlink/?LinkId=323537) и [Удаление пула приложений (IIS)](http://go.microsoft.com/fwlink/?LinkId=323538).  
  
4.  Теперь свяжите новое веб-приложение с обновленной базой данных служб MDS.  
  
    1.  В разделе **Связать приложение с базой данных** щелкните **Выбрать**.  
  
    2.  Выберите базу данных служб MDS.  
  
    3.  Нажмите кнопку **Применить**.  
  
##  <a name="engine"></a> Обновление с обновлением компонента Database Engine  
 В этом сценарии выполняется обновление компонента Database Engine и приложения [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] с версии [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или SQL Server 2012 до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Чтобы выполнить эту задачу, требуются следующие действия.  
  
1.  **Только для [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]**. Откройте **панель управления** > **Программы и компоненты** и удалите Microsoft [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
2.  Обновите компонент Database Engine до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    1.  Откройте мастер установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
    2.  На панели слева щелкните **Установка**.  
  
    3.  В области справа щелкните **обновление с SQL Server 2005, SQL Server 2008, SQL Server 2008 R2 или SQL Server 2012**.  
  
    4.  Завершите работу мастера.  
  
3.  **Для [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] только**: Если обновление будет завершено, добавьте **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** функции.  
  
    1.  Откройте мастер установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
    2.  На панели слева щелкните **Установка**.  
  
    3.  На панели справа щелкните **Новая установка изолированного экземпляра SQL Server или добавление компонентов к существующей установке**.  
  
    4.  На **тип установки** странице мастера выберите **Добавление компонентов к существующему экземпляру** параметр и выберите экземпляр, где установлена база данных MDS.  
  
    5.  На **Выбор компонентов** раздела **общие компоненты**выберите **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]**.  
  
    6.  Завершите работу мастера.  
  
4.  Обновить схему базы данных MDS.  
  
    1.  Откройте версию [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
        > [!IMPORTANT]  
        >  Чтобы обновить схему базы данных служб MDS, необходимо выполнить вход с учетной записью администратора, указанной при создании базы данных служб MDS. В базе данных служб MDS, в таблице mdm.tblUser, этот пользователь имеет свойство **ID** со значением **1**. Дополнительные сведения об изменении этого пользователя, см. в разделе [изменить учетную запись системного администратора &#40;службы Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
    2.  На панели слева щелкните **Конфигурация базы данных**.  
  
    3.  В области справа щелкните **Выбор базы данных** и укажите сведения об экземпляре базы данных.  
  
    4.  Нажмите кнопку **Обновить базу данных** , чтобы запустить **мастер обновления баз данных**. Дополнительные сведения см. в разделе [Мастер обновления баз данных (диспетчер конфигурации служб Master Data Services)](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).  
  
    5.  Нажмите кнопку **Применить**.  
  
5.  После завершения обновления создайте веб-приложение [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    1.  Откройте версию [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
    2.  На панели слева щелкните элемент **Веб-конфигурация**.  
  
    3.  На панели справа в списке **Веб-сайт** выберите один из следующих вариантов.  
  
        -   **Веб-сайт по умолчанию**и щелкните **Создать приложение**.  
  
        -   **Создать новый сайт**. При создании нового веб-сайта автоматически создается новое веб-приложение.  
  
        > [!IMPORTANT]  
        >  На существующей веб-приложением MDS с более ранней версии SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) для выбора доступны в выпуске [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] диспетчер конфигурации служб Master Data Services. Не следует выбрать существующее веб-приложение, и вместо этого следует создать веб-приложение [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для MDS. В противном случае произойдет ошибка при попытке связать веб-приложение обновленной базы данных MDS, которые были запрашиваемая страница недоступна из-за неверной конфигурации данных для этой страницы.  
        >   
        >  Если необходимо использовать одинаковые имена (псевдонимы) для веб-приложением MDS, где будет находиться существующих ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) веб-приложения, необходимо сначала удалить веб-приложения и пул приложений, связанный с IIS, а затем создать веб-приложение с тем же именем в версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], диспетчер конфигурации служб Master Data Services. Дополнительные сведения об удалении веб-приложения и пулов приложений из служб IIS см. в разделах [Удаление приложения (IIS)](http://go.microsoft.com/fwlink/?LinkId=323537) и [Удаление пула приложений (IIS)](http://go.microsoft.com/fwlink/?LinkId=323538).  
  
6.  Теперь свяжите новое веб-приложение с обновленной базой данных служб MDS.  
  
    1.  В разделе **Связать приложение с базой данных** щелкните **Выбрать**.  
  
    2.  Выберите базу данных служб MDS.  
  
    3.  Нажмите кнопку **Применить**.  
  
##  <a name="twocomputer"></a> Обновление при использовании двух компьютеров  
 Этот сценарий включает обновление системы, в которой SQL Server установлен на двух компьютерах: один с [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], а другой — с SQL Server 2008 R2 или SQL Server 2012.  
  
 Если установлена версия [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], то [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] соответственно продолжает использоваться для размещения базы данных служб MDS на одном компьютере. Однако схему базы данных служб MDS необходимо обновить, после чего для доступа к ней необходимо будет использовать веб-приложение [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . База данных служб MDS больше не доступна с помощью веб-приложения [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
-   По умолчанию в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]файлы устанавливаются в каталог *диск*:\Program Files\Microsoft SQL Server\120\Master Data Services.  
  
-   По умолчанию в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]файлы устанавливаются в каталог *диск*:\Program Files\Microsoft SQL Server\110\Master Data Services.  
  
-   По умолчанию в [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]файлы устанавливаются в каталог *диск*:\Program Files\Microsoft SQL Server\Master Data Services.  
  
 Чтобы выполнить эту задачу, требуются следующие действия.  
  
1.  Установите службы [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] и любые другие требуемые компоненты.  
  
    1.  Откройте мастер установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
    2.  На панели слева щелкните **Установка**.  
  
    3.  На панели справа щелкните **Новая установка изолированного экземпляра SQL Server или добавление компонентов к существующей установке**.  
  
    4.  На странице **Выбор компонентов** выберите службы **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** и любые другие компоненты, которые необходимо установить.  
  
    5.  Завершите работу мастера.  
  
2.  По завершении установки обновите схему базы данных служб MDS.  
  
    1.  Откройте версию [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
        > [!IMPORTANT]  
        >  Чтобы обновить схему базы данных служб MDS, необходимо выполнить вход с учетной записью администратора, указанной при создании базы данных служб MDS. В базе данных служб MDS, в таблице mdm.tblUser, этот пользователь имеет свойство **ID** со значением **1**. Дополнительные сведения об изменении этого пользователя, см. в разделе [изменить учетную запись системного администратора &#40;службы Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
    2.  На панели слева щелкните **Конфигурация базы данных**.  
  
    3.  В области справа щелкните **Выбор базы данных** и укажите сведения для вашего [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] базы данных экземпляра на другом компьютере, если [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] устанавливается на другом компьютере.  
  
    4.  Нажмите кнопку **Обновить базу данных** , чтобы запустить **мастер обновления баз данных**. Дополнительные сведения см. в разделе [Мастер обновления баз данных (диспетчер конфигурации служб Master Data Services)](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).  
  
3.  После завершения обновления создайте веб-приложение SQL Server 2014.  
  
    1.  Откройте версию [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
    2.  На панели слева щелкните элемент **Веб-конфигурация**.  
  
    3.  На панели справа в списке **Веб-сайт** выберите один из следующих вариантов.  
  
        -   **Веб-сайт по умолчанию**и щелкните **Создать приложение**.  
  
        -   **Создать новый сайт**. При создании нового веб-сайта автоматически создается новое веб-приложение.  
  
        > [!IMPORTANT]  
        >  На существующей веб-приложением MDS с более ранней версии SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) для выбора доступны в выпуске [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] диспетчер конфигурации служб Master Data Services. Не следует выбрать существующее веб-приложение, и вместо этого следует создать веб-приложение [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для MDS. В противном случае произойдет ошибка при попытке связать веб-приложение обновленной базы данных MDS, которые были запрашиваемая страница недоступна из-за неверной конфигурации данных для этой страницы.  
        >   
        >  Если необходимо использовать одинаковые имена (псевдонимы) для веб-приложением MDS, где будет находиться существующих ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) веб-приложения, необходимо сначала удалить веб-приложения и пул приложений, связанный с IIS, а затем создать веб-приложение с тем же именем в версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], диспетчер конфигурации служб Master Data Services. Дополнительные сведения об удалении веб-приложения и пулов приложений из служб IIS см. в разделах [Удаление приложения (IIS)](http://go.microsoft.com/fwlink/?LinkId=323537) и [Удаление пула приложений (IIS)](http://go.microsoft.com/fwlink/?LinkId=323538).  
  
4.  Теперь свяжите веб-приложение с обновленной базой данных служб MDS.  
  
    1.  В разделе **Связать приложение с базой данных** щелкните **Выбрать**.  
  
    2.  Выберите базу данных служб MDS.  
  
    3.  Нажмите кнопку **Применить**.  
  
##  <a name="restore"></a> Обновление с восстановлением базы данных из резервной копии  
 В этом случае [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] устанавливается вместе с SQL Server 2008 R2 или SQL Server 2012 на том же компьютере или на разных компьютерах 2. Кроме того, резервная копия базы данных создана на версии более ранней, чем версия [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2, перед обновлением и базы данных должны быть восстановлены.  
  
-   По умолчанию в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]файлы устанавливаются в каталог *диск*:\Program Files\Microsoft SQL Server\120\Master Data Services.  
  
-   По умолчанию в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]файлы устанавливаются в каталог *диск*:\Program Files\Microsoft SQL Server\110\Master Data Services.  
  
-   По умолчанию в [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]файлы устанавливаются в каталог *диск*:\Program Files\Microsoft SQL Server\Master Data Services.  
  
 Чтобы выполнить эту задачу, требуются следующие действия.  
  
1.  Установите службы [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] и любые другие требуемые компоненты.  
  
    1.  Откройте мастер установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
    2.  На панели слева щелкните **Установка**.  
  
    3.  На панели справа щелкните **Новая установка изолированного экземпляра SQL Server или добавление компонентов к существующей установке**.  
  
    4.  На странице **Выбор компонентов** выберите службы **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** и любые другие компоненты, которые необходимо установить.  
  
    5.  Завершите работу мастера.  
  
2.  Восстановите базу данных, для которой была создана резервная копия.  
  
3.  По завершении установки обновите схему базы данных служб MDS.  
  
    1.  Откройте версию [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
        > [!IMPORTANT]  
        >  Чтобы обновить схему базы данных служб MDS, необходимо выполнить вход с учетной записью администратора, указанной при создании базы данных служб MDS. В базе данных служб MDS, в таблице mdm.tblUser, этот пользователь имеет свойство **ID** со значением **1**. Дополнительные сведения об изменении этого пользователя, см. в разделе [изменить учетную запись системного администратора &#40;службы Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
    2.  На панели слева щелкните **Конфигурация базы данных**.  
  
    3.  В области справа щелкните **Выбор базы данных** и укажите сведения для вашего [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] экземпляр базы данных.  
  
    4.  Нажмите кнопку **Обновить базу данных** , чтобы запустить **мастер обновления баз данных**. Дополнительные сведения см. в разделе [Мастер обновления баз данных (диспетчер конфигурации служб Master Data Services)](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).  
  
4.  После завершения обновления создайте веб-приложение [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    1.  Откройте версию [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
    2.  На панели слева щелкните элемент **Веб-конфигурация**.  
  
    3.  На панели справа в списке **Веб-сайт** выберите один из следующих вариантов.  
  
        -   **Веб-сайт по умолчанию**и щелкните **Создать приложение**.  
  
        -   **Создать новый сайт**. При создании нового веб-сайта автоматически создается новое веб-приложение.  
  
        > [!IMPORTANT]  
        >  На существующей веб-приложением MDS с более ранней версии SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) для выбора доступны в выпуске [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] диспетчер конфигурации служб Master Data Services. Не следует выбрать существующее веб-приложение, и вместо этого следует создать веб-приложение [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для MDS. В противном случае произойдет ошибка при попытке связать веб-приложение обновленной базы данных MDS, которые были запрашиваемая страница недоступна из-за неверной конфигурации данных для этой страницы.  
        >   
        >  Если необходимо использовать одинаковые имена (псевдонимы) для веб-приложением MDS, где будет находиться существующих ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) веб-приложения, необходимо сначала удалить веб-приложения и пул приложений, связанный с IIS, а затем создать веб-приложение с тем же именем в версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], диспетчер конфигурации служб Master Data Services. Дополнительные сведения об удалении веб-приложения и пулов приложений из служб IIS см. в разделах [Удаление приложения (IIS)](http://go.microsoft.com/fwlink/?LinkId=323537) и [Удаление пула приложений (IIS)](http://go.microsoft.com/fwlink/?LinkId=323538).  
  
5.  Теперь свяжите новое веб-приложение с обновленной базой данных служб MDS.  
  
    1.  В разделе **Связать приложение с базой данных** щелкните **Выбрать**.  
  
    2.  Выберите базу данных служб MDS.  
  
    3.  Нажмите кнопку **Применить**.  
  
## <a name="troubleshooting"></a>Устранение неполадок  
 **Проблема:** при открытии [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] отображается веб-приложения, сообщение об ошибке «версия клиента несовместима с версией базы данных».  
  
 **Решение:** эта проблема возникает, когда [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] веб-приложения диспетчера основных данных пытается получить доступ к базе данных, который был обновлен для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] службы Master Data Services. Следует использовать веб-приложение [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
 Она также может возникнуть, если не были выполнены останов и перезапуск **пула приложений служб MDS** в IIS при обновлении схемы базы данных служб MDS. Перезапустите **пул приложений служб MDS** , чтобы устранить проблему.  
  
## <a name="see-also"></a>См. также  
 [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
