---
title: Соединение с SQL Server для удаления | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 030b10c2-6b88-4c2c-bf67-22994be25a60
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 997f0cf8793b0a809db39abd2b8d484529151950
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65728949"
---
# <a name="connection-to-sql-server-for-delete"></a>Соединение с SQL Server для удаления

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Если имя входа, не имеющее роли с разрешением на запись в базе данных MSXDBCDC (например, **db_owner**), пытается удалить экземпляр Oracle CDC, открывается диалоговое окно "Подключение к SQL Server".  
  
 Чтобы удалить экземпляр Oracle CDC, нужно ввести в это окно учетные данные имени входа, имеющего разрешение на запись в базу данных MSXDBCDC, например учетные данные члена роли базы данных **db_owner** .  
  
 В диалоговом окне «Подключение к SQL Server» введите следующие данные.  
  
 **Имя сервера**  
 Введите имя сервера, на котором находится экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Проверка подлинности**  
 Выберите один из следующих вариантов:  
  
-   **Проверка подлинности Windows.**  
  
-   **Аутентификация SQL Server**: если вы выберете этот вариант, необходимо будет ввести **имя для входа** и **пароль** в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], к которому вы подключаетесь.  
  
 **Параметры**  
 Чтобы просмотреть доступные для настройки параметры, щелкните стрелку. Для них можно оставить значения по умолчанию. Доступные параметры:  
  
-   **Время ожидания соединения**: введите время (в секундах), в течение которого программа ожидает установления соединения с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], прежде чем выдать ошибку, связанную с истечением времени ожидания. Значение по умолчанию ― **15**.  
  
-   **Время ожидания выполнения**: введите время (в секундах), в течение которого программа ожидает выполнения команды SQL, прежде чем выдать ошибку, связанную с истечением времени ожидания. Значение по умолчанию — **30**.  
  
-   **Шифровать соединение**: выберите **Шифровать соединение**, чтобы при установке подключения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использовалось шифрование для обеспечения конфиденциальности.  
  
-   **Дополнительно**: Нажмите кнопку **Дополнительно** и при необходимости введите любые дополнительные свойства подключения в диалоговом окне "Дополнительные свойства подключения".  
  
## <a name="see-also"></a>См. также:  
 [Разрешения, необходимые службе CDC для соединения с SQL Server](../../integration-services/change-data-capture/sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
