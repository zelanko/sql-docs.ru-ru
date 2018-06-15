---
title: Свойства предупреждения — создание предупреждения (страница "Общие") | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ag.alert.general.f1
ms.assetid: f5c11610-62e3-44df-9800-a5dc35be4a09
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 2f2779c1ff64995e0ff9d23ae8f8c2768debd6d6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33040791"
---
# <a name="alert-properties---new-alert-general-page"></a>Свойства предупреждений — новое предупреждение (страница "Общие")
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]


> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Воспользуйтесь этой страницей для просмотра и изменения общих свойств предупреждений агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  

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
  
**Value**  
Укажите значение счетчика.  
  
## <a name="wmi-event-alert-options"></a>Параметры предупреждения о событии WMI  
**Пространство имен**  
Укажите пространство имен для использования в инструкции языка запросов инструментария WMI (WQL). Поддерживаются только пространства имен на компьютере, на котором запущен агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Запрос**  
Укажите инструкцию WQL, определяющую событие, на которое реагирует предупреждение.  
  
## <a name="see-also"></a>См. также:  
[Предупреждения](../../ssms/agent/alerts.md)  
[Использование WQL с поставщиком WMI для событий сервера](http://msdn.microsoft.com/en-us/58b67426-1e66-4445-8e2c-03182e94c4be)  
[Создание предупреждения по номеру сообщения](../../ssms/agent/create-an-alert-using-an-error-number.md)  
[Create an Alert Using Severity Level](../../ssms/agent/create-an-alert-using-severity-level.md)  
  
