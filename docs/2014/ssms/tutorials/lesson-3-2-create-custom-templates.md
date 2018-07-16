---
title: Создание пользовательских шаблонов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- tql
- templates [Transact-SQL], creating
- templates [Transact-SQL]
ms.assetid: 41098e78-b482-410e-bfe8-2ac10769ac4a
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5a679ed1aaf51ff1282976aa7c8c0b509c23a0d4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321704"
---
# <a name="create-custom-templates"></a>Создание пользовательских шаблонов
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
  
11. Измените скрипт шаблона (из шага 7), заменив имя товара с параметром ***< * product_name**, `nvarchar(50)`, **имя*> ***, в четырех местах.  
  
    > [!NOTE]  
    >  Для параметра необходимо указать три элемента: имя замещаемого параметра, тип данных параметра, значение параметра по умолчанию.  
  
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
  
4.  В **замена параметров шаблона** диалоговом окне для `product_name` введите **FreeWheel** (заменяя содержимое по умолчанию), а затем нажмите кнопку **ОК** для закрытия **Замена параметров шаблона** диалоговое окно и отредактируйте скрипт в редакторе запросов.  
  
5.  Нажмите F5, чтобы выполнить запрос и создать процедуру.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Сохранение скриптов в виде проектов или решений](lesson-3-3-save-scripts-as-projects-or-solutions.md)  
  
  
