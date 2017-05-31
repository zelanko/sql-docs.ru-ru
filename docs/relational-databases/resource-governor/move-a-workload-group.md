---
title: "Перемещение группы рабочей нагрузки | Документация Майкрософт"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.rg.properties_moveworkloadgroup.f1
helpviewer_keywords:
- workload groups [SQL Server], move
- Resource Governor, workload group move
ms.assetid: f2068636-6e53-486a-a6fc-c12de2a38424
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2e74236a254493b554c34b5f7c729e8cb91868a0
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="move-a-workload-group"></a>Перемещение группы рабочей нагрузки
  Группу рабочей нагрузки регулятора ресурсов можно переместить в другой пул ресурсов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью Transact-SQL.  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **To move a workload group, using:**  [SQL Server Management Studio](#MoveWGSSMS), [Transact-SQL](#MoveWGTSQL)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 Перемещение группы рабочей нагрузки становится невозможным, если имеется ожидающая выполнения операция настройки регулятора ресурсов.  
  
###  <a name="LimitationsRestrictions"></a> ограничения  
 Перемещение группы рабочей нагрузки становится невозможным, если имеется ожидающая выполнения операция настройки регулятора ресурсов. Чтобы выяснить, находится ли конфигурация в состоянии ожидания, выполните запрос к динамическому административному представлению [sys.dm_resource_governor_configuration (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql.md), получив текущее состояние is_configuration_pending.  
  
###  <a name="Permissions"></a> Разрешения  
 Для перемещения группы рабочей нагрузки требуется разрешение CONTROL SERVER.  
  
##  <a name="MoveWGSSMS"></a> Перемещение группы рабочей нагрузки с использованием среды SQL Server Management Studio  
 **Перемещение группы рабочей нагрузки в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]**  
  
1.  В обозревателе объектов рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните правой кнопкой мыши **Регулятор ресурсов** и выберите пункт **Свойства**, после чего откроется страница **Свойства регулятора ресурсов** .  
  
3.  В окне **Пулы ресурсов** щелкните пул ресурсов, содержащий группу рабочей нагрузки, которая должна быть перемещена. Теперь в окне **Группы рабочей нагрузки** появятся списки групп рабочей нагрузки в этом пуле ресурсов.  
  
4.  Чтобы переместить группу рабочей нагрузки, выделите соответствующую ей строку, щелкните правой кнопкой мыши указатель в начале строки и выберите команду **Переместить** , укажите новое расположение и нажмите кнопку **Переместить**. Будет отображено окно **Перемещение группы рабочей нагрузки** .  
  
5.  Доступные пулы ресурсов отображаются в окне. Щелкните имя пула ресурсов, в который нужно перенести группу рабочей нагрузки, а затем нажмите кнопку **ОК** , чтобы выполнить это действие.  
  
6.  Действие не завершено, пока не будет нажата кнопка **ОК**. При нажатии кнопки **ОК**выполняется инструкция ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
7.  Если операция создания или изменения конфигурации пула ресурсов или группы рабочей нагрузки завершилась неуспешно, под заголовком страницы свойств будет отображено сводное сообщение об ошибке. Чтобы просмотреть подробное сообщение об ошибке, щелкните стрелку вниз рядом с ним.  
  
##  <a name="MoveWGTSQL"></a> Перемещение группы рабочей нагрузки с использованием Transact-SQL  
 **Перемещение группы рабочей нагрузки с использованием Transact-SQL**  
  
1.  Выполните инструкцию **ALTER WORKLOAD GROUP** , указав имя группы рабочей нагрузки для перемещения, и пул ресурсов, в который она должна быть перемещена.  
  
2.  Выполните инструкцию **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере показано, как переместить группу рабочей нагрузки с именем `groupAdhoc` в пул ресурсов по умолчанию.  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
USING [default];  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)   
 [Активация регулятора ресурсов](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [Создание пула ресурсов](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [Создание группы рабочей нагрузки](../../relational-databases/resource-governor/create-a-workload-group.md)   
 [ALTER WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
