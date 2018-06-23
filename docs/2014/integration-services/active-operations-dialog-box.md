---
title: Диалоговое окно «активные операции» | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.ssms.isoperations.executions.f1
- sql12.ssis.ssms.isoperations.general.f1
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: adf25cd2194e1a02877c38a15d81d8697427ad76
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095051"
---
# <a name="active-operations-dialog-box"></a>Диалоговое окно «Активные операции»
  Воспользуйтесь диалоговым окном **Активные операции** , чтобы просмотреть состояние выполняемых в настоящий момент операций [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на сервере служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , таких как развертывание, проверка и выполнение пакетов. Эти данные хранятся в каталоге SSISDB.  
  
 Дополнительные сведения о связанных представлениях [!INCLUDE[tsql](../includes/tsql-md.md)] см. в разделах [catalog.operations (база данных SSISDB)](/sql/integration-services/system-views/catalog-operations-ssisdb-database), [catalog.validations (база данных SSISDB)](/sql/integration-services/system-views/catalog-validations-ssisdb-database) и [catalog.executions (база данных SSISDB)](/sql/integration-services/system-views/catalog-executions-ssisdb-database).  
  
 **Выбор действия**  
  
1.  [Откройте диалоговое окно «активные операции»](#open_dialog)  
  
2.  [Настройка параметров](#options)  
  
##  <a name="open_dialog"></a> Открытие диалогового окна «Активные операции»  
  
1.  Откройте [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
2.  Подключение компонента Microsoft SQL Server Database Engine  
  
3.  В обозревателе объектов разверните узел **Службы Integration Services** , щелкните правой кнопкой мыши элемент **SSISDB**и выберите пункт **Активные операции**.  
  
##  <a name="options"></a> Настройка параметров  
  
### <a name="options"></a>Параметры  
 **Тип**  
 Задает тип операции. Ниже приведены возможные значения для **тип** поля и соответствующие значения в столбце operations_type представления Transact-SQL `catalog.operations` представления.  
  
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
  
  
