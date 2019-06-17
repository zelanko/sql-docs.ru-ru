---
title: Развертывание PowerPivot и Power View - многоуровневой ферме SharePoint 2016 | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ee295f354de5479f5af8add49cb7aee2985a687f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63054616"
---
# <a name="deploy-powerpivot-and-power-view---multi-tier-sharepoint-2016-farm"></a>Развертывание PowerPivot и Power View - многоуровневой ферме SharePoint 2016
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  **Сводка** Сводка. Этот технический документ предоставляет администраторам SharePoint и архитекторы подробные пошаговые инструкции по развертыванию и настройке демонстрационной среды Microsoft BI на ферме SharePoint с несколькими серверами, в зависимости от предварительных выпусков SharePoint Server 2016, office Online Server и SQL Server 2016 BI стека для SharePoint 2016. После краткого описания важных изменений в архитектуре и соответствующих системных зависимостей в нем изложены требования к программному обеспечению и конфигурации, а также рекомендуемый путь развертывания, позволяющий включить и проверить функциональные возможности бизнес-аналитики в три основных этапа. В этом техническом документе также затрагиваются известные проблемы, которые существуют в бета-версии 2 SharePoint Server 2016, предварительной версии Office Online Server и выпусках SQL Server 2016 CTP 3.1, предлагая соответствующие действия для их решения. Эти действия больше не потребуются в окончательных версиях данных продуктов. При развертывании версий RTM проверьте наличие обновленной версии этого документа.  
  
 **Авторы:** Кэй Анкрот (Kay Unkroth), Джейсон Хаак (Jason Haak)  
  
 **Технические редакторы:** ADAM Saxton, Anne Zorner, Craig Guyer, Фрэнк Weigel, Грегори Аппель, Хайди Стин, Каспер де Jonge, Kirk Stark, Sobel Клаус, Mike Plumley, Mike Taghizadeh, Patrick Wheeler, риккардо Мути, Steve Hord  
  
 **Дата публикации:** январь 2016 г.  
  
 **Применимо к:** Предварительная версия SQL Server 2016 CTP 3.1, предварительная версия SharePoint 2016, Office Online Server  
  
 Чтобы ознакомиться с документом, загрузите документ Word [Развертывание SQL Server 2016 PowerPivot и Power View в многоуровневой ферме SharePoint 2016](http://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Deploying%20SQL%20Server%202016%20PowerPivot%20and%20Power%20View%20in%20a%20Multi-Tier%20SharePoint%202016%20Farm.docx) .  
  
  
