---
title: "Хранение политик управления на основе политик | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, storage
ms.assetid: d0cbf214-fc2e-4917-8d31-1d71c9ffa61d
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0426d583d1ada35c7ad3e36d4fe1a621e9754360
ms.lasthandoff: 04/11/2017

---
# <a name="policy-based-management-storage"></a>Хранение политик управления на основе политик
  Политики хранятся в базе данных msdb. После изменения политики или условия необходимо выполнить резервное копирование базы данных msdb. Дополнительные сведения см. в разделе [Резервное копирование и восстановление системных баз данных (SQL Server)](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
## <a name="storing-policies"></a>Политики хранения  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] предусмотрены политики, которые можно использовать для наблюдения за экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию эти политики не устанавливаются в компоненте [!INCLUDE[ssDE](../../includes/ssde-md.md)], однако их можно импортировать из места установки по умолчанию — каталога C:\Program Files\Microsoft SQL Server\130\Tools\Policies\DatabaseEngine\1033.  
  
 Можно создавать политики напрямую, при помощи меню **Файл/Создать** , и сохранять их в файл. Это позволяет создавать политики при отсутствии подключения к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Журнал политик, вычисленных в текущем экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , поддерживается в системных таблицах базы данных msdb. Журнал политик, примененных к другим экземплярам компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , к службам [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , не сохраняется.  
  
  
