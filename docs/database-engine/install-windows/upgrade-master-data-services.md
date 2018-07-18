---
title: Обновление служб Master Data Services | Документы Майкрософт
ms.custom: ''
ms.date: 07/21/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9c3543f3-3eb9-455d-a9bf-f17e9506ad21
caps.latest.revision: 31
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3295485f0c5b660da4a9eb5efaea65fa67fdf28c
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35312673"
---
# <a name="upgrade-master-data-services"></a>Обновление служб Master Data Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  
  Ниже приведены сценарии обновления служб Microsoft [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] Master Data Services.  
  
-   [Обновление без обновления компонента Database Engine](../../database-engine/install-windows/upgrade-master-data-services.md#noengine)  
  
-   [Обновление с обновлением компонента Database Engine](../../database-engine/install-windows/upgrade-master-data-services.md#engine)  
  
-   [Обновление при использовании двух компьютеров](../../database-engine/install-windows/upgrade-master-data-services.md#twocomputer)  
  
-   [Обновление с восстановлением базы данных из резервной копии](../../database-engine/install-windows/upgrade-master-data-services.md#restore)  
  
> [!IMPORTANT]  
> -   Не поддерживается обновление с версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP1 в версии CTP2.  
> -   Создайте резервную копию базы данных перед выполнением каких-либо обновлений.  
> -   В процессе обновления повторно создаются хранимые процедуры, а также обновляются таблицы, используемые в [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. Любая настройка какого-либо из этих компонентов может быть потеряна после обновления.  
> -   Пакеты развертывания модели можно использовать только в выпуске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в котором они были созданы. Нельзя развернуть пакеты развертывания модели, созданные в [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]или [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
> -   После обновления служб Data Quality Services и Master Data Services до версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]более ранние версии надстройки служб Master Data Services для Excel больше не будут работать. Надстройку служб Master Data Services для Excel версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] можно скачать на странице [Надстройка Master Data Services для Microsoft Excel](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md).  
  
##  <a name="fileLocation"></a> Размещение файла  
  
-   По умолчанию в [!INCLUDE[ss2017](../../includes/sssqlv14-md.md)]файлы устанавливаются в каталог *диск*:\Program Files\Microsoft SQL Server\140\Master Data Services.  

-   По умолчанию в [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] файлы устанавливаются в каталог *диск*:\Program Files\Microsoft SQL Server\130\Master Data Services.  
  
-   По умолчанию в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]файлы устанавливаются в каталог *диск*:\Program Files\Microsoft SQL Server\120\Master Data Services.  
  
-   По умолчанию в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]файлы устанавливаются в каталог *диск*:\Program Files\Microsoft SQL Server\110\Master Data Services.  
  
-   По умолчанию в [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]файлы устанавливаются в каталог *диск*:\Program Files\Microsoft SQL Server\Master Data Services.  
  
##  <a name="noengine"></a> Обновление без обновления компонента Database Engine  
 В этом случае можно продолжить использовать [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] для размещения базы данных служб MDS. Однако схему базы данных служб MDS необходимо обновить, после чего для доступа к ней необходимо будет создать текущее веб-приложение [!INCLUDE[ssNoversion](../../includes/ssnoversion-md.md)]. После обновления к базе данных служб MDS больше нельзя получить доступ с помощью предыдущего веб-приложения.  
  
 Текущую версию [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] и более раннюю версию [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] можно установить на одном компьютере. Файлы устанавливаются в разных местах, как показано в разделе [Расположение файла](#fileLocation).  
  
 **Обновление без обновления ядра СУБД**  
  
1.  Установите службы [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] и любые другие требуемые компоненты.  
  
    1.  Откройте мастер установки [!INCLUDE[ssNoversion](../../includes/ssnoversion-md.md)] .  
  
    2.  На панели слева щелкните **Установка**.  
  
    3.  На панели справа щелкните **Новая установка изолированного экземпляра SQL Server или добавление компонентов к существующей установке**.  
  
    4.  На странице **Выбор компонентов** выберите службы **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** и любые другие компоненты, которые необходимо установить.  
  
    5.  Завершите работу мастера.  
  
2.  Обновить схему базы данных MDS.  
  
    1.  Откройте текущую версию [!INCLUDE[ssNoversion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
        > [!IMPORTANT]  
        >  Чтобы обновить схему базы данных служб MDS, необходимо выполнить вход с учетной записью администратора, указанной при создании базы данных служб MDS. В базе данных служб MDS, в таблице mdm.tblUser, этот пользователь имеет свойство **ID** со значением **1**.  
  
    2.  На панели слева щелкните **Конфигурация базы данных**.  
  
    3.  На панели справа щелкните **Выбор базы данных** и укажите сведения для используемого экземпляра базы данных [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] или [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
    4.  Нажмите кнопку **Обновить базу данных** , чтобы запустить **мастер обновления баз данных**. Дополнительные сведения см. в разделе [Мастер обновления баз данных (диспетчер конфигурации служб Master Data Services)](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).  
  
3.  Создайте веб-приложение.  
  
    1.  Откройте текущую версию [!INCLUDE[ssNoversion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
    2.  На панели слева щелкните элемент **Веб-конфигурация**.  
  
    3.  На панели справа в списке **Веб-сайт** выберите один из следующих вариантов.  
  
        -   **Веб-сайт по умолчанию**и щелкните **Создать приложение**.  
  
        -   **Создать новый сайт**. При создании нового веб-сайта автоматически создается новое веб-приложение.  
  
        > [!IMPORTANT]  
        >  Существующее веб-приложение MDS из более ранней версии SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] или [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]) можно выбрать в диспетчере конфигурации Master Data Services версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Не следует выбрать существующее веб-приложение, и вместо этого следует создать веб-приложение [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] для MDS. В противном случае произойдет ошибка при попытке связать веб-приложение обновленной базы данных MDS, которые были запрашиваемая страница недоступна из-за неверной конфигурации данных для этой страницы.  
        >   
        >  Если необходимо использовать одинаковые имена (псевдонимы) для веб-приложения MDS в качестве существующего ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] или [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]), необходимо сначала удалить веб-приложение и пул приложений, связанный с IIS, а затем создать веб-приложение с тем же именем с помощью диспетчера конфигурации Master Data Services версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]. Дополнительные сведения об удалении веб-приложения и пулов приложений из служб IIS см. в разделах [Удаление приложения (IIS)](http://go.microsoft.com/fwlink/?LinkId=323537) и [Удаление пула приложений (IIS)](http://go.microsoft.com/fwlink/?LinkId=323538).  
  
4.  Свяжите новое веб-приложение с обновленной базой данных служб MDS.  
  
    1.  В разделе **Связать приложение с базой данных** щелкните **Выбрать**.  
  
    2.  Выберите базу данных служб MDS.  
  
    3.  Нажмите кнопку **Применить**.  
  
##  <a name="engine"></a> Обновление с обновлением компонента Database Engine  
 В этом сценарии выполняется обновление ядра СУБД и приложения [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] с более ранней версии до версии [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] или [!INCLUDE[ssSQL16](../../includes/sssqlv14-md.md)].  
  
 **Обновление с обновлением ядра СУБД**  
  
1.  **Только для [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]**. Откройте **панель управления** > **Программы и компоненты** и удалите Microsoft [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
2.  Обновите компонент Database Engine до [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] или [!INCLUDE[ssSQL16](../../includes/sssqlv14-md.md)]. Дополнительные сведения см. в разделе [Choose a Database Engine Upgrade Method](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md).  
  
3.  Выполните все действия, описанные в разделе [Обновление без обновления компонента Database Engine](#noengine) .  
  
##  <a name="twocomputer"></a> Обновление при использовании двух компьютеров  
 В этом сценарии выполняется обновление системы, в которой SQL Server установлен на двух компьютерах: один с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] или [!INCLUDE[ssSQL16](../../includes/sssqlv14-md.md)], а другой — с более ранней версией [!INCLUDE[ssNoversion](../../includes/ssnoversion-md.md)].  
  
 Если установлена более ранняя версия [!INCLUDE[ssNoversion](../../includes/ssnoversion-md.md)], вы продолжаете использовать более раннюю версию для размещения базы данных служб MDS на одном компьютере. Однако схему базы данных служб MDS необходимо обновить, после чего для доступа к ней необходимо будет использовать веб-приложение [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] или [!INCLUDE[ssSQL16](../../includes/sssqlv14-md.md)], соответственно. К базе данных служб MDS больше нельзя получить доступ с помощью более ранней версии веб-приложения.  
  
 **Обновление при использовании двух компьютеров**  
  
-   Выполните все действия, описанные в разделе [Обновление без обновления компонента Database Engine](#noengine).  
  
##  <a name="restore"></a> Обновление с восстановлением базы данных из резервной копии  
 В этом случае [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] или [!INCLUDE[ssSQL16](../../includes/sssqlv14-md.md)] устанавливается вместе с более ранней версией на том же компьютере или на двух разных компьютерах. Резервная копия базы данных создана в версии более ранней, чем версия [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] или [!INCLUDE[ssSQL16](../../includes/sssqlv14-md.md)], перед обновлением. Эту базу данных необходимо восстановить.  
  
 **Обновление с восстановлением базы данных из резервной копии**  
  
1.  Установите службы [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] и любые другие требуемые компоненты.  
  
    1.  Откройте мастер установки [!INCLUDE[sssnoversion](../../includes/ssnoversion-md.md)] .  
  
    2.  На панели слева щелкните **Установка**.  
  
    3.  На панели справа щелкните **Новая установка изолированного экземпляра SQL Server или добавление компонентов к существующей установке**.  
  
    4.  На странице **Выбор компонентов** выберите службы **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** и любые другие компоненты, которые необходимо установить.  
  
    5.  Завершите работу мастера.  
  
2.  Восстановите базу данных, для которой была создана резервная копия.  
  
3.  Обновите схему базы данных служб MDS, создайте веб-приложение и свяжите его с обновленной базой данных служб MDS. Инструкции см. в шагах 2–4 раздела [Обновление без обновления компонента Database Engine](#noengine).  
  
## <a name="troubleshooting"></a>Устранение неполадок  
 **Проблема**. При открытии веб-приложения [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] или [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] появляется такое сообщение об ошибке: client version is not compatible with the database version (версия клиента несовместима с версией базы данных).  
  
 **Решение**. Эта ошибка может возникнуть, когда веб-приложение диспетчера основных данных [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] или [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] пытается получить доступ к базе данных, обновленной до служб [!INCLUDE[ssSQL16](../../includes/sssqlv14-md.md)] Master Data Services. Следует использовать веб-приложение [!INCLUDE[ssSQL16](../../includes/sssqlv14-md.md)].  
  
 Она также может возникнуть, если не были выполнены останов и перезапуск **пула приложений служб MDS** в IIS при обновлении схемы базы данных служб MDS. Перезапустите **пул приложений служб MDS** , чтобы устранить проблему.  
  
## <a name="see-also"></a>См. также:  
 [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
