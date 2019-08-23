---
title: Устранение неполадок при установке PowerPivot для SharePoint | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 797405386e8a6c0b9e62328699f3a73a6d845313
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892444"
---
# <a name="troubleshoot-a-powerpivot-for-sharepoint-installation"></a>Устранение неполадок установки PowerPivot для SharePoint
  Если вместо ожидаемых страниц и компонентов выдаются ошибки, выполните следующие действия.  
  
-   Откройте заметки о выпуске SharePoint и [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , чтобы выяснить, какие существуют способы решения известных проблем установки. Заметки о выпуске доступны на установочном носителе или на сайте Майкрософт, с которого было загружено программное обеспечение.  
  
    -   [Заметки о выпуске SQL Server 2014](https://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx).  
  
-   См. раздел [Устранение неполадок установки PowerPivot (и других надстроек)](https://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx)портала TechNet Wiki.  
  
## <a name="issues"></a>Проблемы  
  
### <a name="powerpivot-gallery-thumbnail-images-show-as-a-red-x"></a>Миниатюрные изображения в галерее PowerPivot отображаются в виде красного x  
 Одной из возможных причин **Интеграция функций PowerPivot для семейства веб-сайтов** не активна. Выполните следующие действия.  
  
1.  В библиотеке PowerPivot Gallery щелкните **Параметры сайта** в значке шестеренки![Параметры SharePoint](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "параметры SharePoint") или в списке " **домашний** ".  
  
2.  Щелкните **Компоненты семейства веб-сайтов** в разделе **Администрирование семейства веб-сайтов**.  
  
3.  Щелкните **Компоненты коллекции сайтов**.  
  
4.  Убедитесь, что значение **Функции интеграции с PowerPivot для семейств веб-сайтов** равно **Активны**.  
  
 Дополнительные причины этой проблемы см. в разделе [Галерея PowerPivot с красным крестиком для](https://support.microsoft.com/kb/2361559) значков https://support.microsoft.com/kb/2361559) (.  
  
  
