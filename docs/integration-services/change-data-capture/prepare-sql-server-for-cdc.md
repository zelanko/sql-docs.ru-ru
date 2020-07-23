---
title: Подготовка SQL Server для CDC | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- prepSqlSrv
ms.assetid: 20b51dbf-a545-4234-87ae-4228268a0fb2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8b17436de4950b4dcda69e4c381477640821c9a2
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86921758"
---
# <a name="prepare-sql-server-for-cdc"></a>Подготовка SQL Server для CDC

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Для службы Oracle CDC требуется, чтобы все целевые экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержали базу данных MSXDBCDC. Эта база данных создается с помощью операции «Подготовка SQL Server» в консоли конфигурации службы CDC. Операция формирует специальный скрипт, который выполняется для создания необходимых таблиц, хранимых процедур и других требуемых объектов базы данных. Эта задача выполняется только один раз для каждого целевого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Дополнительные сведения о базе данных MSXDBCDC см. в разделе «База данных MSXDBCDC».  
  
 В консоли конфигурации службы CDC щелкните **Подготовка SQL Server**. Если эта команда недоступна, проверьте, выбран ли элемент **Локальные службы CDC** на левой панели консоли.  
  
## <a name="options"></a>Параметры  
  
### <a name="server-name"></a>Имя сервера  
 Введите имя сервера, на котором находится экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="authentication"></a>Аутентификация  
 Выберите один из следующих вариантов:  
  
-   **Проверка подлинности Windows.**  
  
-   **Аутентификация SQL Server**: если вы выберете этот вариант, необходимо будет ввести **Имя пользователя** и **Пароль** в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], к которому вы подключаетесь.  
  
 Для подготовки экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для Oracle CDC имя входа должно иметь разрешение на запись в базе данных MSXDBCDC. Введите учетные данные для имени входа, имеющего разрешение на запись в базу данных MSXDBCDC. Это может быть член роли `sysasmin` .  
  
### <a name="options"></a>Параметры  
 Чтобы просмотреть доступные для настройки параметры, щелкните стрелку. Для них можно оставить значения по умолчанию. Доступные параметры:  
  
-   **Время ожидания соединения**: Введите время (в секундах), в течение которого служба CDC для Oracle ожидает установления соединения с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Значение по умолчанию ― **15**.  
  
-   **Время ожидания выполнения**: Введите время (в секундах), в течение которого служба Windows CDC Oracle ожидает выполнения команды. Значение по умолчанию — **30**.  
  
-   **Шифровать соединение**: выберите параметр **Шифровать соединение**, чтобы обмен данными между службой Oracle CDC Service и целевым экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнялся по зашифрованному соединению.  
  
-   **Дополнительно**: При необходимости введите любые дополнительные свойства подключения.  
  
### <a name="view-script"></a>Просмотреть скрипт  
 Щелкните **Просмотреть скрипт** для просмотра скрипта установки (он будет доступен только для чтения). Системный администратор [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при необходимости может скопировать этот скрипт в консоль управления SQL Server и отредактировать его. Дополнительные сведения о подготовке скрипта SQL Server см. в разделе [Подготовка SQL Server для скрипта представления CDC Oracle](../../integration-services/change-data-capture/prepare-sql-server-for-oracle-cdc-view-script.md).  
  
## <a name="see-also"></a>См. также:  
 [Как работать со службами CDC](../../integration-services/change-data-capture/how-to-work-with-cdc-services.md)   
 [Как подготовить SQL Server для CDC](../../integration-services/change-data-capture/how-to-prepare-sql-server-for-cdc.md)  
  
  
