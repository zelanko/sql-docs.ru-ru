---
title: Определение таблиц и столбцов определяемого пользователем типа | Документация Майкрософт
ms.custom: ''
ms.date: 12/05/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [CLR integration], columns
- UDTs [CLR integration], columns
- columns [CLR integration]
- user-defined types [CLR integration], tables
- tables [CLR integration]
- UDTs [CLR integration], tables
- UDTs [CLR integration], indexes
- user-defined types [CLR integration], indexes
- indexes [CLR integration]
ms.assetid: aea495f4-ce26-4952-b019-38f012625f3f
author: rothja
ms.author: jroth
ms.openlocfilehash: 8386da85d22f50b45492ecd52588e6d06fe80590
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74901957"
---
# <a name="working-with-user-defined-types---defining-udt-tables-and-columns"></a>Работа с определяемыми пользователем типами — определение пользовательских таблиц и столбцов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  После регистрации в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных сборки, содержащей определение определяемого пользователем типа (UDT), ее можно использовать в определении столбца. Дополнительные сведения см. в разделе [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md).  
  
## <a name="creating-tables-with-udts"></a>Создание таблиц с использованием определяемых пользователем типов  
 Не существует специального синтаксиса для создания в таблице столбца определяемого пользователем типа. Можно использовать в определении столбца имя определяемого пользователем типа, как если бы он был одним из внутренних типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Следующая инструкция CREATE TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)] создает таблицу с именем **points**и столбцом с именем **ID,** который определяется как столбец идентификаторов **int** и первичный ключ для таблицы. Второй столбец называется **PointValue**и имеет тип данных **Point**. В этом примере используется имя схемы **dbo**. Обратите внимание, что требуется иметь соответствующие разрешения на указание имени схемы. Если имя схемы опущено, используется схема по умолчанию для пользователя базы данных.  
  
```sql  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a>Создание индексов по столбцам определяемых пользователем типов  
 Существует два параметра для индексирования столбца определяемого пользователем типа:  
  
-   **Индекс полного значения.** В этом случае, если определяемый пользователем тип поддерживает двоичный режим упорядочивания, можно создать индекс для всего столбца определяемого пользователем типа при помощи инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX.  
  
-   **Индекс выражений определяемого пользователем типа.** Можно создать индексы материализованных вычисляемых столбцов при помощи выражений определяемого пользователем типа. Выражение определяемого пользователем типа может быть полем, методом или свойством определяемого пользователем типа. Выражение должно быть детерминированным и не осуществлять доступ к данным.  
  
 Дополнительные сведения см. в разделе [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Работа с определяемыми пользователем типами данных в SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)     
 [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)     
 [Определяемые пользователем типы данных CLR](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)     
