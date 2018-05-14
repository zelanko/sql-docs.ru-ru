---
title: Папка моментальных снимков | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
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
- sql13.rep.replicationutilities.specifysnapshotfolder.f1
ms.assetid: 3eb1b73f-ddb3-4d09-be6e-811c414698e9
caps.latest.revision: 24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: acb28b1ebb438f3ff135eefe866a5f224134c7da
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="snapshot-folder"></a>Папка моментальных снимков
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Страница **Папка моментальных снимков** отображается в мастере настройки распространителя и мастере создания публикаций. Заданное вами местоположение для папки моментальных снимков будет использоваться по умолчанию для всех издателей, включенных данным мастером (папка моментальных снимков по умолчанию не используется для издателей, включенных позднее с использованием диалогового окна **Свойства распространителя** ). Это значение по умолчанию можно заменить для любого издателя на странице **Издатели** мастера настройки распространителя или диалогового окна **Свойства распространителя** .  
  
 Папка моментальных снимков — это просто каталог, назначенный для совместного использования; агенты, считывающие и записывающие данные в эту папку, должны иметь достаточные разрешения для доступа к ней. Дополнительные сведения о надлежащей защите папок см. в статье [Организация безопасности папки моментальных снимков](../../relational-databases/replication/security/secure-the-snapshot-folder.md). До реализации репликации необходимо убедиться, что агенты репликации смогут подключиться к папке моментальных снимков. Войдите в систему с учетной записью, которая будет использоваться каждым агентом, и попытайтесь получить доступ к папке моментальных снимков.  
  
## <a name="options"></a>Параметры  
 **Snapshot folder**  
 Введите путь к папке, в которой будет храниться моментальный снимок.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует настроить совместно используемую сетевую папку в качестве местоположения папки моментальных снимков. Локальные пути (начинающиеся с буквы диска, например C:\\) недоступны агентам с других компьютеров.  
  
## <a name="see-also"></a>См. также:  
 [Альтернативные расположения папки моментальных снимков](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)   
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
