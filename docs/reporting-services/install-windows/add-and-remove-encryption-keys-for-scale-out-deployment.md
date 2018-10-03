---
title: Добавление и удаление ключей шифрования для масштабного развертывания | Документы Майкрософт
ms.date: 05/31/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- encryption keys [Reporting Services]
- deleting encryption keys
- removing encryption keys
- adding encryption keys
- rskeymgmt utility
- scale-out deployments [Reporting Services]
ms.assetid: 2da86fb3-4b4d-407f-9825-74dcc42486f5
author: markingmyname
ms.author: maghan
ms.openlocfilehash: be584371ef8cb2e1f8594ee9156ea05b7aee85fd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47695952"
---
# <a name="add-and-remove-encryption-keys-for-scale-out-deployment"></a>Добавление и удаление ключей шифрования для масштабного развертывания
  Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] могут работать в модели масштабного развертывания, где несколько серверов отчетов настроены на использование общей базы данных. Членство в масштабном развертывании основано на том, хранит ли сервер отчетов ключ шифрования в базе данных сервера отчетов. Этим членством можно управлять за счет добавления и удаления ключей шифрования для конкретных экземпляров серверов отчетов. При удалении узлов из конфигурации развертывания их можно удалять в любом порядке. Если добавляются узлы к конфигурации, необходимо подключать все новые экземпляры с сервера отчетов, который уже входит в конфигурацию.  
  
## <a name="using-the-reporting-services-configuration-tool-to-configure-scale-out-deployment"></a>Использование программы настройки служб Reporting Services для масштабного развертывания  
 Наиболее простым способом настройки масштабного развертывания является применение программы настройки служб Reporting Services. Дополнительные сведения и пошаговые инструкции см. в разделе [Настройка масштабного развертывания сервера отчетов в собственном режиме (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md).  
  
## <a name="using-rskeymgmt-to-configure-scale-out-deployment"></a>Использование Rskeymgmt для настройки масштабного развертывания  
 Программа **rskeymgmt** служит для инициализации использования экземпляром сервера отчетов общей базы данных сервера отчетов. Добавление сервера отчетов в масштабное развертывание требует инициализации сервера отчетов. Инициализация требует административных разрешений. Необходимо иметь права администратора для удаленного компьютера, на котором размещается сервер отчетов, присоединяемый к развертыванию.  
  
### <a name="how-to-join-a-report-server-to-a-scale-out-deployment-rskeymgmt"></a>Как присоединить сервер отчетов к масштабному развертыванию (rskeymgmt)  
  
1.  Запустите программу **rskeymgmt.exe** локально на компьютере, где размещается сервер отчетов, уже являющийся членом масштабного развертывания сервера отчетов.  
  
2.  С помощью аргумента **-j** присоедините сервер отчетов к базе данных сервера отчетов. Используйте аргументы **-m** и **-n** для указания экземпляра удаленного сервера отчетов, который необходимо добавить к конфигурации развертывания. Используйте аргументы **-u** и **-v** для указания учетной записи администратора на удаленном компьютере. При создании масштабного развертывания, содержащего несколько экземпляров сервера отчетов на том же компьютере, синтаксис будет немного другим. Дополнительные сведения о синтаксисе, который следует использовать в этом случае, см. в разделе [Программа rskeymgmt (SSRS)](../../reporting-services/tools/rskeymgmt-utility-ssrs.md).  
  
     Следующий пример иллюстрирует аргументы, которые необходимо указать при присоединении удаленного сервера отчетов к масштабному развертыванию (можно опустить учетные данные, если на удаленном компьютере имеются разрешения администратора):  
  
    ```  
    rskeymgmt -j -m <remotecomputer> -n <namedreportserverinstance> -u <administratoraccount> -v <administratorpassword>  
    ```
3. Перезапустите службу Windows Reporting Services.
  
### <a name="how-to-remove-a-report-server-from-a-scale-out-deployment-rskeymgmt"></a>Как исключить сервер отчетов из масштабного развертывания (rskeymgmt)  
  
1.  Откройте файл сервера отчетов rsperportserver.config, который необходимо удалить, и найдите идентификатор установки. По умолчанию этот файл находится в папке Program Files\Microsoft SQL Server\MSSQL.*n*\Reporting Services\ReportServer).  
  
     Если установлен всего один экземпляр, на компьютере будет находиться один файл rsreportserver.config. Если установлено несколько экземпляров служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , то на странице «Состояние сервера» программы настройки служб Reporting Services выполните поиск идентификатора экземпляра сервера отчетов (например, «MSSQL.2»), который необходимо удалить. Имя папки, в которой хранятся программные файлы экземпляра сервера отчетов, содержит идентификатор экземпляра (например: Program Files\Microsoft SQL Server\MSSQL.2).  
  
2.  Запустите программу **rskeymgmt.exe**. Ее можно запускать только на сервере отчетов, который входит в масштабное развертывание сервера отчетов.  
  
3.  Используйте аргумент **-r** для исключения экземпляра сервера отчетов из масштабного развертывания. Аргументы, которые необходимо задать, приведены в следующем примере.  
  
    ```  
    rskeymgmt -r <installation ID>  
    ```  
4. Перезапустите службу Windows Reporting Services.
  
 Данные шаги удаляют сервер отчетов из масштабного развертывания, однако удаления экземпляра служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] на сервере отчетов не производится. После того как сервер отчетов будет удален из масштабного развертывания, службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно удалить с сервера (если службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] более не нужны). Сведения см. в разделе [Удаление существующего экземпляра SQL Server (программа установки)](../../sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Настройка ключей шифрования и управление ими (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md)   
 [Инициализация сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)  
  
  
