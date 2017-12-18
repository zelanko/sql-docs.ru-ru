---
title: "Соединение с SQL Server | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5bb582f9-68d3-4c1e-ab02-6fc16807f1a5
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ec5be00d83b0630754456bc3cde7a20678959496
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="connection-to-sql-server"></a>Соединение с SQL Server
  Если имя входа, не имеющее роли с правами записи в базе данных MSXDBCDC (например, **db_owner** ), пытается создать экземпляр Oracle CDC, появляется диалоговое окно "Подключение к SQL Server".  
  
 Чтобы создать новый экземпляр Oracle CDC, нужно ввести в этом окне учетные данные имени входа, имеющего права записи в базу данных MSXDBCDC, например члена роли базы данных **db_owner** .  
  
 В диалоговом окне «Подключение к SQL Server» введите следующие данные.  
  
### <a name="server-name"></a>Имя сервера  
 Введите имя сервера, на котором находится экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="authentication"></a>Проверка подлинности  
 Выберите один из следующих вариантов:  
  
-   Проверка подлинности Windows.  
  
-   **Проверка подлинности SQL Server**. При выборе этого варианта необходимо ввести **Имя** и **Пароль** для пользователя в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , с которым устанавливается соединение.  
  
### <a name="options"></a>Параметры  
 Чтобы просмотреть доступные для настройки параметры, щелкните стрелку. Для них можно оставить значения по умолчанию. Доступные параметры:  
  
-   **Время ожидания подключения**: введите время (в секундах), в течение которого программа ожидает подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , прежде чем выдать ошибку времени ожидания. Значение по умолчанию ― **15**.  
  
-   **Время ожидания выполнения**: введите время (в секундах), в течение которого программа ожидает выполнения команды SQL, прежде чем выдать ошибку времени ожидания. Значение по умолчанию — **30**.  
  
-   **Шифрование подключения**: выберите **Шифрование подключения** , чтобы устанавливаемое подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] шифровалось для обеспечения конфиденциальности.  
  
-   **Дополнительно**: нажмите кнопку **Дополнительно** и при необходимости введите любые дополнительные свойства подключения в диалоговом окне "Дополнительные свойства подключения".  
  
## <a name="see-also"></a>См. также раздел  
 [Разрешения, необходимые службе CDC для соединения с SQL Server](../../integration-services/change-data-capture/sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
