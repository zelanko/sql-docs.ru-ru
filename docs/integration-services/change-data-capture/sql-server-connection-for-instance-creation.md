---
description: Соединение с SQL Server для создания экземпляров
title: Соединение с SQL Server для создания экземпляров | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 81d0e7e2-d8f0-4bd9-9565-218ce996f28e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e1b856327d3e249cd58efe6ccad732f70f900a50
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "88457642"
---
# <a name="sql-server-connection-for-instance-creation"></a>Соединение с SQL Server для создания экземпляров

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Одним из первых шагов при создании экземпляра CDC Oracle является создание базы данных CDC на целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Эта база данных CDC должна быть подготовлена к работе CDC SQL Server, для чего требуется имя входа, которое является членом предопределенной роли сервера `sysadmin` .  
  
 Если пользователь, запускающий мастер **создания экземпляра Oracle CDC** , не является членом предопределенной роли сервера `sysadmin` , то открывается диалоговое окно **Соединение с SQL Server** , где необходимо ввести учетные данные члена роли `sysadmin` , чтобы обеспечить подготовку базы данных задачей CDC SQL Server. При создании базы данных CDC имя входа `sysadmin` удаляется, а работа возобновляется с первоначальным именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которое использовалось для входа в консоль конструктора Oracle.  
  
## <a name="task-list"></a>Список задач  
 В диалоговом окне **Соединение с SQL Server** введите следующие данные.  
  
 **Имя сервера**  
 Введите имя сервера, на котором находится экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Аутентификация**  
 Выберите один из следующих вариантов:  
  
-   **Проверка подлинности Windows**  
  
-   **Проверка подлинности SQL Server**. При выборе этого варианта необходимо ввести **Имя** и **Пароль** для пользователя в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , с которым устанавливается соединение.  
  
 Имя входа должно иметь роль базы данных, которая обеспечивает доступ к базе данных MSXCDCDB. Рекомендуется, чтобы имя входа также имело доступ ко всем другим используемым базам данных. В противном случае пользователь не сможет просматривать данные из этих баз данных.  
  
 **Параметры**  
 Чтобы просмотреть доступные для настройки параметры, щелкните стрелку. Для них можно оставить значения по умолчанию. Доступные параметры:  
  
-   **Время ожидания соединения**: Введите время (в секундах), в течение которого служба CDC для Oracle ожидает установления соединения с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Значение по умолчанию ― **15**.  
  
-   **Время ожидания выполнения**: Введите время (в секундах), в течение которого служба Windows CDC Oracle ожидает выполнения команды. Значение по умолчанию — **30**.  
  
-   **Шифрование соединения**. Выберите параметр **Шифровать соединение** , чтобы обмен данными между службой Oracle CDC Service и целевым экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнялся по зашифрованному соединению.  
  
-   **Дополнительно**: Нажмите кнопку **Дополнительно** и при необходимости введите любые дополнительные свойства подключения в диалоговом окне "Дополнительные свойства подключения".  
  
     Дополнительные сведения о диалоговом окне «Дополнительные свойства подключения» см. в разделе [Advanced Connection Properties](../../integration-services/change-data-capture/advanced-connection-properties.md).  
  
## <a name="see-also"></a>См. также  
 [Создание базы данных изменения SQL Server](../../integration-services/change-data-capture/create-the-sql-server-change-database.md)   
 [Разрешения, необходимые конструктору CDC для соединения с SQL Server](../../integration-services/change-data-capture/sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
