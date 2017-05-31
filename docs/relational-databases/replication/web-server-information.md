---
title: "Сведения о веб-сервере | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newsubwizard.webserverinformation.f1
ms.assetid: 86d72275-45c7-459f-98cf-f5a366ed279c
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9c3db680206fb7c752fe27f968961d751c78aae0
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="web-server-information"></a>Сведения о веб-сервере
  Сведения о веб-сервере необходимы для использования функции веб-синхронизации при репликации слиянием. Дополнительные сведения о конфигурации для веб-синхронизации см. в статье [Настройка веб-синхронизации](../../relational-databases/replication/configure-web-synchronization.md).  
  
## <a name="options"></a>Параметры  
 **Адрес веб-сервера**  
 Если адрес веб-сервера задан на страницах **Моментальный снимок — FTP и Интернет** диалогового окна **Свойства публикации**, он отображается в этом текстовом поле как адрес по умолчанию. Можно принять значение по умолчанию или ввести полный адрес веб-сервера [!INCLUDE[msCoName](../../includes/msconame-md.md)] IIS, синхронизирующего данную подписку.  
  
 **Как будет соединяться с веб-сервером каждый подписчик**  
 Позволяет указать тип проверки подлинности, используемой для подключения к веб-серверу. Рекомендуется использовать обычную проверку подлинности для подключений к серверу IIS в сопряжении с безопасным протоколом Secure Sockets Layer (SSL). Если выбрана обычная проверка подлинности, введите имя входа и пароль, которые будут использоваться для подключения подписчика к серверу IIS.  
  
## <a name="see-also"></a>См. также:  
 [Создание подписки по запросу](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Просмотр и изменение свойств подписки по запросу](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Подписчики, отличные от подписчиков SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)   
 [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
