---
title: Установка обновлений обслуживания SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5f369185b2d7d5e5d65fc98bca40ba66029ceaa8
ms.sourcegitcommit: 87f29b23d5ab174248dab5d558830eeca2a6a0a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51018669"
---
# <a name="install-sql-server-2014-servicing-updates"></a>Установка обновлений для обслуживания SQL Server 2014
  В этом разделе описывается установка обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. В разделе рассматриваются следующие вопросы.  
  
-   Установка обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при установке нового экземпляра  
  
-   Установка обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] после установки экземпляра.  
  
 Пользователям рекомендуется своевременно оценивать и устанавливать последние обновления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы обеспечить наличие последних обновлений безопасности для систем.  
  
## <a name="installing-updates-for-includesscurrentincludessscurrent-mdmd-during-a-new-installation"></a>Установка обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при установке нового экземпляра  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объединяет последние обновления продукта с установкой основного продукта, чтобы он и применимые обновления устанавливались одновременно. Функция обновления продукта может искать подходящие обновления в следующих источниках.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update  
  
-   Службы Windows Server Update Services (WSUS)  
  
-   Локальная папка  
  
-   Сетевая папка  
  
 Когда программа установки обнаруживает последние версии соответствующих обновлений, эти обновления загружаются и интегрируются в текущую процедуру установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Функция обновления продукта может включить в установку пакет обновления, накопительное обновление или и то и другое. Функция обновления продукта является расширением [функции интегрированной установки](http://go.microsoft.com/fwlink/?LinkId=219945) , существовавшей в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] PCU1.  
  
## <a name="installing-updates-for-includesscurrentincludessscurrent-mdmd-after-it-has-already-been-installed"></a>Установка обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] после установки экземпляра  
 В установленном экземпляре [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], мы рекомендуем применить все доступные обновления: выпуски для общего распространения (GDR - безопасности и критические обновления), пакеты обновления (SP1), а также последние доступные накопительное обновление (CU).  
  
 В зависимости от типа служебный выпуск обновления SQL Server доступны через Центр обновления Майкрософт, центра загрузки Майкрософт и/или исправление сервера в службу поддержки пользователей. Безопасности и критические обновления для SQL Server автоматически получают центром обновления Майкрософт (чтобы иметь возможность увидеть эти обновления, которые необходимо согласиться на Центр обновления Майкрософт через Центр обновления Windows на панели управления). Пакеты обновления доступны Центр обновления Майкрософт, как необязательный/важные файлы для загрузки, а также в центре загрузки. Накопительные пакеты обновления доступны на сервере загрузки Microsoft исправление из статьи базы знаний и накопительным Обновлением.  
  
## <a name="see-also"></a>См. также  
 [Установка SQL Server 2014 с помощью мастера установки &#40;установки&#41;](install-sql-server-from-the-installation-wizard-setup.md)   
 [Добавление компонентов к экземпляру SQL Server 2014 &#40;установки&#41;](add-features-to-an-instance-of-sql-server-setup.md)   
 [Удаление установки SQL Server 2014](repair-a-failed-sql-server-installation.md)  
  
  
