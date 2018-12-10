---
title: Указание расположения моментальных снимков по умолчанию (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], default locations
- default snapshot locations
ms.assetid: 27c5d9ad-a915-4c59-a8b7-82e3af61ac4d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3aa167df2f75b42cf5612b725cbfd368f4dc4407
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52519952"
---
# <a name="specify-the-default-snapshot-location-sql-server-management-studio"></a>указать расположение моментальных снимков (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Задайте местоположение моментальных снимков по умолчанию на странице **Папка моментальных снимков** мастера настройки распространителя. Дополнительные сведения см. в статье [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md). При создании публикации на сервере, не настроенном в качестве распространителя, задайте местоположение моментальных снимков по умолчанию на странице **Папка моментальных снимков** мастера создания публикаций. Дополнительные сведения об использовании мастера см. в статье [Создание публикации](../../relational-databases/replication/publish/create-a-publication.md).  
  
 В диалоговом окне **Свойства распространителя —** распространитель> **на странице \<Издатели** измените расположение моментальных снимков по умолчанию. Дополнительные сведения см. в статье [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md). В диалоговом окне **Свойства публикации — \<публикация>** укажите папку моментальных снимков для каждой публикации. Дополнительные сведения см. в статье [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### <a name="to-modify-the-default-snapshot-location"></a>Изменение местоположения моментальных снимков по умолчанию  
  
1.  В диалоговом окне **Свойства распространителя — \<распространитель>** на странице **Издатели** нажмите кнопку свойств (**...**) рядом с издателем, для которого нужно изменить расположение моментальных снимков по умолчанию.  
  
2.  В диалоговом окне **Свойства издателя — \<издатель>** введите значение для свойства **Папка моментальных снимков по умолчанию**.  
  
    > [!NOTE]  
    >  Агент моментальных снимков должен иметь разрешения на запись в указанный каталог, а агент распространителя или агент слияния должен иметь разрешения на чтение из этого каталога. Если используются подписки по запросу, необходимо указать UNC-путь общего каталога, например \\\computername\snapshot. Дополнительные сведения см. в статье [Организация безопасности папки моментальных снимков](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Альтернативные расположения папки моментальных снимков](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
