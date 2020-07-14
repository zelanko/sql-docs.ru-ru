---
title: Имя входа для обновляемых подписок | Документация Майкрософт
ms.custom: ''
ms.date: 08/25/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.updatablesubscriptionslogin.f1
ms.assetid: 301ea227-0455-40ba-9009-d38f8676b325
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d242fc31411bc0fdb05cca1f65355f49acec575a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85640428"
---
# <a name="login-for-updatable-subscriptions"></a>Имя входа для обновляемых подписок
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Если выбрано **Репликация** на странице **Обновляемые подписки** данного мастера, то чтобы выполнить немедленное обновление, требуется задать учетную запись с помощью подписчика, под которой будут устанавливаться соединения с издателем. 
  
 Соединения используются триггерами, которые запускаются на подписчике и распространяют изменения на издатель. Эта учетная запись необходима, даже если выбран пункт **Ставить изменения в очередь и фиксировать по возможности** на странице **Обновляемые подписки**. По умолчанию мастер создания подписки настраивает обновление посредством очередей с возможностью переключения на немедленное обновление при необходимости.  
  
> **ВАЖНО!** Учетная запись, заданная для соединения, должна предоставлять только разрешения для вставки, обновления и удаления данных в представлениях, которые репликация создает в базе данных публикации. Она не должна иметь никаких дополнительных разрешений. Предоставьте разрешения на представления в базе данных публикации с именами в виде **syncobj_** _\<HexadecimalNumber>_ , для учетной записи, настроенной на каждом подписчике.  
  
 Для этого типа соединения имеются следующие три параметра.  
  
-   Уже определенный связанный или удаленный сервер.  
  
-   Связанный сервер, создаваемый репликацией; соединение устанавливается с использованием учетных данных, заданных в данном мастере.  
  
-   Связанный сервер, создаваемый репликацией; соединение устанавливается с использованием учетных данных пользователя, который вносит изменения на подписчике.  
  
 Первые два параметра можно задать в данном мастере. Последний параметр можно задать только с помощью процедуры [sp_link_publication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md). Задайте значение **1** для параметра `@security_mode`.  
  
## <a name="options"></a>Параметры  
 **Создание связанного сервера, который подключается с использованием следующей проверки подлинности имени входа SQL Server:**  
 Репликация создает связанный сервер с использованием учетных данных, заданных в полях **Имя входа** и **Пароль** .  
  
 **Имя входа**  
 Введите имя входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которое обладает только разрешениями, описанными в данном разделе.  
  
 **Пароль**  
 Введите надежный пароль для имени входа, заданного в поле **Имя входа**.  
    
 **Использовать уже указанный связанный или удаленный сервер**  
 Для данного параметра необходим уже определенный связанный или удаленный сервер. Дополнительные сведения см. в статьях [Linked Servers (Database Engine)](../../relational-databases/linked-servers/linked-servers-database-engine.md) (Связанные серверы (ядро СУБД)) и [Remote Servers](../../database-engine/configure-windows/remote-servers.md) (Удаленные серверы). Убедитесь в том, что имя входа, используемое для связанного сервера или удаленного сервера, имеет надежный пароль и обладает только разрешениями, описанными в данном разделе.  
  
## <a name="see-also"></a>См. также раздел  
 [Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md)   
 [Просмотр и изменение параметров безопасности репликации](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
