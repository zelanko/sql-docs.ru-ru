---
title: Включение регулятора ресурсов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Resource Governor, enabling
ms.assetid: 4d17af53-cf11-4ce4-aab4-deda94a49836
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0f6afa21780fe5c3aca2da5f584c115cd21d445c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087580"
---
# <a name="enable-resource-governor"></a>Активация регулятора ресурсов
  Регулятор ресурсов отключен по умолчанию. Регулятор ресурсов можно включить с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или Transact-SQL.  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **To enable Resource Governorn, using:**  [Object Explorer](#RGOnObjEx), [Resource Governor Properties](#RGOnProp), [Transact-SQL](#RGOnTSQL)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 В результате включения регулятора ресурсов произойдет следующее.  
  
-   Будет выполнена функция-классификатор для новых соединений, что позволит связать их рабочую нагрузку с определенными группами рабочей нагрузки.  
  
-   Ограничения ресурсов, заданные в конфигурации регулятора ресурсов, будут соблюдены и применены.  
  
-   Запросы, которые существовали до включения регулятора ресурсов, будут испытывать воздействие всех изменений конфигурации, которые были внесены, пока регулятор ресурсов был отключен.  
  
###  <a name="LimitationsRestrictions"></a> ограничения  
 В ходе пользовательской транзакции нельзя использовать инструкцию `ALTER RESOURCE GOVERNOR` для включения регулятора ресурсов.  
  
###  <a name="Permissions"></a> Permissions  
 Для включения регулятора ресурсов требуется разрешение CONTROL SERVER.  
  
##  <a name="RGOnObjEx"></a> Включение регулятора ресурсов с использованием обозревателя объектов  
 **Включение регулятора ресурсов с помощью обозревателя объектов**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните элемент **Resource Governor**правой кнопкой мыши и выберите команду **Включить**.  
  
##  <a name="RGOnProp"></a> Включение регулятора ресурсов с применением свойств регулятора ресурсов  
 **Включение регулятора ресурсов с использованием страницы свойств регулятора ресурсов**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните правой кнопкой мыши элемент **Resource Governor** и выберите пункт **Свойства**, после чего откроется страница **Свойства Resource Governor** .  
  
3.  Установите флажок **Включить регулятор ресурсов** и нажмите кнопку **ОК**.  
  
##  <a name="RGOnTSQL"></a> Включение регулятора ресурсов с применением Transact-SQL  
 **Включение регулятора ресурсов с применением Transact-SQL**  
  
1.  Выполните инструкцию **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере показано включение регулятора ресурсов.  
  
```  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Регулятор ресурсов](resource-governor.md)   
 [Отключение регулятора ресурсов](disable-resource-governor.md)   
 [Пул ресурсов регулятора ресурсов](resource-governor-resource-pool.md)   
 [Группа рабочей нагрузки регулятора ресурсов](resource-governor-workload-group.md)   
 [Функция-классификатор регулятора ресурсов](resource-governor-classifier-function.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
