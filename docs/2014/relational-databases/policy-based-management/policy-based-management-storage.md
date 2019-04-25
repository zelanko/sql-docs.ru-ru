---
title: Хранение политик управления на основе политик | Документация Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, storage
ms.assetid: d0cbf214-fc2e-4917-8d31-1d71c9ffa61d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e1eab3ad745a83a8a55545570e020c1f1af732ad
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62628874"
---
# <a name="policy-based-management-storage"></a>Хранение политик управления на основе политик
  Политики хранятся в базе данных msdb. После изменения политики или условия необходимо выполнить резервное копирование базы данных msdb. Дополнительные сведения см. в статье [Резервное копирование и восстановление системных баз данных (SQL Server)](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
## <a name="storing-policies"></a>Политики хранения  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] предусмотрены политики, которые можно использовать для наблюдения за экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию эти политики не устанавливаются на [!INCLUDE[ssDE](../../includes/ssde-md.md)], однако их можно импортировать из места установки по умолчанию C:\Program Files (x86) \Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033.  
  
 Можно создавать политики напрямую, при помощи меню **Файл/Создать** , и сохранять их в файл. Это позволяет создавать политики при отсутствии подключения к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Журнал политик, вычисленных в текущем экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , поддерживается в системных таблицах базы данных msdb. Журнал политик, примененных к другим экземплярам компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , к службам [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , не сохраняется.  
  
  
