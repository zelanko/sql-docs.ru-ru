---
title: "Указание расположения моментальных снимков по умолчанию (SQL Server Management Studio) | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], default locations
- default snapshot locations
ms.assetid: 27c5d9ad-a915-4c59-a8b7-82e3af61ac4d
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e6cda346b9dfdbc0a5693ce263456ee7f10076a2
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="specify-the-default-snapshot-location-sql-server-management-studio"></a>указать расположение моментальных снимков (среда SQL Server Management Studio)
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
  
  
