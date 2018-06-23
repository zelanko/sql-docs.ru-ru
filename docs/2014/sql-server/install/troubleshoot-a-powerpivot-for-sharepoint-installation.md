---
title: Устранение неполадок PowerPivot для SharePoint | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: b4881ce3be8ede7d97dc2b71fb464b94b8677ca0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109629"
---
# <a name="troubleshoot-a-powerpivot-for-sharepoint-installation"></a>Устранение неполадок установки PowerPivot для SharePoint
  Если вместо ожидаемых страниц и компонентов выдаются ошибки, выполните следующие действия.  
  
-   Откройте заметки о выпуске SharePoint и [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , чтобы выяснить, какие существуют способы решения известных проблем установки. Заметки о выпуске доступны на установочном носителе или на сайте Майкрософт, с которого было загружено программное обеспечение.  
  
    -   [Заметки о выпуске SQL Server 2014](http://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx).  
  
-   См. раздел [Устранение неполадок установки PowerPivot (и других надстроек)](http://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx)портала TechNet Wiki.  
  
## <a name="issues"></a>Проблемы  
  
### <a name="powerpivot-gallery-thumbnail-images-show-as-a-red-x"></a>Миниатюрные изображения в галерее PowerPivot отображаются в виде красного x  
 Одной из возможных причин **Интеграция функций PowerPivot для семейства веб-сайтов** не активна. Выполните следующие действия.  
  
1.  В библиотеке PowerPivot Gallery, выберите **параметры сайта** значок шестеренки ![параметры SharePoint](../../../2014/analysis-services/media/as-sharepoint2013-settings-gear.gif "параметры SharePoint") или **домашней** списка.  
  
2.  Щелкните **Компоненты семейства веб-сайтов** в разделе **Администрирование семейства веб-сайтов**.  
  
3.  Щелкните **Компоненты коллекции сайтов**.  
  
4.  Убедитесь, что значение **Функции интеграции с PowerPivot для семейств веб-сайтов** равно **Активны**.  
  
 Дополнительные причины возникновения этой проблемы см. в разделе [Галерея PowerPivot отображается красная x для значков](http://support.microsoft.com/kb/2361559) (http://support.microsoft.com/kb/2361559).  
  
  