---
title: Установка обновлений для обслуживания SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 09/05/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 7d6c962b-c8d0-49f7-a2ac-00ad8dca930a
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: jroth
ms.openlocfilehash: 6e27dc247648e8fd69ed372a5ddd2a8566240efd
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794897"
---
# <a name="install-sql-server-servicing-updates"></a>Установка обновлений для обслуживания SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Эта статья содержит сведения об установке обновлений для [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]. В разделе рассматриваются следующие вопросы.
  
- Установка обновлений для [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] при установке нового экземпляра  
  
- Установка обновлений для [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] после установки экземпляра.  
  
Установите последние обновления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы обеспечить наличие последних обновлений безопасности для систем.  
  
## <a name="installing-updates-for-includenoversionincludesssnoversion-mdmd-during-a-new-installation"></a>Установка обновлений для [!INCLUDE[noVersion](../../includes/ssNoVersion-md.md)] при установке нового экземпляра  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объединяет последние обновления продукта с установкой основного продукта, чтобы он и применимые обновления устанавливались одновременно. Функция обновления продукта может искать подходящие обновления в следующих источниках.  
  
- [!INCLUDE[msCoName](../../includes/msconame-md.md)] Update  
  
- Службы Windows Server Update Services (WSUS)  
  
- Локальная папка  
  
- Сетевая папка  
  
Когда программа установки обнаруживает последние версии соответствующих обновлений, эти обновления загружаются и интегрируются в текущую процедуру установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Функция обновления продукта может включить в установку пакет обновления, накопительное обновление или и то и другое.  
  
## <a name="installing-updates-for-includessnoversionincludesssnoversion-mdmd-after-it-has-already-been-installed"></a>Установка обновлений для [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] после установки экземпляра  
В установленном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]рекомендуется установить последние обновления безопасности и критические обновления, в том числе выпуски для общего распространения (GDR), пакеты обновления (SP) и накопительные пакеты обновления (CU). Дополнительные сведения см. в [объявлении о добавочной модели обслуживания SQL Server за март 2016 года](https://blogs.msdn.microsoft.com/sqlreleaseservices/announcing-updates-to-the-sql-server-incremental-servicing-model-ism/).

> [!NOTE]
> Начиная с [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] мы реализуем упрощенный и прогнозируемый основной жизненный цикл обслуживания, поэтому пакеты обновления (SP) больше не будут доступны. При необходимости следует использовать только накопительные обновления (CU) и выпуски для общего распространения (GDR).
> Дополнительные сведения см. в [объявлении о современной модели обслуживания SQL Server за сентябрь 2017 года](https://blogs.msdn.microsoft.com/sqlreleaseservices/announcing-the-modern-servicing-model-for-sql-server/).
  
Обновления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступны через центр обновления [!INCLUDE[msCoName](../../includes/msconame-md.md)] (MU), службу обновления Windows (WSUS) и Центр загрузки Майкрософт. Обновления безопасности и критические обновления для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступны в центре обновления [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Чтобы увидеть эти обновления, необходимо дать согласие на использование MU в приложении центра обновления Windows на панели управления.  
  
После получения обновления через центр обновления [!INCLUDE[msCoName](../../includes/msconame-md.md)] все компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обновляются до последней версии в автоматическом режиме. Если необходима дополнительная гибкость в процессе установки или отсутствует доступ к Интернету или службам WSUS, то нужно получить обновления из Центра загрузки [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
## <a name="see-also"></a>См. также:  
[Установка SQL Server с помощью мастера установки &#40;программы установки&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)
[Добавление компонентов в экземпляр SQL Server &#40;программа установки&#41;](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)
[Исправление неудавшейся установки SQL Server](../../database-engine/install-windows/repair-a-failed-sql-server-installation.md)  

