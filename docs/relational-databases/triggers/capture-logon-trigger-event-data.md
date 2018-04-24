---
title: Данные о захвате событий триггера входа | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: triggers
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e05b1ab4-c10b-402a-9591-f6ec1e3db8c0
caps.latest.revision: 5
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 4867295e93c60372f38a28abce0aba7943a2c83b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="capture-logon-trigger-event-data"></a>Захват данных событий триггера входа
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]
  XML-данные о событиях LOGON для использования внутри триггеров входа могут быть захвачены с использованием функции [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md) . Для события LOGON возвращается следующая схема данных событий:  
  
 `<EVENT_INSTANCE>`  
  
 `<EventType>event_type</EventType>`  
  
 `<PostTime>post_time</PostTime>`  
  
 `<SPID>spid</SPID>`  
  
 `<ServerName>server_name</ServerName>`  
  
 `<LoginName>login_name</LoginName>`  
  
 `<LoginType>login_type</LoginType>`  
  
 `<SID>sid</SID>`  
  
 `<ClientHost>client_host</ClientHost>`  
  
 `<IsPooled>is_pooled</IsPooled>`  
  
 `</EVENT_INSTANCE>`  
  
 `<EventType>`  
 Содержит `LOGON`.  
  
 `<PostTime>`  
 Содержит время запроса на установление сеанса.  
  
 `<SID>`  
 Содержит закодированный в base 64-битовый бинарный поток идентификационного номера безопасности (SID) для указанного имени входа.  
  
 `<ClientHost>`  
 Содержит имя узла клиента, с которого устанавливается подключение. Если имя сервера совпадает с именем клиента, то значение по умолчанию — «`<local_machine>`». Иначе значение равно IP-адресу клиента.  
  
 `<IsPooled>`  
 `1` , если соединение повторно используется с помощью пула соединений. В противном случае — значение `0`.  
  
  
