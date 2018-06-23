---
title: Страница выбора баз данных (группы доступности мастер добавления базы данных мастер) | Документы Microsoft
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.adddatabasewizard.selectdatabases.f1
- sql12.swb.newagwizard.selectdatabases.f1
ms.assetid: 929c5e15-d087-438d-b1f2-aa97c5f8bff8
caps.latest.revision: 12
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: 304ce826a45debaf4d18a63e9d68061ef393705b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189126"
---
# <a name="select-databases-page-new-availability-group-wizard-add-database-wizard"></a>Страница выбора баз данных (группы доступности мастер добавления базы данных мастер)
  В этом разделе описаны параметры на странице **Выбор баз данных** . Эта тема относится к [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] и [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
##  <a name="PageOptions"></a> Выбор параметров баз данных  
 В сетке **Пользовательские базы данных в этом экземпляре SQL Server** перечислены все локальные пользовательские базы данных. Существуют следующие столбцы.  
  
 **Название**  
 Отображает имя локальной пользовательской базы данных.  
  
 **Размер**  
 Отображает размер базы данных, если он доступен мастеру.  
  
 **Состояние**  
 Отображает гиперссылку, текст которой показывает, отвечает ли база данных требованиям по добавлению в группу доступности. Если состояние — «**Отвечает требованиям**», то базу данных можно добавить в группу доступности. Если база данных не отвечает всем требованиям, то по гиперссылке **Состояние** приводится краткое объяснение причин, по которым база данных не подходит. Для получения дополнительных сведений щелкните гиперссылку.  
  
 Можно выйти из мастера на странице **Выбор базы данных** на время действий, позволяющих сделать так, чтобы база данных отвечала требованиям. По возвращении на страницу **Выбор баз данных** нажмите кнопку **Обновить** для обновления сетки.  
  
 **Обновить**  
 Щелкните, чтобы обновить сетку. Это следует сделать после того, как были приняты действия по приведению базы данных в соответствие требованиям.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Использование диалогового окна "Создание группы доступности" (среда SQL Server Management Studio)](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Использование мастера добавления базы данных в группу доступности (среда SQL Server Management Studio)](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  