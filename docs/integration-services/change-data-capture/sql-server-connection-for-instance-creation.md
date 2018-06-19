---
title: Соединение с SQL Server для создания экземпляров | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 81d0e7e2-d8f0-4bd9-9565-218ce996f28e
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 116c18105f4969cf92d5a2af3751875ec32cd515
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35401486"
---
# <a name="sql-server-connection-for-instance-creation"></a>Соединение с SQL Server для создания экземпляров
  Одним из первых шагов при создании экземпляра CDC Oracle является создание базы данных CDC на целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Эта база данных CDC должна быть подготовлена к работе CDC SQL Server, для чего требуется имя входа, которое является членом предопределенной роли сервера `sysadmin` .  
  
 Если пользователь, запускающий мастер **создания экземпляра Oracle CDC** , не является членом предопределенной роли сервера `sysadmin` , то открывается диалоговое окно **Соединение с SQL Server** , где необходимо ввести учетные данные члена роли `sysadmin` , чтобы обеспечить подготовку базы данных задачей CDC SQL Server. При создании базы данных CDC имя входа `sysadmin` удаляется, а работа возобновляется с первоначальным именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которое использовалось для входа в консоль конструктора Oracle.  
  
## <a name="task-list"></a>Список задач  
 В диалоговом окне **Соединение с SQL Server** введите следующие данные.  
  
 **Имя сервера**  
 Введите имя сервера, на котором находится экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Проверка подлинности**  
 Выберите один из следующих вариантов:  
  
-   **Проверка подлинности Windows.**  
  
-   **Проверка подлинности SQL Server**. При выборе этого варианта необходимо ввести **Имя** и **Пароль** для пользователя в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , с которым устанавливается соединение.  
  
 Имя входа должно иметь роль базы данных, которая обеспечивает доступ к базе данных MSXCDCDB. Рекомендуется, чтобы имя входа также имело доступ ко всем другим используемым базам данных. В противном случае пользователь не сможет просматривать данные из этих баз данных.  
  
 **Параметры**  
 Чтобы просмотреть доступные для настройки параметры, щелкните стрелку. Для них можно оставить значения по умолчанию. Доступные параметры:  
  
-   **Время ожидания соединения**. Введите время (в секундах), в течение которого служба CDC для Oracle ожидает соединения с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Значение по умолчанию ― **15**.  
  
-   **Время ожидания выполнения**. Введите время (в секундах), в течение которого служба Windows CDC Oracle ожидает выполнения команды. Значение по умолчанию — **30**.  
  
-   **Шифрование соединения**. Выберите параметр **Шифровать соединение** , чтобы обмен данными между службой Oracle CDC Service и целевым экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполнялся по зашифрованному соединению.  
  
-   **Дополнительно**: нажмите кнопку **Дополнительно** и при необходимости введите любые дополнительные свойства подключения в диалоговом окне "Дополнительные свойства подключения".  
  
     Дополнительные сведения о диалоговом окне «Дополнительные свойства подключения» см. в разделе [Advanced Connection Properties](../../integration-services/change-data-capture/advanced-connection-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Создание базы данных изменения SQL Server](../../integration-services/change-data-capture/create-the-sql-server-change-database.md)   
 [Разрешения, необходимые конструктору CDC для соединения с SQL Server](../../integration-services/change-data-capture/sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
