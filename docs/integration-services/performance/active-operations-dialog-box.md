---
title: "Диалоговое окно &#171;Активные операции&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.ssms.isoperations.executions.f1"
  - "sql13.ssis.ssms.isoperations.general.f1"
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Диалоговое окно &#171;Активные операции&#187;
  Воспользуйтесь диалоговым окном **Активные операции** , чтобы просмотреть состояние выполняемых в настоящий момент операций [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , таких как развертывание, проверка и выполнение пакетов. Эти данные хранятся в каталоге SSISDB.  
  
 Дополнительные сведения о связанных представлениях [!INCLUDE[tsql](../../includes/tsql-md.md)] см. в разделах [catalog.operations (база данных SSISDB)](../../integration-services/system-views/catalog-operations-ssisdb-database.md), [catalog.validations (база данных SSISDB)](../../integration-services/system-views/catalog-validations-ssisdb-database.md) и [catalog.executions (база данных SSISDB)](../../integration-services/system-views/catalog-executions-ssisdb-database.md).  
  
 **Выбор действия**  
  
-   [Открытие диалогового окна «Активные операции»](../../integration-services/performance/active-operations-dialog-box.md#open_dialog)  
  
-   [Параметры](#options)  
  
##  <a name="open_dialog"></a> Открытие диалогового окна «Активные операции»  
  
1.  Откройте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  Подключение компонента Microsoft SQL Server Database Engine  
  
3.  В обозревателе объектов разверните узел **Службы Integration Services**, щелкните правой кнопкой мыши элемент **SSISDB** и выберите пункт **Активные операции**.  
  
## Настройка параметров  
  
###  <a name="options"></a> Параметры  
 **Тип**  
 Задает тип операции. Ниже приведены возможные значения поля **Тип** и соответствующие значения в столбце operations_type представления Transact-SQL **catalog.operations**.  
  
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
  
  