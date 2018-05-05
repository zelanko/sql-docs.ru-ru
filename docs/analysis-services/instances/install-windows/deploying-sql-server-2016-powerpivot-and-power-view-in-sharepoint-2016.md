---
title: Развертывание SQL Server 2016 PowerPivot и Power View в SharePoint 2016 | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ppvt-sharepoint
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5218e3388fa33a38f0574f9f206118b85deaf50e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="deploying-sql-server-2016-powerpivot-and-power-view-in-sharepoint-2016"></a>Развертывание SQL Server 2016 PowerPivot и Power View в SharePoint 2016
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  **Сводка.** Этот технический документ предоставляет администраторам и архитекторам SharePoint подробные пошаговые инструкции по развертыванию и настройке демонстрационной среды Microsoft BI на основе предварительных выпусков SharePoint Server 2016, Office Online Server и стека SQL Server 2016 BI для SharePoint 2016. После краткого описания важных изменений в архитектуре и соответствующих системных зависимостей в нем изложены требования к программному обеспечению и конфигурации, а также рекомендуемый путь развертывания, позволяющий включить и проверить функциональные возможности бизнес-аналитики в три основных этапа. В этом техническом документе также затрагиваются известные проблемы, которые существуют в бета-версии 2 SharePoint Server 2016, предварительной версии Office Online Server и выпусках SQL Server 2016 CTP 3.1, предлагая соответствующие действия для их решения. Эти действия больше не потребуются в окончательных версиях данных продуктов. При развертывании версий RTM проверьте наличие обновленной версии этого документа.  
  
 **Автор:** Кэй Анкрот (Kay Unkroth)  
  
 **Технические редакторы:** Адам Сакстон (Adam Saxton), Энн Зорнер (Anne Zorner), Крейг Гайер (Craig Guyer), Фрэнк Вейгель (Frank Weigel), Грегори Аппель (Gregory Appel), Хайди Стин (Heidi Steen), Джейсон Хаак (Jason Haak), Каспер де Йонг (Kasper de Jonge), Кирк Старк (Kirk Stark), Клаус Собель (Klaus Sobel), Майк Пламли (Mike Plumley), Майк Таджизаде (Mike Taghizadeh), Патрик Вилер (Patrick Wheeler), Риккардо Мути (Riccardo Muti), Стив Хорд (Steve Hord)  
  
 **Опубликовано:** декабрь 2015 г.  
  
 **Применимо для следующих объектов:** SQL Server 2016, CTP-версия 3.1, предварительная версия SharePoint 2016, предварительная версия Office Online Server  
  
 Чтобы прочитать этот документ, скачайте документ Word [Развертывание SQL Server 2016 PowerPivot и Power View в SharePoint 2016](http://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Deploying%20SQL%20Server%202016%20PowerPivot%20and%20Power%20View%20in%20SharePoint%202016.docx) .  
  
  
