---
title: Свойства предупреждения — создание предупреждения (страница "Общие") | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.alert.general.f1
ms.assetid: f5c11610-62e3-44df-9800-a5dc35be4a09
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: ce2952af8a3f75ce8cc3e7714bb0490db33febd5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65099347"
---
# <a name="alert-properties---new-alert-general-page"></a>Свойства предупреждений — новое предупреждение (страница "Общие")
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]


> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Воспользуйтесь этой страницей для просмотра и изменения общих свойств предупреждений агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  

## <a name="options"></a>Параметры  
**Название**  
Изменить имя предупреждения.  
  
**Как включить**  
Включить предупреждение. Если предупреждение не активировано, действия, указанные в предупреждении, не совершаются.  
  
**Тип**  
Выбрать тип предупреждения:  
  
-   **Предупреждение о событии SQL Server** реагирует на сообщения в журнале событий [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows.  
  
-   **Предупреждение о производительности SQL Server** реагирует на конкретные условия в счетчике производительности.  
  
-   **Предупреждение о событии WMI** реагирует на событие инструментария управления Windows.  
  
## <a name="sql-server-event-alert-options"></a>Параметры предупреждений о событиях SQL Server  
**Имя базы данных**  
Укажите базу данных для события или **Все базы данных** , чтобы реагировать на сообщение независимо от того, где происходит событие.  
  
**Номер ошибки**  
Укажите, что это событие реагирует на ошибку, и укажите номер ошибки.  
  
**Severity**  
Укажите, что это событие реагирует на любое сообщение с указанным уровнем серьезности, и укажите уровень серьезности.  
  
**Создать предупреждение, если сообщение содержит**  
Фильтровать события по указанной строке. Когда выбран этот параметр, предупреждение реагирует только на события, содержащие указанную строку.  
  
**Текст сообщения**  
Укажите строку, которую нужно использовать для фильтрации событий.  
  
## <a name="sql-server-performance-condition-alerts"></a>Предупреждения о производительности SQL Server  
**Объект**  
Укажите объект производительности для контроля.  
  
**Счетчик**  
Укажите счетчик в объекте производительности для контроля.  
  
**Экземпляр**  
Укажите экземпляр счетчика для контроля.  
  
**Создать предупреждение, если счетчик**  
Укажите поведение счетчика, на которое должно реагировать предупреждение. Например, нужно, чтобы предупреждение реагировало на условие, когда значение счетчика **Свободное пространство в tempdb (КБ)** падает ниже определенного значения, или чтобы оповещение реагировало на условие, когда число **Компиляций SQL в секунду** превышает определенное значение.  
  
**Значение**  
Укажите значение счетчика.  
  
## <a name="wmi-event-alert-options"></a>Параметры предупреждения о событии WMI  
**Пространство имен**  
Укажите пространство имен для использования в инструкции языка запросов инструментария WMI (WQL). Поддерживаются только пространства имен на компьютере, на котором запущен агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
**Запрос**  
Укажите инструкцию WQL, определяющую событие, на которое реагирует предупреждение.  
  
## <a name="see-also"></a>См. также:  
[Предупреждения](../../ssms/agent/alerts.md)  
[Использование WQL с поставщиком WMI для событий сервера](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)  
[Создание предупреждения по номеру сообщения](../../ssms/agent/create-an-alert-using-an-error-number.md)  
[Create an Alert Using Severity Level](../../ssms/agent/create-an-alert-using-severity-level.md)  
  
