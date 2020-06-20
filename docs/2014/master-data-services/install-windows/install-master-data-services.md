---
title: Установка Master Data Services | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: bb7aa3e7-8807-42c8-884f-0e41d7a20837
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3fe5382fae26d01478b33c7b54c3d6f5170d34eb
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971338"
---
# <a name="install-master-data-services"></a>Установка служб Master Data Services
  В этой статье приведен обзор установки и настройки служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] устанавливается в три этапа:  
  
-   [Предварительная подготовка](#preinstall). Проверьте системные требования перед установкой [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
-   [Установка](#install). Установите [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] с помощью программы установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или командной строки.  
  
-   [Дополнительная настройка](#postinstall). Завершите настройку, используя [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] . Создайте и настройте базу данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] и веб-службу, а также разверните образец модели.  
  
##  <a name="pre-installation-tasks"></a><a name="preinstall"></a>Задачи перед установкой  
  
|Действие|Сведения|См. также|  
|------------|-------------|--------------------|  
|Проверьте требования к установке|Компьютер, на котором запускается программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должен соответствовать минимальным требованиям.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к установке;<br /><br /> Веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] и веб-службы.<br /><br /> База данных служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , если она размещается на этом же компьютере в виде веб-приложения.<br /><br /> Обратите внимание, что можно разделить компьютер веб-сервера и сервер базы данных, запустив программу установки только на компьютере веб-сервера и создав [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] базу данных на удаленном компьютере, на котором работает поддерживаемая версия и выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|[Возможности, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)<br /><br /> [Требования к аппаратному и программному обеспечению для установки SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)<br /><br /> [Требования веб-приложений (службы Master Data Services)](web-application-requirements-master-data-services.md)<br /><br /> [Требования к базе данных (службы Master Data Services)](database-requirements-master-data-services.md)|  
|Настройка необходимых ролей, служб ролей и компонентов|Перед запуском установки настройте на компьютере необходимые роли Windows, службы ролей и компоненты.<br /><br /> Этот этап можно выполнить и позже, но мы рекомендуем настроить все необходимое перед началом установки. Таким образом вы сможете приступить к веб-настройке сразу после завершения установки.|[Требования веб-приложений (службы Master Data Services)](web-application-requirements-master-data-services.md)|  
|Общие сведения о поддержке языков|Определите язык установки и пользовательского интерфейса служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .|[Многоязычное и международное развертывание (службы Master Data Services)](multi-lingual-and-global-deployments-master-data-services.md)|  
  
##  <a name="installation-operations"></a><a name="install"></a> Установка  
  
|Действие|Сведения|См. также|  
|------------|-------------|--------------------|  
|Запустите программу установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|На компьютере, на котором планируется установка веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] и веб-служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , установите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью программы установки [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]или командной строки. При использовании программы установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] службы [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] доступны на странице **Выбор компонентов** в области **Общие компоненты**. При использовании командной строки компонент [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] доступен в виде параметра компонента. Обратите внимание, что процесс установки из командной строки устанавливает [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], но не настраивает его. Его настройку необходимо выполнить с помощью диспетчера конфигурации Master Data Services. Процесс установки.<br /><br /> Установка папок и файлов служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] в расположении, указанном для общих компонентов, и назначение разрешений для них.<br /><br /> Регистрация сборок служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] в глобальном кэше сборок.<br /><br /> Устанавливает [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].|[Установка SQL Server 2014 с помощью мастера установки &#40;установки&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)<br /><br /> [Разрешения для папок и файлов (службы Master Data Services)](../folder-and-file-permissions-master-data-services.md)|  
  
##  <a name="post-installation-tasks"></a><a name="postinstall"></a>Задачи, выполняемые после установки  
  
|Действие|Сведения|См. также|  
|------------|-------------|--------------------|  
|Откройте программу [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] и выполните действия после установки.|После завершения установки откройте [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]. [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] выполняет на локальном компьютере следующие действия после установки:<br /><br /> Создание группы Windows **MDS_ServiceAccounts**, содержащей учетные записи служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] для пулов приложений.<br /><br /> Создание папки MDSTempDir в пути установки служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] и назначение разрешений для группы **MDS_ServiceAccounts**. В этой папке компилируются временные файлы для веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .<br /><br /> В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] файле Web.config настраивает `tempDirectory` атрибут **\<compilation>** элемента с помощью пути к папке MDSTempDir.<br /><br /> <br /><br /> Если процесс установки реализован в виде скрипта, то можно открыть [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] для регистрации оснастки служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], но для завершения настройки остальные действия необходимо выполнить вручную. Процесс настройки в [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] выполняется с помощью мастера. Не существует процесса командной строки для настройки [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].|[Разрешения для папок и файлов (службы Master Data Services)](../folder-and-file-permissions-master-data-services.md)<br /><br /> [Раздел "Веб-конфигурация" (службы Master Data Services)](../web-configuration-reference-master-data-services.md)|  
|Создание базы данных служб [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|С помощью [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] создайте базу данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] для хранения основных данных.|[Создание базы данных служб Master Data Services](create-a-master-data-services-database.md)|  
|Создание веб-приложения служб [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]|С помощью программы [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] создайте и настройте веб-приложение для размещения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].|[Создание веб-приложения мастера основных данных (службы Master Data Services)](create-a-master-data-manager-web-application-master-data-services.md)|  
|Свяжите базу данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] с веб-приложением|Свяжите веб-приложение [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] с базой данных [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] с помощью программы [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .|[Связывание базы данных служб Master Data Services и веб-приложения](associate-a-master-data-services-database-and-web-application.md)|  
|Настройка улучшенной безопасности в Internet Explorer|При установке [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] на компьютер под управлением ОС Windows Server 2008 или Windows Server 2008 R2 может понадобиться настроить улучшенную безопасность в Internet Explorer, чтобы разрешить использование скриптов на сайте приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]. Без этого просмотр сайта приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] в браузере на серверном компьютере работать не будет.|[Конфигурация усиленной безопасности Internet Explorer 8](https://go.microsoft.com/fwlink/p/?LinkId=223869)|  
|Установка [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]|Пользователи, которые будут работать с основными данными, могут установить [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)].|[https://go.microsoft.com/fwlink/?LinkId=219530](https://go.microsoft.com/fwlink/?LinkId=219530)|  
|Включение интеграции со службами Data Quality Services|Для пользователей [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]включите интеграцию с компонентом DQS, который можно использовать для сравнения похожих данных.|[Включение интеграции служб Data Quality Services со службами Master Data Services](enable-data-quality-services-integration-with-master-data-services.md)|  
|Развертывание образца модели|Пакеты модели образца установлены с помощью служб Master Data Services и могут быть развернуты с применением MDSModelDeploy.exe.|[Развертывание образцов MDS в SQL Server](https://go.microsoft.com/fwlink/?LinkId=251486&clcid=0x409)|  
  
 Если в процессе установки или первоначальной настройки возникли проблемы, см. раздел [Устранение неполадок во время установки и настройки](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-installation-and-configuration-issues-master-data-services.aspx) в TechNet Wiki.  
  
 Если службы [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] больше не требуются, их можно удалить [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , указав, следует ли удалять объекты, не затронутые процессом удаления Дополнительные сведения см. в статье [Удаление служб Master Data Services](../../sql-server/install/uninstall-and-remove-master-data-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Установка SQL Server 2014](../../database-engine/install-windows/install-sql-server.md)  
  
  
