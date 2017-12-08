---
title: "Развертывание PowerPivot и Power View - многоуровневой ферме SharePoint 2016 | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: instances
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e36a632-0750-4247-92b6-1fe38c7a4ce2
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 290c8d09fbb59ec8b7c6db580946fa7ee6f45806
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="deploy-powerpivot-and-power-view---multi-tier-sharepoint-2016-farm"></a>Развертывание PowerPivot и Power View - многоуровневой ферме SharePoint 2016
  **Сводка.** Этот технический документ предоставляет администраторам и архитекторам SharePoint подробные пошаговые инструкции по развертыванию и настройке демонстрационной среды Microsoft BI на ферме SharePoint с несколькими серверами на основании предварительных выпусков SharePoint Server 2016, Office Online Server и стека SQL Server 2016 BI для SharePoint 2016. После краткого описания важных изменений в архитектуре и соответствующих системных зависимостей в нем изложены требования к программному обеспечению и конфигурации, а также рекомендуемый путь развертывания, позволяющий включить и проверить функциональные возможности бизнес-аналитики в три основных этапа. В этом техническом документе также затрагиваются известные проблемы, которые существуют в бета-версии 2 SharePoint Server 2016, предварительной версии Office Online Server и выпусках SQL Server 2016 CTP 3.1, предлагая соответствующие действия для их решения. Эти действия больше не потребуются в окончательных версиях данных продуктов. При развертывании версий RTM проверьте наличие обновленной версии этого документа.  
  
 **Авторы:**Кэй Анкрот (Kay Unkroth), Джейсон Хаак (Jason Haak)  
  
 **Технические редакторы:** Адам Сакстон (Adam Saxton), Энн Зорнер (Anne Zorner), Крейг Гайер (Craig Guyer), Фрэнк Вейгель (Frank Weigel), Грегори Аппель (Gregory Appel), Хайди Стин (Heidi Steen), Каспер де Йонг (Kasper de Jonge), Кирк Старк (Kirk Stark), Клаус Собель (Klaus Sobel), Майк Пламли (Mike Plumley), Майк Таджизаде (Mike Taghizadeh), Патрик Вилер (Patrick Wheeler), Риккардо Мути (Riccardo Muti), Стив Хорд (Steve Hord)  
  
 **Дата публикации:**январь 2016 г.  
  
 **Применимо для следующих объектов:** SQL Server 2016, CTP-версия 3.1, предварительная версия SharePoint 2016, предварительная версия Office Online Server  
  
 Чтобы ознакомиться с документом, загрузите документ Word [Развертывание SQL Server 2016 PowerPivot и Power View в многоуровневой ферме SharePoint 2016](http://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Deploying%20SQL%20Server%202016%20PowerPivot%20and%20Power%20View%20in%20a%20Multi-Tier%20SharePoint%202016%20Farm.docx) .  
  
  
