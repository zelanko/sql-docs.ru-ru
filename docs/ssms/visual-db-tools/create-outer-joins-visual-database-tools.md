---
title: "Создание внешних соединений (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- outer joins
- joins [SQL Server], outer
ms.assetid: 18de47b1-f936-427d-b852-fe6d20334f71
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7399c344d94920c76093883eb8cf5244222ce707
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="create-outer-joins-visual-database-tools"></a>Создание внешних соединений (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] По умолчанию [Конструктор запросов и представлений](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) создает внутреннее соединение таблиц. Внутренние соединения исключают строки, не соответствующие строке из другой таблицы. Однако внешние соединения возвращают все строки хотя бы из одной таблицы или представления, упомянутых в предложении FROM, если эти строки удовлетворяют условиям поиска WHERE или HAVING. Если необходимо включить строки данных, которые не имеют совпадений в соединяемой таблице, в результирующий набор, можно создать внешнее соединение.  
  
При создании внешнего соединения имеет значение порядок, в котором указывают таблицы в инструкции SQL (как показано на панели SQL). Первая таблица становится «левой» таблицей, а вторая — «правой» (Реальный порядок, в котором указываются таблицы на [панели диаграммы](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md), несущественен.) При указании левого или правого внешнего соединения указывается порядок, в котором таблицы были добавлены в запрос, и порядок, в котором они появляются в инструкции SQL на [панели SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
### <a name="to-create-an-outer-join"></a>Создание внешнего соединения  
  
1.  Создайте соединение автоматически или вручную. Дополнительные сведения см. в статье [Автоматическое соединение таблиц (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/join-tables-automatically-visual-database-tools.md) или [Соединение таблиц вручную (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/join-tables-manually-visual-database-tools.md).  
  
2.  Выберите линию соединения на панели диаграммы, а затем в меню **Конструктор запросов** выберите **Выбрать все строки из <tablename>**, указав команду, включающую таблицу, дополнительные строки которой необходимо включить.  
  
    -   Выберите первую таблицу для создания левого внешнего соединения.  
  
    -   Выберите вторую таблицу для создания правого внешнего соединения.  
  
    -   Выберите обе таблицы для создания полного внешнего соединения.  
  
При указании внешнего соединения конструктор запросов и представлений изменяет линию соединения для отображения внешнего соединения.  
  
Кроме того, конструктор запросов и представлений изменяет инструкцию SQL на панели SQL для отражения изменений типа соединения, как показано в следующей инструкции:  
  
```  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
```  
  
Так как внешнее соединение включает несовпадающие строки, можно использовать его для поиска строк, которые нарушают ограничение внешнего ключа. Чтобы сделать это, надо создать внешнее соединение и добавить условие поиска строк, в которых значение первичного ключевого столбца самой правой таблицы равно NULL. Например, следующее внешнее соединение находит строки в таблице `employee` , которая не содержит соответствующих строк в таблице `jobs` :  
  
```  
SELECT employee.emp_id, employee.job_id  
FROM employee LEFT OUTER JOIN jobs   
   ON employee.job_id = jobs.job_id  
WHERE (jobs.job_id IS NULL)  
```  
  
## <a name="see-also"></a>См. также:  
[Запросы с соединениями (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
[Диалоговое окно "Соединение" (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/join-dialog-box-visual-database-tools.md)  
  
