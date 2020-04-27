---
title: Изменение параметров пула ресурсов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool alter
- resource pools [SQL Server], alter
ms.assetid: 49438285-a011-4dac-bd4f-f35cd90fda61
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6392c8211e073183b68d2d04e9c949317d6a33a9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "68198943"
---
# <a name="change-resource-pool-settings"></a>Изменение параметров пула ресурсов
  Можно изменить параметры пула ресурсов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Перед началом работы**  [ограничения](#LimitationsRestrictions), [разрешения](#Permissions)  
  
-   **Изменение параметров для пула ресурсов с использованием:**  [среды SQL Server Management Studio](#ChgRPProp), [Transact-SQL](#ChgRPTSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Ограничения  
 Максимальный процент использования ЦП должен быть больше минимального или равен ему. Максимальный процент использования памяти должен быть больше минимального или равен ему.  
  
 Сумма значений минимальных процентов использования ЦП и минимальных процентов использования памяти для всех пулов ресурсов не должна превышать 100.  
  
###  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для изменения параметров пула ресурсов требуется разрешение CONTROL SERVER.  
  
##  <a name="change-resource-pool-settings-using-sql-server-management-studio"></a><a name="ChgRPProp"></a> Изменение параметров пула ресурсов в среде SQL Server Management Studio  
 **Изменение параметров пула ресурсов с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Пулы ресурсов**.  
  
2.  Щелкните правой кнопкой мыши пул ресурсов, подлежащий изменению, и выберите пункт **Свойства**.  
  
3.  На странице **Свойства регулятора ресурсов** выберите строку, относящуюся к пулу ресурсов, в сетке **Пулы ресурсов** , если она не выделена автоматически.  
  
4.  Щелкните или дважды щелкните ячейки в строке, подлежащие изменению, и введите новые значения.  
  
5.  Чтобы сохранить изменения, нажмите кнопку **ОК**.  
  
##  <a name="change-resource-pool-settings-using-transact-sql"></a><a name="ChgRPTSQL"></a> Изменение параметров пула ресурсов с помощью Transact-SQL  
 **Изменение параметров пула ресурсов с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
1.  Выполните инструкцию `ALTER RESOURCE POOL`, указав значения свойств, которые необходимо изменить.  
  
2.  Выполните инструкцию **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере показано изменение значения параметра максимального процента использования ЦП для пула ресурсов с именем `poolAdhoc`.  
  
```  
ALTER RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 25);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [регулятор ресурсов](resource-governor.md)   
 [Активация регулятора ресурсов](enable-resource-governor.md)   
 [Создание пула ресурсов](create-a-resource-pool.md)   
 [Удаление пула ресурсов](delete-a-resource-pool.md)   
 [Группа рабочей нагрузки регулятора ресурсов](resource-governor-workload-group.md)   
 [Функция-классификатор регулятора ресурсов](resource-governor-classifier-function.md)   
 [ALTER RESOURCE POOL (Transact-SQL)](/sql/t-sql/statements/alter-resource-pool-transact-sql)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
