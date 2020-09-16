---
title: вставлять фрагменты кода Transact-SQL
description: Узнайте, как выбрать, вставить и изменить фрагмент кода Transact-SQL, который может служить отправной точкой при написании новых инструкций Transact-SQL в редакторе запросов ядра СУБД.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [SQL Server], snippets
- Transact-SQL snippets, code
- snippets [Transact-SQL], how to insert
ms.assetid: d66c96f4-2e84-4d79-9bfd-3635fdd98425
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 979018404b696ef3d8a39b198d4cf115e28f068f
ms.sourcegitcommit: 6d53ecfdc463914f045c20eda96da39dec22acca
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/26/2020
ms.locfileid: "88901908"
---
# <a name="insert-transact-sql-snippets"></a>вставлять фрагменты кода Transact-SQL
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
  Фрагмент кода [!INCLUDE[tsql](../../includes/tsql-md.md)] можно использовать в качестве шаблона при написании новых инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] в редакторе запросов компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
## <a name="inserting-snippets"></a>Вставка фрагментов  
 Открыть упорядоченный по категориям перечень доступных для выбора фрагментов можно из меню **Вставить фрагмент** .  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] содержат точки замены: текст с рекомендациями по синтаксису, относящемуся к данной точке. Например, во фрагменте CREATE TABLE находятся точки замены для таких элементов, как имя таблицы, имена столбцов, типы данных в столбцах. После вставки фрагмента кода необходимо заменить текст замены, образовав правильную инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] . Дополнительные сведения см. в разделе [Завершение фрагментов кода Transact-SQL](../../relational-databases/scripting/complete-transact-sql-snippets.md).  
  
#### <a name="inserting-a-snippet-by-using-the-insert-snippet-menu"></a>Вставка фрагмента с помощью меню «Вставить фрагмент»  
  
1.  Откройте окно «Редактор запроса компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] » и переместите курсор в место будущей вставки фрагмента [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
2.  Вызовите подсказку одним из следующих способов.  
  
    -   Нажмите комбинацию клавиш CTRL+K или CTRL+X.  
  
    -   В меню **Правка** укажите пункт **IntelliSense**и выберите **Вставить фрагмент**.  
  
    -   Щелкните правой кнопкой мыши и выберите из контекстного меню команду **Вставить фрагмент** .  
  
3.  Дважды щелкните фрагмент или выберите фрагмент из захваченных и нажмите клавишу TAB или ВВОД.  
  
## <a name="see-also"></a>См. также:  
 [Вставка фрагментов кода окружения Transact-SQL](../../relational-databases/scripting/insert-surround-with-transact-sql-snippets.md)  
  
  
