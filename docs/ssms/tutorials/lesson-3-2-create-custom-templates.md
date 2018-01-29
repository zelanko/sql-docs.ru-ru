---
title: "Создание пользовательских шаблонов | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-tutorial
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tql
- templates [Transact-SQL], creating
- templates [Transact-SQL]
ms.assetid: 41098e78-b482-410e-bfe8-2ac10769ac4a
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 757a6b2aebe68dc32ddc493c3e6649a8b589be3e
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="lesson-3-2---create-custom-templates"></a>Занятие 3–2. Создание пользовательских шаблонов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] поставляется с шаблонами, с помощью которых можно решить многие стандартные задачи, однако реальная эффективность шаблонов заключается в возможности создания пользовательского шаблона для часто используемых сложных скриптов. В этом практическом задании будет создан простой скрипт с несколькими параметрами, однако шаблоны применимы и для длинных скриптов с повторениями.  
  
## <a name="using-custom-templates"></a>Использование пользовательских шаблонов  
  
#### <a name="to-create-a-custom-template"></a>Использование пользовательских шаблонов  
  
1.  В обозревателе шаблонов разверните узел **Шаблоны SQL Server**, щелкните правой кнопкой мыши элемент **Хранимая процедура**, наведите указатель на пункт **Создать**и выберите пункт **Папка**.  
  
2.  Введите **Пользовательская** в качестве имени новой папки шаблона и нажмите клавишу ВВОД.  
  
3.  Щелкните правой кнопкой мыши папку **Пользовательская**, наведите указатель на пункт **Создать**и выберите пункт **Шаблон**.  
  
4.  Введите **WorkOrdersProc** в качестве имени нового шаблона и нажмите клавишу **ВВОД**.  
  
5.  Щелкните правой кнопкой мыши значок **WorkOrdersProc**и выберите команду **Изменить**.  
  
6.  В диалоговом окне **Подключиться к ядру СУБД** проверьте сведения о соединении и нажмите кнопку **Подключиться**.  
  
7.  В редакторе запросов введите следующий скрипт, чтобы создать хранимую процедуру, выполняющую поиск заказов для нужной детали, в данном случае роликовых коньков. Код сценария можно скопировать из учебника.  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersForBlade')  
       DROP PROCEDURE dbo.WorkOrdersForBlade;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersForBlade  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = 'Blade';  
    GO  
    ```  
  
8.  Нажмите клавишу F5, чтобы выполнить скрипт и создать процедуру **WorkOrdersForBlade** .  
  
9. В обозревателе объектов щелкните правой кнопкой мыши свой сервер и выберите команду **Создать запрос**. Будет открыто новое окно редактора запросов.  
  
10. В редакторе запросов введите **EXECUTE dbo.WorkOrdersForBlade**и нажмите клавишу F5, чтобы выполнить запрос. Убедитесь в том, что на панели **Результаты** отображается список заказов на производство роликовых коньков.  
  
11. Измените скрипт шаблона (из шага 7), заменив в четырех местах имя товара Blade параметром ***\<*product_name**, **nvarchar(50)**, **name*>***.  
  
    > [!NOTE]  
    > Для параметра необходимо указать три элемента: имя замещаемого параметра, тип данных параметра, значение параметра по умолчанию.  
  
12. Скрипт должен иметь следующий вид:  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersFor<product_name, nvarchar(50), name>')  
       DROP PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = '<product_name, nvarchar(50), name>';  
    GO  
    ```  
  
13. В меню **Файл** выберите команду **Сохранить WorkOrdersProc.sql** , чтобы сохранить шаблон.  
  
#### <a name="to-test-the-custom-template"></a>Проверка пользовательского шаблона  
  
1.  В обозревателе шаблонов последовательно разверните элементы **Хранимая процедура**и **Пользовательская**, а затем дважды щелкните шаблон **WorkOrderProc**.  
  
2.  В диалоговом окне **Подключиться к ядру СУБД** введите сведения о соединении и нажмите кнопку **Подключиться**. Откроется новое окно редактора запросов, в котором приводится содержимое шаблона **WorkOrderProc** .  
  
3.  В меню **Запрос** выберите пункт **Указать значения для параметров шаблона**.  
  
4.  В диалоговом окне **Замена параметров шаблона** в поле **product_name** введите **FreeWheel** (заменив содержимое по умолчанию), а затем нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **Замена параметров шаблона** и изменить скрипт в редакторе запросов.  
  
5.  Нажмите F5, чтобы выполнить запрос и создать процедуру.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Сохранение скриптов в виде проектов или решений](../../tools/sql-server-management-studio/lesson-3-3-save-scripts-as-projects-or-solutions.md)  
  
  
  
