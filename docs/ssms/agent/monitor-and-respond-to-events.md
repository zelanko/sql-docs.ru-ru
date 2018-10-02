---
title: Наблюдение за событиями и их обработка | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- notifications [SQL Server], alert
- events [SQL Server], alerts
- alerts [SQL Server]
- notifications [SQL Server]
- events [SQL Server], automatically responding to
- administrator notifications [SQL Server Agent]
- automatic event responses
- SQL Server Agent alerts
- monitoring [SQL Server], events
- responding to events automatically
ms.assetid: f7fbe155-5b68-4777-bc71-a47637471f32
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 47f88b65cb7ad746f3e3ab1ab7b0c7ad95de1196
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47715068"
---
# <a name="monitor-and-respond-to-events"></a>Наблюдение и обработка событий
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент производит мониторинг и автоматическую обработку различных *событий*: сообщений от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], некоторых условий производительности и событий инструментария управления Windows (WMI).  
  
## <a name="in-this-section"></a>в этом разделе  
[Предупреждения](../../ssms/agent/alerts.md)  
Содержит сведения об именовании предупреждений и о выборе событий или условий производительности, которые обрабатываются предупреждениями.  
  
[Создание пользовательского события](../../ssms/agent/create-a-user-defined-event.md)  
Содержит сведения о том, как создать событие, отличное от стандартного для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
[Операторы](../../ssms/agent/operators.md)  
Содержит сведения о создании псевдонимов для администраторов, которым агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] рассылает уведомления при успешном или неуспешном выполнении заданий.  
  
## <a name="about-monitoring-and-responding-to-events"></a>О мониторинге и обработке событий  
Автоматические отклики на события называются *предупреждениями*. Можно назначить предупреждение на одно или несколько событий, определив, каким образом должен реагировать агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на его возникновение. При обработке события предупреждение может отправить уведомление администратору, выполнить какое-либо задание, либо то и другое. Предупреждение может также переслать событие в журнал приложений Microsoft Windows на другом компьютере. Например, можно задать немедленное уведомление оператора при возникновении события с уровнем серьезности 19. Использование предупреждений позволяет администраторам базы данных более эффективно производить мониторинг и управление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент обрабатывает только те события, для которых назначены предупреждения. Метод, применяемый агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для мониторинга событий, зависит от их типа.  
  
Если предупреждение агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определено для счетчика производительности, агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] непосредственно его отслеживает. Для отслеживания событий WMI агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] регистрирует запрос события WMI.  
  
Для отслеживания сообщений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] производит мониторинг журнала приложений Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Агент может обрабатывать только те сообщения, которые появляются в этом журнале. По умолчанию SQL Server протоколирует в журнале приложений Windows следующие сообщения.  
  
-   Ошибки из таблицы sysmessages с уровнем серьезности 19 и выше.  
  
    Если необходимо протоколировать и другие ошибки из таблицы sysmessages, которые имеют уровень серьезности ниже 19, с помощью хранимой процедуры sp_altermessage можно обозначить такие ошибки как «протоколируемые всегда».  
  
-   Инструкции RAISERROR, вызываемые при использовании синтаксиса WITH LOG.  
  
    Этот способ рекомендуется для записи в журнал приложений Windows из экземпляра сервера SQL Server.  
  
-   Любые события приложения, протоколируемые при помощи процедуры xp_logevent.  
  
    > [!NOTE]  
    > Протоколирование событий приложений занимает место в журнале, в результате чего может произойти превышение его максимально допустимого размера. Чтобы предотвратить потери данных о событиях SQL Server, необходимо установить в качестве максимального размера журнала приложений Windows достаточно большое значение.  
  
После того, как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] записал сообщение в журнал, служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сравнивает его с предупреждениями, определенными администратором [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Независимо от источника события, служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обрабатывает его, выполняя задачи, заданные в предупреждении для данного события.  
  
## <a name="see-also"></a>См. также:  
[sp_altermessage](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)  
  
