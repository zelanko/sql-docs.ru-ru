---
title: Установка и удаление служб Master Data Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: efc2431c-588b-42e7-b23b-c875145a33f6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e9bac4dba698af6e7f3dc57904da66a7fb15a08b
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53365726"
---
# <a name="uninstall-and-remove-master-data-services"></a>Удаление служб Master Data Services
  Чтобы удалить компонент [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] из экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполните действия из раздела [Удаление существующего экземпляра SQL Server (программа установки)](../../../2014/sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) и укажите [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] в качестве компонента для удаления на странице **Выбор компонентов**. В процессе удаления удаляются файлы и папки [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], а также удаляется [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] на локальном компьютере.  
  
 Чтобы избежать потери данных или нарушения работы других компьютеров в системе, некоторые компоненты при удалении не удаляются или не изменяются. Чтобы определить, следует ли оставить или удалить элементы, просмотрите следующую таблицу.  
  
|Элемент|Описание|  
|----------|-----------------|  
|Файлы и папки|В процессе удаления удаляется большинство файлов и папок, расположенных в пути установки.<br /><br /> В процессе удаления в пути установки не удаляются папки Master Data Services и MDSTempDir. После завершения процесса удаления эти папки можно удалить из файловой системы вручную. Дополнительные сведения см. в разделе [Разрешения для папок и файлов (службы Master Data Services)](../../master-data-services/folder-and-file-permissions-master-data-services.md).|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] сборки|Процесс удаления удаляет сборки [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] из глобального кэша сборок (GAC).|  
|База данных|Процесс удаления не затрагивает базу данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . База данных на экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] остается неизменной, поэтому все данные, включая основные данные, объекты моделей, разрешения пользователей и групп, бизнес-правила и т. п., сохраняются.<br /><br /> Если база данных больше не нужна и не предвидится ее соединение с другим веб-сайтом или приложением [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] в будущем, можно удалить базу данных на экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , на котором она размещена. Дополнительные сведения см. в разделе [Удаление базы данных](../../relational-databases/databases/delete-a-database.md).|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] и Web.config|В процессе удаления в файловой системе удаляется папка WebApplication. Папка WebApplication содержит файлы веб-приложения и файл Web.config, используемые [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].<br /><br /> **\*\* Важно! \*\*** Перед удалением можно скопировать файл Web.config в другое расположение, чтобы сохранить любые пользовательские настройки или другие содержащиеся в файле сведения. После завершения процесса удаления восстановить файл Web.config невозможно.|  
|Элементы служб Internet Information Services (IIS)|Процесс удаления не затрагивает пулы приложений, веб-сайты и веб-приложения в IIS на локальном компьютере. Так как процесс удаления удаляет папку WebApplication и файл Web.config для [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], любые веб-приложения [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , которым требуются эти файлы, прекратят работу. Если пользователи пытаются получить доступ к веб-приложения, он получит сообщение об ошибке HTTP 500.19: Внутренняя ошибка сервера: «Запрашиваемая страница недоступна из-за неверной конфигурации данных для этой страницы».<br /><br /> Если веб-сайт или приложение больше не нужны, а сайт или приложение предоставляются пулом приложений, для их удаления можно воспользоваться средствами IIS. Дополнительные сведения см. в [Руководстве по использованию IIS 7](https://go.microsoft.com/fwlink/?LinkId=184885) на сайте [!INCLUDE[msCoName](../../includes/msconame-md.md)] TechNet.|  
|Группа**MDS_ServiceAccounts** |После завершения процесса удаления группа Windows **MDS_ServiceAccounts** и любые добавленные в нее учетные записи служб сохраняются. Если эта группа и учетные записи больше не нужны, можно удалить их.|  
|Реестр|В процессе удаления из реестра Windows удаляются все разделы, связанные со службами [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .|  
  
## <a name="see-also"></a>См. также  
 [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
