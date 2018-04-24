---
title: Завершение фрагментов кода Transact-SQL | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-scripting
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense [SQL Server], completing snippets
- snippets [Transact-SQL], completing
- Transact-SQL snippets, completing
ms.assetid: a8316a58-bb57-485e-845f-84c23360314c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8e1793b4d6987dbb40d1370855f51394d325d0a5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="complete-transact-sql-snippets"></a>Завершение фрагментов кода Transact-SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  После вставки фрагмента кода [!INCLUDE[tsql](../../includes/tsql-md.md)] в скрипт нужно изменить содержимое этого фрагмента, чтобы получить завершенную инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
## <a name="completing-snippets"></a>Завершение фрагментов  
 При добавлении фрагмента кода [!INCLUDE[tsql](../../includes/tsql-md.md)] в скрипт во вставленном фрагменте имеется одна или несколько подсвеченных точек замены. При наведении указателя мыши на точку замены появляется подсказка с описанием синтаксического элемента, который можно указать. Редактор запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] распознает фрагмент кода как отдельный блок в скрипте до закрытия исходного файла. Точки замены остаются активными до закрытия исходного файла.  
  
 Также в код шаблона, вставленный во фрагменте, можно добавить дополнительные синтаксические элементы. Например, если шаблон создания таблицы создает два определения столбца, для создания таблицы с числом столбцов больше двух необходимо добавить дополнительные определения столбцов.  
  
#### <a name="completing-the-snippet-statement"></a>Завершение инструкций фрагмента кода  
  
1.  С помощью клавиши табуляции можно перейти к следующей точке замены. С помощью сочетания клавиш SHIFT и табуляции можно перейти к предыдущей точке замены.  
  
2.  Нажмите сочетание клавиш Click+ПРОБЕЛ для вызова IntelliSense.  
  
3.  Выберите элемент из списка или введите собственный вариант.  
  
## <a name="see-also"></a>См. также:  
 [вставлять фрагменты кода Transact-SQL](../../relational-databases/scripting/insert-transact-sql-snippets.md)   
 [Вставка фрагментов кода окружения Transact-SQL](../../relational-databases/scripting/insert-surround-with-transact-sql-snippets.md)  
  
  
