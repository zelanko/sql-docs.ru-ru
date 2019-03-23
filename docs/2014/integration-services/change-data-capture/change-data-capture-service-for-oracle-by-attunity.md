---
title: Служба системы отслеживания измененных данных для Oracle компании Attunity | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 22ec8a5c-9550-4d38-8a4a-485ec3e53ea8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a01524acf4fc72cb50732650f1f2e6f58b4ff74d
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58388340"
---
# <a name="change-data-capture-service-for-oracle-by-attunity"></a>Служба системы отслеживания измененных данных для Oracle компании Attunity
  Служба CDC Service для Oracle ― это служба Windows, которая просматривает журналы транзакций Oracle и регистрирует изменения выбранных таблиц Oracle в таблицах изменений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Таблицы изменений SQL, где хранятся отслеженные изменения из базы данных Oracle, принадлежат к тому же типу, что и таблицы изменений, используемые в собственной системе отслеживания изменений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Поэтому использовать эти изменения так же легко, как и изменения баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="installation"></a>Установка  
 Службу CDC Service для Oracle можно установить на любой поддерживаемый компьютер с ОС Windows с доступом к исходным базам данных Oracle, изменения в которых отслеживаются, и к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , где находится целевая база данных CDC. Службе CDC Service не нужны локально установленные базы данных Oracle или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а только их поддерживаемые клиенты. Сведения о месте установки необходимых компонентов базы данных см. в подразделе **Предварительные требования базы данных** в этом разделе.  
  
 Установка службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC Service для Oracle помещает в выбранном месте графический интерфейс пользователя для настройки службы и служебную программу. Служба CDC Service для Oracle настраивается отдельно с помощью консоли конфигурации службы Oracle CDC. Дополнительные сведения о настройке службы Oracle CDC Service см. в разделе [Change Data Capture Service for Oracle by Attunity F1 Help](change-data-capture-service-for-oracle-by-attunity-f1-help.md).  
  
 Чтобы установить службу CDC Service для Oracle, вручную запустите файл **AttunityOracleCdcDesigner.msi** с установочного носителя SQL Server. Установочные пакеты для x86 и x64 расположены в **.\Tools\AttunityCDCOracle\\**  на установочном носителе SQL Server.  
  
 Службу CDC Service для Oracle можно установить на любой поддерживаемый компьютер с ОС Windows, на котором установлен собственный клиент Native Client [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ; он не обязательно должен быть установлен на том же компьютере, что и целевая база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="supported-windows-environments"></a>Поддерживаемые среды Windows  
 Служба системы отслеживания измененных данных для Oracle от Attunity может работать в следующих средах Windows:  
  
-   Windows 8  
  
-   Windows 7, 32-разрядная (x86) и 64-разрядная (x64) версии  
  
-   Windows Server 2012  
  
-   Windows Server 2008 R2 с пакетом обновления 1 (SP1)  
  
-   Windows Server 2008, 32-разрядная (x86) и 64-разрядная (x64) версии с пакетом обновления 2 (SP2)  
  
## <a name="database-prerequisites"></a>Предварительные требования базы данных  
 Для работы со службой CDC Service для Oracle следует установить программное обеспечения собственного клиента Native Client Oracle [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Это обязательный компонент, который нужно получить у Oracle и установить до установки службы Oracle CDC Service. Кроме того, необходимо установить клиент ODBC для SQL Server, используя процесс установки SQL Server.  
  
 Служба CDC для Oracle поддерживает следующие версии:  
  
### <a name="source-oracle-database"></a>Исходная база данных Oracle  
  
-   База данных Oracle 11x, любая версия  
  
-   База данных Oracle 10x, любая версия  
  
### <a name="target-sql-server-database"></a>Целевая база данных SQL Server  
 Перечень функций, поддерживаемых в разных выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="running-the-installation-program"></a>Запуск программы установки  
 Чтобы установить службу CDC Service для Oracle, откройте мастер установки для используемой платформы Windows (32-/64-разрядной) и следуйте инструкциям на экране.  
  
## <a name="uninstalling-change-data-capture-service-for-oracle-by-attunity"></a>Удаление службы системы отслеживания измененных данных для Oracle от Attunity  
 Служба CDC Service для Oracle удаляется с помощью пункта панели управления «Программы и компоненты».  
  
 При удалении службы CDC Service созданные базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удаляются. Для полного удаления этого средства нужно удалить базу данных MSXDBCDC и конкретные базы данных CDC, созданные в целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , с которым производилась работа.  
  
 Если программное обеспечение службы CDC Service удаляется с одного компьютера и устанавливается на другой, нужно задать только следующие данные:  
  
-   Учетная запись службы  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и учетные данные  
  
-   Главный пароль  
  
 Все прочие определения хранятся в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и доступны из предыдущей установки на другом компьютере.  
  
## <a name="in-this-documentation"></a>В этой документации  
  
-   [Архитектура службы системы отслеживания измененных данных для Oracle компании Attunity](change-data-capture-service-for-oracle-by-attunity-system-architecture.md)  
  
-   [Служба CDC Oracle](the-oracle-cdc-service.md)  
  
-   [Справка F1 по службе системы отслеживания информации об изменениях данных для Oracle компании Attunity](change-data-capture-service-for-oracle-by-attunity-f1-help.md)  
  
-   [Руководство по службе системы отслеживания измененных данных для Oracle компании Attunity](change-data-capture-service-for-oracle-by-attunity-how-to-guide.md)  
  
## <a name="see-also"></a>См. также:  
 [Работа со службой CDC Oracle](working-with-the-oracle-cdc-service.md)  
  
  
