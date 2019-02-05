---
title: Удаление пула ресурсов | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool delete
- resource pools [SQL Server], delete
ms.assetid: 3bdd348b-6582-4ffa-80ef-d49e50596ce5
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 94a559d7486263d1edf50383e3a8af39fe93689d
ms.sourcegitcommit: cebfa2610ea36e3c5ad510c214590035ecb499c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/04/2019
ms.locfileid: "55689807"
---
# <a name="delete-a-resource-pool"></a>Удаление пула ресурсов
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Регулятор ресурсов можно удалить в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью Transact-SQL.  
  
-   **Перед началом работы**  [ограничения](#LimitationsRestrictions), [разрешения](#Permissions)  
  
-   **Удаление пула ресурсов с использованием:** [среды SQL Server Management Studio](#DelRPSSMS), [Transact-SQL](#DelRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 Пул ресурсов нельзя удалить, если он содержит группы рабочей нагрузки.  
  
###  <a name="LimitationsRestrictions"></a> ограничения  
 Нельзя удалять пулы регулятора ресурсов по умолчанию или внутренние пулы ресурсов. Пул ресурсов нельзя удалить, если он содержит группы рабочей нагрузки. Дополнительные сведения см. в статье [Delete a Workload Group](../../relational-databases/resource-governor/delete-a-workload-group.md).  
  
###  <a name="Permissions"></a> Permissions  
 Для удаления пула ресурсов требуется разрешение CONTROL SERVER.  
  
##  <a name="DelRPSSMS"></a> Удаление пула ресурсов с помощью обозревателя объектов  
 **Удаление пула ресурсов в среде SQL Server Management Studio**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните правой кнопкой мыши пул ресурсов, который необходимо удалить, а затем нажмите кнопку **Удалить**.  
  
3.  В окне **Удаление объекта** этот пул ресурсов будет указан в списке **Объект для удаления** . Чтобы удалить пул ресурсов, нажмите кнопку **ОК**.  
  
    > [!NOTE]  
    >  Если удаляемый пул ресурсов содержит группы рабочей нагрузки, удалить его не удастся.  
  
##  <a name="DelRPTSQL"></a> Удаление пула ресурсов с помощью Transact-SQL  
 **Удаление пула ресурсов с помощью Transact-SQL**  
  
1.  Выполните инструкцию **DROP RESOURCE POOL** или **DROP EXTERNAL RESOURCE POOL** , указав имя пула ресурсов, который необходимо удалить.  
  
2.  Выполните инструкцию **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере удаляется группа рабочей нагрузки с именем `poolAdhoc`.  
  
```  
DROP RESOURCE POOL poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)   
 [Пул ресурсов регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Создание пула ресурсов](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [Изменение параметров пула ресурсов](../../relational-databases/resource-governor/change-resource-pool-settings.md)   
 [Группа рабочей нагрузки регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Функция-классификатор регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [DROP WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [DROP RESOURCE POOL (Transact-SQL)](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [DROP EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)   
 [CREATE EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [ALTER EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)  
  
  
