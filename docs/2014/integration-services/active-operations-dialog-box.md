---
title: Диалоговое окно «активные операции» | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isoperations.executions.f1
- sql12.ssis.ssms.isoperations.general.f1
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f930a2e6f3ce84c330a4b7292ebaaba3b2ab871e
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66062219"
---
# <a name="active-operations-dialog-box"></a>Диалоговое окно «Активные операции»
  Воспользуйтесь диалоговым окном **Активные операции** , чтобы просмотреть состояние выполняемых в настоящий момент операций [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на сервере служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , таких как развертывание, проверка и выполнение пакетов. Эти данные хранятся в каталоге SSISDB.  
  
 Дополнительные сведения о связанных представлениях [!INCLUDE[tsql](../includes/tsql-md.md)] см. в разделах [catalog.operations (база данных SSISDB)](/sql/integration-services/system-views/catalog-operations-ssisdb-database), [catalog.validations (база данных SSISDB)](/sql/integration-services/system-views/catalog-validations-ssisdb-database) и [catalog.executions (база данных SSISDB)](/sql/integration-services/system-views/catalog-executions-ssisdb-database).  
  
 **Выбор действия**  
  
1.  [Открытие диалогового окна «Активные операции»](#open_dialog)  
  
2.  [Настройка параметров](#options)  
  
##  <a name="open_dialog"></a> Открытие диалогового окна «Активные операции»  
  
1.  Откройте [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
2.  Подключение компонента Microsoft SQL Server Database Engine  
  
3.  В обозревателе объектов разверните узел **Службы Integration Services** , щелкните правой кнопкой мыши элемент **SSISDB**и выберите пункт **Активные операции**.  
  
##  <a name="options"></a> Настройка параметров  
  
### <a name="options"></a>Параметры  
 **Тип**  
 Задает тип операции. Ниже приведены возможные значения для **тип** поля и соответствующие значения в столбце operations_type Transact-SQL `catalog.operations` представления.  
  
|||  
|-|-|  
|Инициализация служб Integration Services|1|  
|Очистка операций (задание агента SQL Server)|2|  
|Очистка версий проекта (задание агента SQL Server)|3|  
|Развернуть проект|101|  
|Восстановить проект|106|  
|Создать и запустить выполнение пакета|200|  
|Остановить операцию (остановка проверки или выполнения|202|  
|Проверить проект|300|  
|Проверить пакет|301|  
|Настроить каталог|1000|  
  
 **Остановить**  
 Щелкните, чтобы остановить выполняемую в настоящий момент операцию.  
  
  
