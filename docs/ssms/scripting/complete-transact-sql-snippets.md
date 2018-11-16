---
title: Завершение фрагментов кода Transact-SQL | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], completing snippets
- snippets [Transact-SQL], completing
- Transact-SQL snippets, completing
ms.assetid: a8316a58-bb57-485e-845f-84c23360314c
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 198699516b4246f171bbd7a5c3f3fe2d5124b04d
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2018
ms.locfileid: "51643875"
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
  
  
