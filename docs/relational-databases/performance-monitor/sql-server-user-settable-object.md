---
title: SQL Server, объект User Settable | Документация Майкрософт
description: Сведения об объекте "Настраивается пользователем", который создает пользовательские экземпляры счетчиков в SQL Server для контроля тех аспектов сервера, которые не отслеживаются существующими счетчиками.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- User Settable object
- SQLServer:User Settable
ms.assetid: 633de3ef-533c-4f0c-9c7b-c105129d8e94
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 980a7161eba7cc40da6de3f2c4172df7e2349c78
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505572"
---
# <a name="sql-server-user-settable-object"></a>SQL Server, объект User Settable
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В Microsoft **объект** User Settable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет создавать пользовательские экземпляры счетчиков, которые используются для контроля тех характеристик сервера, которые нельзя отследить при использовании существующих счетчиков, какими являются, например компоненты, уникальные для вашей базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : число зарегистрированных заказов или опись продукции.  
  
 В объекте **User Settable** содержится 10 экземпляров счетчиков запросов: с **User counter 1** по **User counter 10**. Этим счетчикам соответствуют хранимые процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] от **sp_user_counter1** до **sp_user_counter10**. Поскольку эти хранимые процедуры выполняются пользовательскими приложениями, значения, получаемые в результате выполнения хранимых процедур, отображаются в системном мониторе. Счетчик может контролировать любое целочисленное значение (например, хранимая процедура может подсчитывать, сколько заказов конкретного продукта было совершено за один день).  
  
> [!NOTE]  
>  Хранимые процедуры пользовательских счетчиков системным монитором автоматически не опрашиваются. Чтобы значения счетчика обновлялись, эти процедуры должны явным образом вызываться пользовательским приложением. Для автоматического обновления значений счетчиков используйте триггеры. Например, для создания счетчика, который отслеживает число строк в таблице, создайте для этой таблицы триггер INSERT и DELETE, выполняющий следующую инструкцию: `SELECT COUNT(*) FROM table`. При каждом срабатывании триггера в результате выполнения в таблице операций INSERT или DELETE происходит автоматическое обновление счетчика в системном мониторе.  
  
 В этой таблице приводится описание объекта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **User Settable**.  
  
|SQL Server, счетчики User Settable|Описание|  
|---------------------------------------|-----------------|  
|**Запрос**|Объект **User Settable** содержит счетчик запроса. Пользователи настраивают **User counters** в рамках объекта запроса.|  
  
 В данной таблице приводится описание **экземпляров** счетчика **Query** .  
  
|Экземпляры счетчиков запросов|Описание|  
|-----------------------------|-----------------|  
|**User counter 1**|Определяется хранимой процедурой **sp_user_counter1**.|  
|**User counter 2**|Определяется хранимой процедурой **sp_user_counter2**.|  
|**User counter 3**|Определяется хранимой процедурой **sp_user_counter3**.|  
|...||  
|**User counter 10**|Определяется хранимой процедурой **sp_user_counter10**.|  
  
 Хранимые процедуры пользовательских счетчиков запускаются из приложения с одним целочисленным параметром, представляющим новое значение счетчика. Например, чтобы задать значение 10 для объекта **User counter 1** , выполните следующую инструкцию Transact-SQL:  
  
```  
EXECUTE sp_user_counter1 10  
```  
  
 Хранимые процедуры пользовательских счетчиков можно вызывать из любого места, где могут быть вызваны любые другие (например пользовательские) хранимые процедуры. Например, можно создать следующую хранимую процедуру для подсчета числа и попыток соединений с момента запуска экземпляра сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
```  
DROP PROC My_Proc  
GO  
CREATE PROC My_Proc  
AS   
   EXECUTE sp_user_counter1 @@CONNECTIONS  
GO  
```  
  
 Функция @@CONNECTIONS возвращает число соединений или попыток соединений, осуществленных с момента запуска экземпляра сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это значение передается в качестве параметра хранимой процедуре **sp_user_counter1** .  
  
> [!IMPORTANT]  
>  Делайте запросы, определяемые в хранимых процедурах пользовательских счетчиков, как можно более простыми. Ресурсоемкие запросы, выполняющие ресурсоемкую сортировку или хэш-операции, либо задействующие большое количество операций ввода-вывода, являются очень затратными и могут повлиять на производительность.  
  
## <a name="permissions"></a>Разрешения  
 Хранимая процедура **sp_user_counter** доступна всем пользователям, но доступ к любому из счетчиков запросов может быть ограничен.  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
