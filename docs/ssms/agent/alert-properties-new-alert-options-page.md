---
title: Свойства предупреждения — создание предупреждения (страница "Параметры") | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.ag.alert.options.f1
ms.assetid: 6e4f41aa-832d-46ba-b6b5-cf1d3b15d33f
caps.latest.revision: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0f86a156d1e7f659e5460d92d80454eb34a4644a
ms.sourcegitcommit: 34766933e3832ca36181641db4493a0d2f4d05c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="alert-properties---new-alert-options-page"></a>Свойства предупреждения — создание предупреждения (страница "Параметры")
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Используйте эту страницу, чтобы просмотреть и изменить параметры предупреждений агента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  

## <a name="options"></a>Параметры  
**Электронная почта**  
Включает текст сообщения об ошибке от события, при наличии таковой, в уведомления, доставляемые по электронной почте.  
  
**Пейджер**  
Включает текст сообщения об ошибке от события, при наличии таковой, в уведомления, доставляемые на пейджер.  
  
**Команда Net send**  
Включает текст сообщения об ошибке от события, при наличии таковой, в уведомления, доставляемые службой net send.  
  
**Дополнительное сообщение уведомления**  
Введите любой дополнительный текст для включения в уведомления.  
  
**Задержка между ответами**  
Укажите время задержки между повторными наступлениями события. Некоторые события могут происходить часто в течение короткого периода времени. В таком случае, вероятно, необходимо будет узнать о наступлении события, но не обязательно, чтобы для каждого события выдавался ответ. Используйте этот параметр для указания лимита времени ожидания. При наличии задержки после того, как предупреждение отвечает на событие, агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] выжидает в течение указанного времени задержки прежде, чем ответить снова, независимо от того, происходит ли событие во время ожидания.  
  
**Минуты**  
Укажите задержку в минутах. Для ответа при каждом наступлении события укажите 0 минут и 0 секунд.  
  
**Секунды**  
Укажите задержку в секундах. Для ответа при каждом наступлении события укажите 0 минут и 0 секунд.  
  
## <a name="see-also"></a>См. также:  
[Предупреждения](../../ssms/agent/alerts.md)  
  
