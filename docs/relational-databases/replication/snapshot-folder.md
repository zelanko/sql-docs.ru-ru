---
title: Папка моментальных снимков | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.replicationutilities.specifysnapshotfolder.f1
ms.assetid: 3eb1b73f-ddb3-4d09-be6e-811c414698e9
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: c33897a3597bfecf58a36ee371821a6f944e44ce
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76287177"
---
# <a name="snapshot-folder"></a>Папка моментальных снимков
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

Страница **Папка моментальных снимков** отображается в мастере настройки распространителя и мастере создания публикаций. Заданное вами местоположение для папки моментальных снимков будет использоваться по умолчанию для всех издателей, включенных данным мастером (папка моментальных снимков по умолчанию не используется для издателей, включенных позднее с использованием диалогового окна **Свойства распространителя** ). Это значение по умолчанию можно заменить для любого издателя на странице **Издатели** мастера настройки распространителя или диалогового окна **Свойства распространителя** .  
  
Папка моментальных снимков — это просто каталог, назначенный для совместного использования; агенты, считывающие и записывающие данные в эту папку, должны иметь достаточные разрешения для доступа к ней. Дополнительные сведения о надлежащей защите папок см. в статье [Организация безопасности папки моментальных снимков](../../relational-databases/replication/security/secure-the-snapshot-folder.md). До реализации репликации необходимо убедиться, что агенты репликации смогут подключиться к папке моментальных снимков. Войдите в систему с учетной записью, которая будет использоваться каждым агентом, и попытайтесь получить доступ к папке моментальных снимков.  

Для управляемого экземпляра базы данных SQL Microsoft Azure папка моментальных снимков должна быть общей папкой Azure. 
  
## <a name="options"></a>Параметры  
 **Папка моментальных снимков**  
 Введите путь к папке, в которой будет храниться моментальный снимок.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует настроить совместно используемую сетевую папку в качестве местоположения папки моментальных снимков. Локальные пути (начинающиеся с буквы диска, например C:\\) недоступны агентам с других компьютеров.  
  
## <a name="see-also"></a>См. также:  
 [Изменение параметров моментального снимка](../../relational-databases/replication/snapshot-options.md)   
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)   
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
