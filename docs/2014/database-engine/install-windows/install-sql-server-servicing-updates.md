---
title: Установка обновлений обслуживания SQL Server 2014 | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c7601914ed32def54b153282a90b51629b1380b6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193632"
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
 На установленном экземпляре [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], рекомендуется применять все доступные обновления: выпуски для общего распространения (GDR - безопасности или критические обновления), пакеты обновления (SP1), а также последние доступные накопительное обновление (CU).  
  
 В зависимости от типа обслуживания выпуска обновления SQL Server доступны через Центр обновления Майкрософт, центра загрузки Майкрософт и/или исправление сервера в службу поддержки пользователей. Безопасности и критические обновления для SQL Server автоматически предоставляются через Центр обновления Майкрософт (чтобы иметь возможность увидеть эти обновления, которые необходимо явно согласиться на Центр обновления Майкрософт через Центр обновления Windows на панели управления). Пакеты обновления доступны Центр обновления Майкрософт по мере загрузки необязательно/важно, а также центра загрузки Майкрософт. Накопительные пакеты обновления доступны на сервере загрузки исправления Microsoft, приведенные в статьях базы знаний CU.  
  
## <a name="see-also"></a>См. также  
 [Установка с помощью мастера установки SQL Server 2014 &#40;установки&#41;](install-sql-server-from-the-installation-wizard-setup.md)   
 [Добавление компонентов к экземпляру SQL Server 2014 &#40;установки&#41;](add-features-to-an-instance-of-sql-server-setup.md)   
 [Удаление установки SQL Server 2014](repair-a-failed-sql-server-installation.md)  
  
  