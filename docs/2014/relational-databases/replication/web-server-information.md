---
title: Сведения о веб-сервере | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.webserverinformation.f1
ms.assetid: 86d72275-45c7-459f-98cf-f5a366ed279c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f7b461ed26b3e234f083add3312e256e164efc9b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063648"
---
# <a name="web-server-information"></a>Сведения о веб-сервере
  Сведения о веб-сервере необходимы для использования функции веб-синхронизации при репликации слиянием. Дополнительные сведения о конфигурации для веб-синхронизации см. в статье [Настройка веб-синхронизации](configure-web-synchronization.md).  
  
## <a name="options"></a>Параметры  
 **Адрес веб-сервера**  
 Если адрес веб-сервера задан на страницах **Моментальный снимок — FTP и Интернет** диалогового окна **Свойства публикации**, он отображается в этом текстовом поле как адрес по умолчанию. Можно принять значение по умолчанию или ввести полный адрес веб-сервера [!INCLUDE[msCoName](../../includes/msconame-md.md)] IIS, синхронизирующего данную подписку.  
  
 **Как будет соединяться с веб-сервером каждый подписчик**  
 Позволяет указать тип проверки подлинности, используемой для подключения к веб-серверу. Рекомендуется использовать обычную проверку подлинности для подключений к серверу IIS в сопряжении с безопасным протоколом Secure Sockets Layer (SSL). Если выбрана обычная проверка подлинности, введите имя входа и пароль, которые будут использоваться для подключения подписчика к серверу IIS.  
  
## <a name="see-also"></a>См. также:  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Просмотр и изменение свойств подписки по запросу](view-and-modify-pull-subscription-properties.md)   
 [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md)   
 [Subscribe to Publications](subscribe-to-publications.md)   
 [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md)  
  
  
