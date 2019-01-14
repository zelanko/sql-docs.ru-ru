---
title: Создание пула ресурсов | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- resource pools [SQL Server], create
- Resource Governor, resource pool create
ms.assetid: 44dd0567-a4c8-4c72-89ff-e76f6ddef344
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 93add4b3d9ed4ff71a57845443813c323861145b
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2018
ms.locfileid: "53379682"
---
# <a name="create-a-resource-pool"></a>Создание пула ресурсов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Можно создать пул ресурсов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]. Общие сведения о пулах ресурсов см. в статье [Resource Governor Resource Pool](../../relational-databases/resource-governor/resource-governor-resource-pool.md).  
  
-   **Перед началом работы**  [ограничения](#LimitationsRestrictions), [разрешения](#Permissions)  
  
-   **Создание пула ресурсов с использованием:**  [среды SQL Server Management Studio](#CreRPProp), [Transact-SQL](#CreRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="LimitationsRestrictions"></a> ограничения  
 Максимальный процент использования ЦП должен быть больше минимального или равен ему. Максимальный процент использования памяти должен быть больше минимального или равен ему.  
  
 Сумма значений минимальных процентов использования ЦП и минимальных процентов использования памяти для всех пулов ресурсов не должна превышать 100.  
  
###  <a name="Permissions"></a> Permissions  
 Для создания пула ресурсов требуется разрешение CONTROL SERVER.  
  
##  <a name="CreRPProp"></a> Создание пула ресурсов в среде SQL Server Management Studio  
 **Создание пула ресурсов с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните **Регулятор ресурсов**правой кнопкой мыши и выберите команду **Свойства**.  
  
3.  В сетке **Пулы ресурсов** щелкните первый столбец в пустой строке. Этот столбец отмечен звездочкой (*).  
  
4.  Дважды щелкните пустую ячейку в столбце **Имя** . Введите имя, которое следует присвоить пулу ресурсов.  
  
5.  Щелкните или дважды щелкните все прочие ячейки в строке, в которые необходимо внести изменения, и введите новые значения.  
  
6.  Чтобы сохранить изменения, нажмите кнопку **ОК**.  
  
##  <a name="CreRPTSQL"></a> Создание пула ресурсов с помощью Transact-SQL  
 **Создание пула ресурсов с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
1.  Выполните инструкцию [CREATE RESOURCE POOL](../../t-sql/statements/create-resource-pool-transact-sql.md) или [CREATE EXTERNAL RESOURCE POOL](../../t-sql/statements/create-external-resource-pool-transact-sql.md) , указав значения свойств, которые необходимо установить.  
  
2.  Выполните инструкцию **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере создается пул ресурсов с именем `poolAdhoc`.  
  
```  
CREATE RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 20);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)   
 [Активация регулятора ресурсов](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [Resource Governor Resource Pool](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Изменение параметров пула ресурсов](../../relational-databases/resource-governor/change-resource-pool-settings.md)   
 [Удаление пула ресурсов](../../relational-databases/resource-governor/delete-a-resource-pool.md)   
 [Настройка регулятора ресурсов с помощью шаблона](../../relational-databases/resource-governor/configure-resource-governor-using-a-template.md)   
 [Группа рабочей нагрузки регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Функция-классификатор регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [CREATE RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [CREATE EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [ALTER EXTERNAL RESOURCE POOL (Transact-SQL)](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)  
  
  
