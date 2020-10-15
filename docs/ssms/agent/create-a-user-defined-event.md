---
description: Создание пользовательского события
title: Создание пользовательского события
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent alerts, user-defined events
- user-defined events [SQL Server]
- multiple language support [SQL Server], alerts
- languages [SQL Server], alerts
- severity levels [SQL Server]
- global considerations [SQL Server], alerts
- events [SQL Server], user-defined
- SQL Server Agent alerts, multiple-language environments
- alerts [SQL Server], user-defined events
- alerts [SQL Server], multiple-language environments
- custom events [SQL Server Agent]
- international considerations [SQL Server], alerts
ms.assetid: 03d71a35-97fa-4bba-aa9a-23ac9c9cf879
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: bf18385b89ac7af32bfde26d704880eb4e9bb300
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036677"
---
# <a name="create-a-user-defined-event"></a>Создание пользовательского события
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Можно создать пользовательское событие, если нужно производить мониторинг событий, отличных от предопределенных системой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Можно назначить уровень серьезности для каждого пользовательского события.  
  
> [!NOTE]  
> При использовании среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]выберите параметр **Записать журнал событий приложений Windows** для каждого сообщения определяемого пользователем события, чтобы регистрировать данные сообщения. По умолчанию после возникновения определяемые пользователем сообщения с уровнем серьезности, меньшим 19, не отправляются в журнал приложений [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows. Определяемые пользователем сообщения с уровнем серьезности, меньшим 19, не приводят к возникновению предупреждения агента SQL Server.  
  
Определяемые пользователем события должны обладать уникальными номерами сообщений. Номера сообщений для определяемых пользователем событий должны превышать 50 000. Можно определить сообщения для событий на нескольких языках. Однако перед добавлением сообщений на других языках должно быть создано сообщение об ошибке **En-US** .  
  
При управлении многоязыковым окружением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо создать пользовательские сообщения на всех поддерживаемых языках. Например, если создается новое сообщение события, которое будет использоваться и на английском, и на немецком сервере, то необходимо использовать один и тот же номер сообщения и один и тот же уровень серьезности для обоих серверов, но на каждый из них назначить сообщение на соответствующем языке.  
  
В следующих задачах приводятся сведения о том, как создавать пользовательские события и реагирующие на них предупреждения.  
  
**Создание предупреждения по номеру сообщения**  
  
-   [Среда SQL Server Management Studio](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)  
  
**Создание предупреждения по уровню серьезности**  
  
-   [Среда SQL Server Management Studio](../../ssms/agent/create-an-alert-using-severity-level.md)  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)  
  
**Определение ответа на предупреждение**  
  
-   [Среда SQL Server Management Studio](../../ssms/agent/define-the-response-to-an-alert-sql-server-management-studio.md)  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)  
  
**Создание сообщения об ошибке пользовательского события**  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)  
  
**Изменение сообщения об ошибке пользовательского события**  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)  
  
**Удаление сообщения об ошибке пользовательского события**  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)  
  
**Отключение или повторное включение предупреждения**  
  
-   [Среда SQL Server Management Studio](../../ssms/agent/disable-or-reactivate-an-alert.md)  
  
-   [Transact-SQL](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
[Хранимая процедура sp_update_alert (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)  
