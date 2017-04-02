---
title: "Сведения о веб-сервере | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.webserverinformation.f1"
ms.assetid: 86d72275-45c7-459f-98cf-f5a366ed279c
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# Сведения о веб-сервере
  Сведения о веб-сервере необходимы для использования функции веб-синхронизации при репликации слиянием. Сведения о настройке веб-синхронизации см. в разделе [настройки веб-синхронизации](../../relational-databases/replication/configure-web-synchronization.md).  
  
## Параметры  
 **Адрес веб-сервера**  
 Если вы указали адрес веб-сервера в **andInternet моментальный снимок — FTP** Страница **Свойства публикации** откроется диалоговое окно, его в этом текстовом поле по умолчанию. Можно принять значение по умолчанию или ввести полный адрес веб-сервера [!INCLUDE[msCoName](../../includes/msconame-md.md)] IIS, синхронизирующего данную подписку.  
  
 **Как будет соединяться с веб-сервером каждый подписчик**  
 Позволяет указать тип проверки подлинности, используемой для подключения к веб-серверу. Рекомендуется использовать обычную проверку подлинности для подключений к серверу IIS в сопряжении с безопасным протоколом Secure Sockets Layer (SSL). Если выбрана обычная проверка подлинности, введите имя входа и пароль, которые будут использоваться для подключения подписчика к серверу IIS.  
  
## См. также:  
 [Создание подписки по запросу](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Просмотр и изменение свойств подписки по запросу](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Подписчики, отличные от подписчиков SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [Веб-синхронизация для репликации слиянием](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  