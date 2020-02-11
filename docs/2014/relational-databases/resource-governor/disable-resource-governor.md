---
title: Отключение регулятора ресурсов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, disabling
ms.assetid: 2c2d2db0-34a5-4f50-b783-17693e3ce3f1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 75feaf114355c3a23abad6ec23be9011e0de5e06
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63209716"
---
# <a name="disable-resource-governor"></a>Отключение регулятора ресурсов
  Регулятор ресурсов можно отключить в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью Transact-SQL.  
  
-   **Перед началом работы**  [ограничения](#LimitationsRestrictions), [разрешения](#Permissions)  
  
-   **Отключение Resource Governor с использованием:**  [обозревателя объектов](#RGOffObjEx), [свойств Resource Governor](#RGOffProp), [Transact-SQL](#RGOffTSQL)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 В результате отключения регулятора ресурсов происходит следующее.  
  
-   Функция-классификатор не выполняется.  
  
-   Все новые соединения в результате классификации автоматически попадают в группу рабочей нагрузки по умолчанию.  
  
-   Инициированные системой запросы попадают во внутреннюю группу рабочей нагрузки.  
  
-   Все существующие параметры групп рабочей нагрузки и пулов ресурсов сбрасываются в значения по умолчанию. В этом случае при достижении ограничений не возникает никаких событий.  
  
-   Обычное наблюдение за системой не затрагивается.  
  
-   Изменения конфигурации можно вносить, но эти изменения не вступят в силу, пока не будет включен регулятор ресурсов.  
  
-   После перезапуска SQL Server регулятор ресурсов не будет загружать конфигурацию, а вместо этого будет иметь только применяемые по умолчанию внутренние группы рабочей нагрузки и пулы ресурсов.  
  
###  <a name="LimitationsRestrictions"></a> Ограничения  
 В пользовательской транзакции регулятор ресурсов нельзя отключить с помощью инструкции `ALTER RESOURCE GOVERNOR`.  
  
###  <a name="Permissions"></a> Permissions  
 Для отключения регулятора ресурсов требуется разрешение CONTROL SERVER.  
  
##  <a name="RGOffObjEx"></a> Отключение регулятора ресурсов с помощью обозревателя объектов  
 **Отключение регулятора ресурсов с помощью обозревателя объектов**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните элемент **Resource Governor**правой кнопкой мыши и выберите команду **Отключить**.  
  
##  <a name="RGOffProp"></a> Отключение регулятора ресурсов с помощью свойств регулятора ресурсов  
 **Отключение регулятора ресурсов с помощью страницы «Свойства регулятора ресурсов»**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните правой кнопкой мыши **Регулятор ресурсов** и выберите пункт **Свойства**, после чего откроется страница **Свойства регулятора ресурсов** .  
  
3.  Щелкните флажок **Включить регулятор ресурсов** , убедитесь в том, что этот флажок не выбран, и нажмите кнопку **ОК**.  
  
##  <a name="RGOffTSQL"></a> Отключение регулятора ресурсов с помощью Transact-SQL  
 **Отключение регулятора ресурсов с помощью Transact-SQL**  
  
1.  Выполните инструкцию **ALTER RESOURCE GOVERNOR DISABLE** .  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере показано включение регулятора ресурсов.  
  
```  
ALTER RESOURCE GOVERNOR DISABLE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [регулятор ресурсов](resource-governor.md)   
 [Активация регулятора ресурсов](enable-resource-governor.md)   
 [Пул ресурсов регулятора ресурсов](resource-governor-resource-pool.md)   
 [Группа рабочей нагрузки регулятора ресурсов](resource-governor-workload-group.md)   
 [Функция-классификатор регулятора ресурсов](resource-governor-classifier-function.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
