---
title: Топологии для веб-синхронизации | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- Web synchronization, topologies
- IIS server configuration [SQL Server replication]
ms.assetid: 59444faf-bcb6-4421-a3df-8715753e453b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3607a2d85005827421353be5f9871c58de9f5a41
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191814"
---
# <a name="topologies-for-web-synchronization"></a>Topologies for Web Synchronization
  Существует несколько топологий репликации [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для веб-синхронизации. Наиболее часто используемые способы настройки веб-синхронизации включают в себя следующие.  
  
-   Одиночный сервер  
  
-   Два сервера  
  
-   Несколько системы на основе служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] IIS и переиздание с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 Дополнительные сведения о конфигурации для веб-синхронизации см. в статье [Настройка веб-синхронизации](configure-web-synchronization.md).  
  
## <a name="single-server"></a>Одиночный сервер  
 В самой простой топологии, службах IIS, издатель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и распространитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вместе находятся на одиночном сервере. Подписчики осуществляют синхронизацию, подключаясь к службам IIS на издателе. Издатель может быть защищен брандмауэром.  
  
> [!NOTE]  
>  Данная конфигурация рекомендуется только для сценариев, использующих корпоративные сети. Для других сценариев рекомендуется, чтобы сервер IIS и издатель/распространитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] находились на разных компьютерах.  
  
 ![Веб-синхронизация с одним сервером](media/web-sync02.gif "Веб-синхронизация с одним сервером")  
  
## <a name="two-servers"></a>Два сервера  
 Можно установить службы IIS на один сервер и настроить издатель и распространитель [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на другом сервере. Сервер, на котором запускаются службы IIS, может быть изолирован от Интернета брандмауэром. Подписчики осуществляют синхронизацию, подключаясь к службам IIS.  
  
 ![Веб-синхронизация с двумя серверами](media/web-sync03.gif "Веб-синхронизация с двумя серверами")  
  
## <a name="multiple-iis-systems-and-sql-server-republishing"></a>Несколько систем IIS и переиздание с помощью SQL Server  
 При необходимости поддержки очень большого количества подписчиков, одновременно осуществляющих синхронизацию, можно разделить работу между несколькими компьютерам, на которых выполняются службы IIS.  
  
 ![Веб-синхронизация с несколькими серверами IIS](media/web-sync04.gif "Веб-синхронизация с несколькими серверами IIS")  
  
 Если требуется дополнительная балансировка нагрузки на компьютере, использующем [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], можно создать иерархию переиздания на нескольких компьютерах. Издатель верхнего уровня публикует данные на подписчики, которые, в свою очередь, переиздают данные, осуществляя выравнивание нагрузки при обработке запросов от подписчиков.  
  
> [!NOTE]  
>  Подписчики могут синхронизироваться только с конкретным издателем. Например, подписчик на переиздающий подписчик A не может синхронизироваться с переиздающим подписчиком Б, если переиздающий подписчик А недоступен.  
  
 ![Веб-синхронизация с повторной публикацией](media/web-sync05.gif "Веб-синхронизация с повторной публикацией")  
  
## <a name="see-also"></a>См. также  
 [Настройка веб-синхронизации](configure-web-synchronization.md)   
 [Веб-синхронизация для репликации слиянием](web-synchronization-for-merge-replication.md)  
  
  
