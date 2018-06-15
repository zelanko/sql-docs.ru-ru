---
title: Имя входа для обновляемых подписок | Документация Майкрософт
ms.custom: ''
ms.date: 08/25/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.updatablesubscriptionslogin.f1
ms.assetid: 301ea227-0455-40ba-9009-d38f8676b325
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6d4a62b5390198366e650b13bdf0d58028dc4e79
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32957739"
---
# <a name="login-for-updatable-subscriptions"></a>Имя входа для обновляемых подписок
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Если выбрано **Репликация** на странице **Обновляемые подписки** данного мастера, то чтобы выполнить немедленное обновление, требуется задать учетную запись с помощью подписчика, под которой будут устанавливаться соединения с издателем. 
  
 Соединения используются триггерами, которые запускаются на подписчике и распространяют изменения на издатель. Эта учетная запись необходима, даже если выбран пункт **Ставить изменения в очередь и фиксировать по возможности** на странице **Обновляемые подписки**. По умолчанию мастер создания подписки настраивает обновление посредством очередей с возможностью переключения на немедленное обновление при необходимости.  
  
> **ВАЖНО!** Учетная запись, заданная для соединения, должна предоставлять только разрешения для вставки, обновления и удаления данных в представлениях, которые репликация создает в базе данных публикации. Она не должна иметь никаких дополнительных разрешений. Предоставьте разрешения на представления, которые имеют имена в виде **syncobj_***\<шестнадцатеричный_номер>*, для учетной записи, настроенной на каждом подписчике.  
  
 Для этого типа соединения имеются следующие три параметра.  
  
-   Уже определенный связанный или удаленный сервер.  
  
-   Связанный сервер, создаваемый репликацией; соединение устанавливается с использованием учетных данных, заданных в данном мастере.  
  
-   Связанный сервер, создаваемый репликацией; соединение устанавливается с использованием учетных данных пользователя, который вносит изменения на подписчике.  
  
 Первые два параметра можно задать в данном мастере. Последний параметр можно задать только с использованием процедуры [sp_link_publication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md). Задайте значение **1** для параметра **@security_mode**.  
  
## <a name="options"></a>Параметры  
 **Создание связанного сервера, который подключается с использованием следующей проверки подлинности имени входа SQL Server:**  
 Репликация создает связанный сервер с использованием учетных данных, заданных в полях **Имя входа** и **Пароль** .  
  
 **Имя входа**  
 Введите имя входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которое обладает только разрешениями, описанными в данном разделе.  
  
 **Пароль**  
 Введите надежный пароль для имени входа, заданного в поле **Имя входа**.  
    
 **Использовать уже указанный связанный или удаленный сервер**  
 Для данного параметра необходим уже определенный связанный или удаленный сервер. Дополнительные сведения см. в статьях [Linked Servers (Database Engine)](../../relational-databases/linked-servers/linked-servers-database-engine.md) (Связанные серверы (ядро СУБД)) и [Remote Servers](../../database-engine/configure-windows/remote-servers.md) (Удаленные серверы). Убедитесь в том, что имя входа, используемое для связанного сервера или удаленного сервера, имеет надежный пароль и обладает только разрешениями, описанными в данном разделе.  
  
## <a name="see-also"></a>См. также раздел  
 [Создание обновляемой подписки для публикации транзакций](publish/create-an-updatable-subscription-to-a-transactional-publication.md)   
 [Просмотр и изменение параметров безопасности репликации](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [Updatable Subscriptions- For Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  (Обновляемые подписки для репликации транзакций)  
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
