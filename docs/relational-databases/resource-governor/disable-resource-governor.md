---
title: Отключение регулятора ресурсов | Документация Майкрософт
description: Сведения о том, как отключить Resource Governor с помощью SQL Server Management Studio или Transact-SQL. Необходимо иметь разрешение CONTROL SERVER.
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, disabling
ms.assetid: 2c2d2db0-34a5-4f50-b783-17693e3ce3f1
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: bc4aea056c466aaf7cbacc8a6871fac488d31ef7
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2020
ms.locfileid: "86457902"
---
# <a name="disable-resource-governor"></a>Отключение регулятора ресурсов
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Регулятор ресурсов можно отключить в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью Transact-SQL.  
  
-   **Перед началом работы**  [ограничения](#LimitationsRestrictions), [разрешения](#Permissions)  
  
-   **Отключение Resource Governor с использованием:**  [обозревателя объектов](#RGOffObjEx), [свойств Resource Governor](#RGOffProp), [Transact-SQL](#RGOffTSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
 В результате отключения регулятора ресурсов происходит следующее.  
  
-   Функция-классификатор не выполняется.  
  
-   Все новые соединения в результате классификации автоматически попадают в группу рабочей нагрузки по умолчанию.  
  
-   Инициированные системой запросы попадают во внутреннюю группу рабочей нагрузки.  
  
-   Все существующие параметры групп рабочей нагрузки и пулов ресурсов сбрасываются в значения по умолчанию. В этом случае при достижении ограничений не возникает никаких событий.  
  
-   Обычное наблюдение за системой не затрагивается.  
  
-   Изменения конфигурации можно вносить, но эти изменения не вступят в силу, пока не будет включен регулятор ресурсов.  
  
-   После перезапуска SQL Server регулятор ресурсов не будет загружать конфигурацию, а вместо этого будет иметь только применяемые по умолчанию внутренние группы рабочей нагрузки и пулы ресурсов.  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Ограничения  
 В пользовательской транзакции регулятор ресурсов нельзя отключить с помощью инструкции **ALTER RESOURCE GOVERNOR** .  
  
###  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для отключения регулятора ресурсов требуется разрешение CONTROL SERVER.  
  
##  <a name="disable-resource-governor-using-object-explorer"></a><a name="RGOffObjEx"></a> Отключение регулятора ресурсов с помощью обозревателя объектов  
 **Отключение регулятора ресурсов с помощью обозревателя объектов**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните элемент **Resource Governor**правой кнопкой мыши и выберите команду **Отключить**.  

##  <a name="disable-resource-governor-using-resource-governor-properties"></a><a name="RGOffProp"></a> Отключение регулятора ресурсов с помощью свойств регулятора ресурсов  
 **Отключение регулятора ресурсов с помощью страницы «Свойства регулятора ресурсов»**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните правой кнопкой мыши **Регулятор ресурсов** и выберите пункт **Свойства**, после чего откроется страница **Свойства регулятора ресурсов** .  
  
3.  Щелкните флажок **Включить регулятор ресурсов** , убедитесь в том, что этот флажок не выбран, и нажмите кнопку **ОК**.  
  
##  <a name="disable-resource-governor-using-transact-sql"></a><a name="RGOffTSQL"></a> Отключение регулятора ресурсов с помощью Transact-SQL  
 **Отключение регулятора ресурсов с помощью Transact-SQL**  
  
1.  Выполните инструкцию **ALTER RESOURCE GOVERNOR DISABLE** .  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере показано включение регулятора ресурсов.  
  
```  
ALTER RESOURCE GOVERNOR DISABLE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)   
 [Активация регулятора ресурсов](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [Пул ресурсов регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Группа рабочей нагрузки регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Функция-классификатор регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
