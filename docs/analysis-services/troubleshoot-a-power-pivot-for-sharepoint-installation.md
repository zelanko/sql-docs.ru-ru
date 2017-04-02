---
title: "Устранение неполадок установки PowerPivot для SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Устранение неполадок установки PowerPivot для SharePoint
  Если вместо ожидаемых страниц и компонентов выдаются ошибки, выполните следующие действия.  
  
-   Откройте заметки о выпуске SharePoint и [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] , чтобы выяснить, какие существуют способы решения известных проблем установки. Заметки о выпуске доступны на установочном носителе или на сайте Майкрософт, с которого было загружено программное обеспечение.  
  
    -   [Заметки о выпуске SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)  
  
-   См. статью [Troubleshooting Installations of Power Pivot (and other add-ins)](http://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx) (Устранение неполадок установки Power Pivot (и других надстроек)) на вики-сайте TechNet.  
  
## Проблемы  
  
### Эскизы в коллекции Power Pivot отображаются в виде красного креста  
 Одной из возможных причин является неактивная **[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] для семейств веб-сайтов** . Выполните следующие действия.  
  
1.  В библиотеке коллекции [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] выберите команду **Настройки веб-сайта** из меню значка с шестеренкой ![Параметры SharePoint](../analysis-services/media/as-sharepoint2013-settings-gear.png "Параметры SharePoint") или списка **Главная**.  
  
2.  Щелкните **Компоненты семейства веб-сайтов** в разделе **Администрирование семейства веб-сайтов**.  
  
3.  Щелкните **Компоненты коллекции сайтов**.  
  
4.  Убедитесь, что параметр **[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] для семейств веб-сайтов** имеет значение **Активно**.  
  
 Сведения о других причинах этой проблемы см. в статье [Power Pivot Gallery shows Red X's for Icons](http://support.microsoft.com/kb/2361559) (В коллекции Power Pivot вместо значков отображаются красные кресты) (http://support.microsoft.com/kb/2361559).  
  
  