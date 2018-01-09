---
title: "При удалении сборки | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- removing assemblies
- DROP ASSEMBLY statement
- assemblies [CLR integration], removing
- dropping assemblies
ms.assetid: 03481034-dc91-4488-ab24-ba44243e2690
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5c3f4ddb7618756878da84112ea713520a0d3e01
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="dropping-an-assembly"></a>Удаление сборки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Сборки, которые были зарегистрированы в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью инструкции CREATE ASSEMBLY может быть удалена или удалена, когда они предоставляют функциональные возможности больше не нужны. При удалении сборки из базы данных удаляются и все связанные с ней файлы, такие как файлы отладки. Чтобы удалить сборку, используйте инструкцию DROP ASSEMBLY со следующим синтаксисом:  
  
```  
DROP ASSEMBLY MyDotNETAssembly  
```  
  
 Инструкция DROP ASSEMBLY не влияет на код, ссылающийся на работающую в данный момент сборку, но после ее выполнения любые попытки вызова кода сборки завершатся ошибкой.  
  
 Инструкция DROP ASSEMBLY возвращает ошибку, если на сборку ссылается другая существующая в базе данных сборка или если она используется функциями среды CLR, процедурами, триггерами, определенными пользователем типами или статистическими функциями в текущей базе данных. Сначала используйте инструкции DROP AGGREGATE, DROP FUNCTION, DROP PROCEDURE, DROP TRIGGER и DROP TYPE, чтобы удалить все управляемые объекты базы данных, содержащиеся в сборке.  
  
## <a name="removing-a-udt-from-the-database"></a>Удаление определяемого пользователем типа из базы данных  
 Инструкция DROP TYPE удаляет определяемый пользователем тип из текущей базы данных. После удаления определяемого пользователем типа можно инструкцией DROP ASSEMBLY удалить сборку из базы данных.  
  
 Инструкция DROP TYPE завершается с ошибкой, если объекты зависят от определяемого пользователем типа, как, например, в следующих ситуациях.  
  
-   Таблицы в базе данных, которые содержат столбцы, определенные с помощью определяемого пользователем типа.  
  
-   Функции, хранимые процедуры или триггеры, которые используют переменные или параметры определяемого пользователем типа и созданы в базе данных с помощью предложения WITH SCHEMABINDING.  
  
### <a name="finding-udt-dependencies"></a>Поиск зависимостей определяемого пользователем типа  
 Сначала необходимо удалить все зависимые объекты, а затем выполнить инструкцию DROP TYPE. Следующие [!INCLUDE[tsql](../../../includes/tsql-md.md)] запрос находит все столбцы и параметры, используемые определяемого пользователем ТИПА в **AdventureWorks** базы данных.  
  
```  
USE Adventureworks;  
SELECT o.name AS major_name, o.type_desc AS major_type_desc  
     , c.name AS minor_name, c.type_desc AS minor_type_desc  
     , at.assembly_class  
  FROM (  
        SELECT object_id, name, user_type_id, 'SQL_COLUMN' AS type_desc  
          FROM sys.columns  
     UNION ALL  
        SELECT object_id, name, user_type_id, 'SQL_PROCEDURE_PARAMETER'  
          FROM sys.parameters  
     ) AS c  
  JOIN sys.objects AS o  
    ON o.object_id = c.object_id  
  JOIN sys.assembly_types AS at  
    ON at.user_type_id = c.user_type_id;   
```  
  
## <a name="see-also"></a>См. также:  
 [Управление сборками интеграции со средой CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [Изменение сборки](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)   
 [Создание сборки](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [DROP AGGREGATE &#40; Transact-SQL &#41;](../../../t-sql/statements/drop-aggregate-transact-sql.md)   
 [ФУНКЦИЯ СБРОСА &#40; Transact-SQL &#41;](../../../t-sql/statements/drop-function-transact-sql.md)   
 [DROP PROCEDURE &#40; Transact-SQL &#41;](../../../t-sql/statements/drop-procedure-transact-sql.md)   
 [DROP TRIGGER (Transact-SQL)](../../../t-sql/statements/drop-trigger-transact-sql.md)   
 [Тип удаления &#40; Transact-SQL &#41;](../../../t-sql/statements/drop-type-transact-sql.md)  
  
  
