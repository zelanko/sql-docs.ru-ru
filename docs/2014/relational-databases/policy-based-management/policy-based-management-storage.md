---
title: Хранение политик управления на основе политик | Документация Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, storage
ms.assetid: d0cbf214-fc2e-4917-8d31-1d71c9ffa61d
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b741f03de6a1c36678752b1d0f926479dec91c0b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098623"
---
# <a name="policy-based-management-storage"></a>Хранение политик управления на основе политик
  Политики хранятся в базе данных msdb. После изменения политики или условия необходимо выполнить резервное копирование базы данных msdb. Дополнительные сведения см. в статье [Резервное копирование и восстановление системных баз данных (SQL Server)](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
## <a name="storing-policies"></a>Политики хранения  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] предусмотрены политики, которые можно использовать для наблюдения за экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию эти политики не устанавливаются на [!INCLUDE[ssDE](../../includes/ssde-md.md)], однако их можно импортировать из места установки по умолчанию C:\Program Files (x86) \Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033.  
  
 Можно создавать политики напрямую, при помощи меню **Файл/Создать** , и сохранять их в файл. Это позволяет создавать политики при отсутствии подключения к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Журнал политик, вычисленных в текущем экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , поддерживается в системных таблицах базы данных msdb. Журнал политик, примененных к другим экземплярам компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , к службам [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , не сохраняется.  
  
  