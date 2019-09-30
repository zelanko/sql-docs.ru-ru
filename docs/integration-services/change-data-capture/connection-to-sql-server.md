---
title: Соединение с SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5bb582f9-68d3-4c1e-ab02-6fc16807f1a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e87e29349cdef9db94e917f6fe543b327c5abf9f
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71298857"
---
# <a name="connection-to-sql-server"></a>Соединение с SQL Server

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Если имя входа, не имеющее роли с правами записи в базе данных MSXDBCDC (например, **db_owner**), пытается создать экземпляр Oracle CDC, появляется диалоговое окно "Подключение к SQL Server".  
  
 Чтобы создать новый экземпляр Oracle CDC, нужно ввести в этом окне учетные данные имени входа, имеющего права записи в базу данных MSXDBCDC, например члена роли базы данных **db_owner** .  
  
 В диалоговом окне «Подключение к SQL Server» введите следующие данные.  
  
### <a name="server-name"></a>Имя сервера  
 Введите имя сервера, на котором находится экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="authentication"></a>Проверка подлинности  
 Выберите один из следующих вариантов:  
  
-   Проверка подлинности Windows.  
  
-   **Аутентификация SQL Server**: если вы выберете этот вариант, необходимо будет ввести **Имя для входа** и **Пароль** в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], к которому вы подключаетесь.  
  
### <a name="options"></a>Параметры  
 Чтобы просмотреть доступные для настройки параметры, щелкните стрелку. Для них можно оставить значения по умолчанию. Доступные параметры:  
  
-   **Время ожидания соединения**: введите время (в секундах), в течение которого программа ожидает установления соединения с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], прежде чем выдать ошибку, связанную с истечением времени ожидания. Значение по умолчанию ― **15**.  
  
-   **Время ожидания выполнения**: введите время (в секундах), в течение которого программа ожидает выполнения команды SQL, прежде чем выдать ошибку, связанную с истечением времени ожидания. Значение по умолчанию — **30**.  
  
-   **Шифровать соединение**: выберите **Шифровать соединение**, чтобы при установке подключения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использовалось шифрование для обеспечения конфиденциальности.  
  
-   **Дополнительно**: Нажмите кнопку **Дополнительно** и при необходимости введите любые дополнительные свойства подключения в диалоговом окне "Дополнительные свойства подключения".  
  
## <a name="see-also"></a>См. также:  
 [Разрешения, необходимые службе CDC для соединения с SQL Server](../../integration-services/change-data-capture/sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
