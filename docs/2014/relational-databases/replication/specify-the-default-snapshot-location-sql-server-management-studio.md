---
title: Указание расположения моментальных снимков по умолчанию (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], default locations
- default snapshot locations
ms.assetid: 27c5d9ad-a915-4c59-a8b7-82e3af61ac4d
caps.latest.revision: 36
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b94fd7bcd72476fd550c139533e7540e66f39d4f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172725"
---
# <a name="specify-the-default-snapshot-location-sql-server-management-studio"></a>указать расположение моментальных снимков (среда SQL Server Management Studio)
  Задайте местоположение моментальных снимков по умолчанию на странице **Папка моментальных снимков** мастера настройки распространителя. Дополнительные сведения см. в статье [Настройка публикации и распространения](configure-publishing-and-distribution.md). При создании публикации на сервере, не настроенном в качестве распространителя, задайте местоположение моментальных снимков по умолчанию на странице **Папка моментальных снимков** мастера создания публикаций. Дополнительные сведения об использовании мастера см. в статье [Создание публикации](publish/create-a-publication.md).  
  
 В диалоговом окне **Свойства распространителя —** распространитель> **на странице \<Издатели** измените расположение моментальных снимков по умолчанию. Дополнительные сведения см. в статье [Просмотр и изменение свойств издателя и распространителя](view-and-modify-distributor-and-publisher-properties.md). В диалоговом окне **Свойства публикации — \<публикация>** укажите папку моментальных снимков для каждой публикации. Дополнительные сведения см. в статье [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).  
  
### <a name="to-modify-the-default-snapshot-location"></a>Изменение местоположения моментальных снимков по умолчанию  
  
1.  В диалоговом окне **Свойства распространителя — \<распространитель>** на странице **Издатели** нажмите кнопку свойств (**...**) рядом с издателем, для которого нужно изменить расположение моментальных снимков по умолчанию.  
  
2.  В диалоговом окне **Свойства издателя — \<издатель>** введите значение для свойства **Папка моментальных снимков по умолчанию**.  
  
    > [!NOTE]  
    >  Агент моментальных снимков должен иметь разрешения на запись в указанный каталог, а агент распространителя или агент слияния должен иметь разрешения на чтение из этого каталога. Если используются подписки по запросу, необходимо указать UNC-путь общего каталога, например \\\computername\snapshot. Дополнительные сведения см. в статье [Организация безопасности папки моментальных снимков](security/secure-the-snapshot-folder.md).  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Альтернативные расположения папки моментальных снимков](alternate-snapshot-folder-locations.md)   
 [Инициализация подписки с помощью моментального снимка](initialize-a-subscription-with-a-snapshot.md)  
  
  
