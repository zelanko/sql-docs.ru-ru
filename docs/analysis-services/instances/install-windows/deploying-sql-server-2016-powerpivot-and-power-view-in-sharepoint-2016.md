---
title: "Развертывание SQL Server 2016 PowerPivot и Power View в SharePoint 2016 | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d0a9834-db91-403f-847c-79a8f49fc916
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ae98c7bb08848dd1d4b914ebfbaef71f40b22873
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="deploying-sql-server-2016-powerpivot-and-power-view-in-sharepoint-2016"></a>Развертывание SQL Server 2016 PowerPivot и Power View в SharePoint 2016
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]**Сводка:** этот технический документ предоставляет SharePoint Администраторы и архитекторы подробные пошаговые инструкции по развертыванию и настройке демонстрационной среды Microsoft BI основании предварительных выпусков SharePoint Server 2016, office Online Server и SQL Server 2016 BI стека для SharePoint 2016. После краткого описания важных изменений в архитектуре и соответствующих системных зависимостей в нем изложены требования к программному обеспечению и конфигурации, а также рекомендуемый путь развертывания, позволяющий включить и проверить функциональные возможности бизнес-аналитики в три основных этапа. В этом техническом документе также затрагиваются известные проблемы, которые существуют в бета-версии 2 SharePoint Server 2016, предварительной версии Office Online Server и выпусках SQL Server 2016 CTP 3.1, предлагая соответствующие действия для их решения. Эти действия больше не потребуются в окончательных версиях данных продуктов. При развертывании версий RTM проверьте наличие обновленной версии этого документа.  
  
 **Автор:** Кэй Анкрот (Kay Unkroth)  
  
 **Технические редакторы:** Адам Сакстон (Adam Saxton), Энн Зорнер (Anne Zorner), Крейг Гайер (Craig Guyer), Фрэнк Вейгель (Frank Weigel), Грегори Аппель (Gregory Appel), Хайди Стин (Heidi Steen), Джейсон Хаак (Jason Haak), Каспер де Йонг (Kasper de Jonge), Кирк Старк (Kirk Stark), Клаус Собель (Klaus Sobel), Майк Пламли (Mike Plumley), Майк Таджизаде (Mike Taghizadeh), Патрик Вилер (Patrick Wheeler), Риккардо Мути (Riccardo Muti), Стив Хорд (Steve Hord)  
  
 **Опубликовано:** декабрь 2015 г.  
  
 **Применимо для следующих объектов:** SQL Server 2016, CTP-версия 3.1, предварительная версия SharePoint 2016, предварительная версия Office Online Server  
  
 Чтобы прочитать этот документ, скачайте документ Word [Развертывание SQL Server 2016 PowerPivot и Power View в SharePoint 2016](http://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Deploying%20SQL%20Server%202016%20PowerPivot%20and%20Power%20View%20in%20SharePoint%202016.docx) .  
  
  
