---
title: Рекомендации по выполнению программы, не - прочим наборам элементов сбора на том же экземпляре SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ca7ee9b3-ef9a-4ba4-83d0-9ee9f80dab27
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5f2e77a1c4be8462fc509b1a2437329f026d5987
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63187171"
---
# <a name="considerations-for-running-utility-and-non-utility-collection-sets-on-the-same-instance-of-sql-server"></a>Замечания по выполнению программы, не относящиеся к прочим наборам элементов сбора на том же экземпляре SQL Server
  Набор элементов сбора служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживается параллельно с наборами элементов сбора, не касающимися служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Таким образом, управляемый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно наблюдать по другим наборам элементов сбора, поскольку он является элементом служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Однако при регистрации экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] все функции сбора данных, не относящиеся к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должны быть отключены.  
  
 После регистрации экземпляра в UCP наборы элементов сбора, не относящиеся к служебной программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , можно будет перезапустить. Следует, однако, отметить, что все наборы элементов сбора, находящиеся в управляемом экземпляре, передают свои данные в хранилище данных управления для программы (UMDW).  
  
 Чтобы наборы элементов сбора служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работали параллельно с наборами элементов сбора, не относящимися к служебной программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо учитывать следующее.  
  
-   Поддерживается параллельная работа наборов элементов сбора.  
  
-   Существующие сборщики данных необходимо отключать при регистрации экземпляров в программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Чтобы передать требования проверки, перед созданием UCP, а также перед регистрацией экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо запустить следующие хранимые процедуры:  
  
    ```  
    exec msdb.dbo.sp_syscollector_set_warehouse_database_name NULL  
    exec msdb.dbo.sp_syscollector_set_warehouse_instance_name NULL  
    ```  
  
     Если не запустить эти хранимые процедуры перед запуском мастера создания UCP или мастера добавления управляемого экземпляра, то операция завершится неудачей.  
  
-   Для всех наборов элементов сбора в управляемом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо использовать хранилище UMDW (sysutility_mdw) служебной программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md)   
 [Настройка хранилища данных точки управления служебной программы (служебная программа SQL Server)](configure-your-utility-control-point-data-warehouse-sql-server-utility.md)  
  
  
