---
title: Реализация уведомлений о событиях | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], target service
- target service [SQL Server]
- event notifications [SQL Server], creating
ms.assetid: 29ac8f68-a28a-4a77-b67b-a8663001308c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8c5b17b45b50634806c60e5064efc6ebd9d03f8b
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53353762"
---
# <a name="implement-event-notifications"></a>Реализация уведомлений о событиях
  Для реализации уведомлений о событиях необходимо сперва создать целевую службу, которая будет получать уведомления о событиях, а затем создать уведомление о событиях.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssSB](../../includes/sssb-md.md)] на удаленном сервере, необходимо настроить безопасность диалога. Безопасность диалога должна быть настроена вручную согласно модели полной безопасности.  
  
## <a name="creating-the-target-service"></a>Создание целевой службы  
 Не нужно создавать службу, инициирующую компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)], так как [!INCLUDE[ssSB](../../includes/sssb-md.md)] включает в себя следующий специальный тип сообщения и контракт для уведомлений о событиях:  
  
```  
https://schemas.microsoft.com/SQL/Notifications/PostEventNotification  
```  
  
 Целевая служба, принимающая уведомления о событиях, должна поддерживать такой уже существующий контракт.  
  
 **Создание целевой службы**  
  
1.  Создайте очередь для получения сообщений.  
  
    > [!NOTE]  
    >  Очередь получает сообщения следующего типа: `https://schemas.microsoft.com/SQL/Notifications/QueryNotification`.  
  
2.  Создайте службу для очереди, ссылающуюся на контракт уведомлений о событии.  
  
3.  Создайте маршрут для службы, чтобы определить адрес, на который компонент [!INCLUDE[ssSB](../../includes/sssb-md.md)] будет отправлять сообщения этой службе. Если уведомление о событии отправляется службе в той же базе данных, укажите `ADDRESS = 'LOCAL'`.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssSB](../../includes/sssb-md.md)] определяет службу, получающую уведомления. Если уведомление о событии направляется службе на удаленном сервере, маршруты необходимо определить и на исходном, и на целевом сервере, чтобы обеспечить двухстороннюю связь.  
  
 В следующем примере создается очередь, служба для этой очереди и маршрут к службе, обрабатывающей сообщения от контракта уведомления о событиях:  
  
```  
CREATE QUEUE NotifyQueue ;  
GO  
CREATE SERVICE NotifyService  
ON QUEUE NotifyQueue  
(  
[https://schemas.microsoft.com/SQL/Notifications/PostEventNotification]  
);  
GO  
CREATE ROUTE NotifyRoute  
WITH SERVICE_NAME = 'NotifyService',  
ADDRESS = 'LOCAL';  
GO  
```  
  
## <a name="creating-the-event-notification"></a>Создание уведомления о событии  
 Уведомления о событиях создаются при помощи инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE EVENT NOTIFICATION и удаляются при помощи инструкции DROP EVENT NOTIFICATION. Чтобы изменить уведомление о событии, его нужно удалить, а затем создать заново.  
  
 В следующем примере создается уведомление о событии `CreateDatabaseNotification`. Это уведомление отправляет предварительно созданной службе `CREATE_DATABASE` сообщения обо всех событиях `NotifyService`, происходящих на сервере.  
  
```  
CREATE EVENT NOTIFICATION CreateDatabaseNotification  
ON SERVER  
FOR CREATE_DATABASE  
TO SERVICE 'NotifyService', '8140a771-3c4b-4479-8ac0-81008ab17984' ;  
```  
  
> [!CAUTION]  
>  Уведомления о событиях считают события CREATE_SCHEMA и определения <schema_element> в инструкциях CREATE SCHEMA различными событиями. Например, пусть создано уведомление о событиях CREATE_SCHEMA и CREATE_TABLE и выполняется следующий пакет.  
>   
>  `CREATE SCHEMA s`  
>   
>  `CREATE TABLE t1 (col1 int)`  
>   
>  В этом случае уведомление о событиях направляется дважды: в первый раз при возникновении события CREATE_SCHEMA, а во второй — при возникновении события CREATE_TABLE. Рекомендуется либо избегать создания уведомлений о событиях одновременно для событий CREATE_SCHEMA и текстов <schema_element> в любых соответствующих определениях CREATE SCHEMA, либо встраивать в приложение логику, позволяющую избежать регистрации ненужных данных о событиях.  
  
 **Создание уведомления о событии**  
  
-   [CREATE EVENT NOTIFICATION (Transact-SQL)](/sql/t-sql/statements/create-event-notification-transact-sql)  
  
 **Удаление уведомления о событии**  
  
-   [DROP EVENT NOTIFICATION (Transact-SQL)](/sql/t-sql/statements/drop-event-notification-transact-sql)  
  
## <a name="see-also"></a>См. также  
 [Получение сведений об уведомлениях о событиях](event-notifications.md)   
 [EVENTDATA (Transact-SQL)](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
