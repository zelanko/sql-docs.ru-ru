---
title: Параметры сортировки и типы данных интеграции со средой CLR | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data types [CLR integration]
- parameter collation [CLR integration]
- collations [CLR integration]
ms.assetid: 6ebaed8e-2e2b-4f6d-bf4b-bc25452de441
caps.latest.revision: 38
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 617c8dea3844f1b2ae980775949d4d1c793b4f1a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="collation-and-clr-integration-data-types"></a>Параметры сортировки и типы данных интеграции со средой CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]объект **CompareInfo** обрабатывает параметры сортировки. Строковые API-интерфейсы платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] используют свойство **CompareInfo** , связанное с объектом **CultureInfo** текущего потока, для сравнения строк. Настройка по умолчанию свойства **CultureInfo** основана на параметрах локали [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows для компьютера, на котором выполняется [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Она определяет семантику сравнения по умолчанию для сравнения значений типа **CultureInfo** , если свойство **System.String** не задано явно. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не изменяет явно **CompareInfo** свойство с параметрами сортировки базы данных или сервера. При необходимости пользователи должны самостоятельно устанавливать свойство **CompareInfo** в своих программах.  
  
## <a name="parameter-collation"></a>Параметр с параметрами сортировки  
 При создании программы CLR, если параметр метода CLR, связанного с программой, имеет тип **SQLString**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает экземпляр параметра с параметрами сортировки по умолчанию базы данных, содержащей вызывающую программу. Если параметр имеет тип, отличный от **SqlType** (например, **String** , а не **SQLString**), сведения о параметрах сортировки из базы данных с этим параметром не связываются.  
  
## <a name="see-also"></a>См. также  
 [Типы данных SQL Server в .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
