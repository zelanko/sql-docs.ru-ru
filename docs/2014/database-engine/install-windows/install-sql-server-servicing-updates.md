---
title: Установка обновлений для обслуживания SQL Server 2014 | Документация Майкрософт
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
ms.openlocfilehash: 07f438f86a22b866351a0b83ee7634338f3ad2cd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62775347"
---
# <a name="install-sql-server-2014-servicing-updates"></a>Установка обновлений для обслуживания SQL Server 2014
  В этом разделе описывается установка обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. В разделе рассматриваются следующие вопросы.  
  
-   Установка обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при установке нового экземпляра  
  
-   Установка обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] после установки экземпляра.  
  
 Пользователям рекомендуется своевременно оценивать и устанавливать последние обновления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы обеспечить наличие последних обновлений безопасности для систем.  
  
## <a name="installing-updates-for-sscurrent-during-a-new-installation"></a>Установка обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при установке нового экземпляра  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объединяет последние обновления продукта с установкой основного продукта, чтобы он и применимые обновления устанавливались одновременно. Функция обновления продукта может искать подходящие обновления в следующих источниках.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update  
  
-   Службы Windows Server Update Services (WSUS)  
  
-   Локальная папка  
  
-   Сетевая папка  
  
 Когда программа установки обнаруживает последние версии соответствующих обновлений, эти обновления загружаются и интегрируются в текущую процедуру установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Функция обновления продукта может включить в установку пакет обновления, накопительное обновление или и то и другое. Функция обновления продукта является расширением [функции интегрированной установки](https://go.microsoft.com/fwlink/?LinkId=219945) , существовавшей в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] PCU1.  
  
## <a name="installing-updates-for-sscurrent-after-it-has-already-been-installed"></a>Установка обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] после установки экземпляра  
 На установленном экземпляре [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]рекомендуется применить все доступные обновления: выпуски общего распространения (GDR-Security/критические обновления), пакеты обновления (SP), а также Последнее доступное накопительное обновление (Cu).  
  
 В зависимости от типа выпуска для обслуживания SQL Server обновления доступны через Центр обновления Майкрософт (MU), центра загрузки Майкрософт и (или) сервера исправлений службы поддержки пользователей. Обновления для системы безопасности и критических обновлений для SQL Server автоматически предоставляются Центр обновления Майкрософт (чтобы они могли видеть эти обновления, необходимо принять участие в программе MU через Центр обновления Windows на панели управления). Пакеты обновления доступны в виде необязательных или важных загружаемых файлов, а также в центре загрузки. Накопительные обновления доступны на сервере загрузки исправлений Майкрософт, приведенном в статьях базы знаний CU.  
  
## <a name="see-also"></a>См. также  
 [Установка SQL Server 2014 с помощью мастера установки &#40;установки&#41;](install-sql-server-from-the-installation-wizard-setup.md)   
 [Установка обновлений из командной строки](installing-updates-from-the-command-prompt.md) [Добавление компонентов в экземпляр компонента SQL Server 2014 &#40;установки&#41;](add-features-to-an-instance-of-sql-server-setup.md)   
 [Удаление установки SQL Server 2014](repair-a-failed-sql-server-installation.md)  
  
  
