---
description: Проверка состояния сообщений электронной почты, отправленных при помощи компонента Database Mail
title: Состояние сообщений электронной почты, отправленных при помощи компонента Database Mail
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- e-mail [SQL Server], status information
- mail [SQL Server], status information
- Database Mail [SQL Server], message status
- status information [Database Mail]
ms.assetid: eb290f24-b52f-46bc-84eb-595afee6a5f3
author: stevestein
ms.author: sstein
ms.custom: seo-dt-2019
ms.openlocfilehash: 245a50951896f923165e011fc51c09abd00f96e4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421248"
---
# <a name="check-the-status-of-e-mail-messages-sent-with-database-mail"></a>Проверка состояния сообщений электронной почты, отправленных при помощи компонента Database Mail
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  В этом разделе описывается порядок проверки с помощью [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] состояния сообщений электронной почты, отправленных компонентом Database Mail в [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Перед началом работы**  
  
-   **Чтобы просмотреть состояние сообщения электронной почты отправляются с помощью компонента Database Mail, используя:**  [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
 Компонент Database Mail хранит копии исходящих сообщений электронной почты и отображает их в представлениях **sysmail_allitems**, **sysmail_sentitems**, **sysmail_unsentitems**и **sysmail_faileditems** базы данных **msdb** . Внешняя программа компонента Database Mail протоколирует активность и отображает журнал при помощи компонента Windows Application Event Log и представления **sysmail_event_log** базы данных **msdb** . Для проверки состояния сообщений электронной почты запустите запрос для данного представления. У сообщений электронной почты может быть одно из следующих четырех состояний: **отправлено**, **не отправлено**, **попытка отправки**и **ошибка при отправке**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Проверка состояния сообщений электронной почты, отправленных компонентом Database Mail**  
  
1.  Выберите из таблицы **sysmail_allitems** важные сообщения, используя поля **mailitem_id** или **sent_status**.  
  
2.  Чтобы проверить состояние сообщений электронной почты, возвращенных из внешней программы, соединение **sysmail_allitems** с представлением **sysmail_event_log** столбца **mailitem_id** , как показано в следующем разделе.  
  
     По умолчанию внешняя программа не протоколирует сведения об успешно посланных сообщениях. Для протоколирования всех сообщений установите детализированный уровень ведения журнала на странице **Установка параметров системы** окна **Мастер настройки компонента Database Mail**.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В следующем примере приводятся данные о любых сообщениях электронной почты, отправленных `danw` , которые внешняя программа не смогла успешно отправить. Инструкция выдает тему, дату и время попытки отправки сообщения, при отправке которого внешней программой произошла ошибка, а также текст сообщения об ошибке из журнала компонента Database Mail.  
  
```  
USE msdb ;  
GO  
  
-- Show the subject, the time that the mail item row was last  
-- modified, and the log information.  
-- Join sysmail_faileditems to sysmail_event_log   
-- on the mailitem_id column.  
-- In the WHERE clause list items where danw was in the recipients,  
-- copy_recipients, or blind_copy_recipients.  
-- These are the items that would have been sent  
-- to danw.  
  
SELECT items.subject,  
    items.last_mod_date  
    ,l.description FROM dbo.sysmail_faileditems as items  
INNER JOIN dbo.sysmail_event_log AS l  
    ON items.mailitem_id = l.mailitem_id  
WHERE items.recipients LIKE '%danw%'    
    OR items.copy_recipients LIKE '%danw%'   
    OR items.blind_copy_recipients LIKE '%danw%'  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Ведение журнала и аудит компонента Database Mail](../../relational-databases/database-mail/database-mail-log-and-audits.md)  
  
  
