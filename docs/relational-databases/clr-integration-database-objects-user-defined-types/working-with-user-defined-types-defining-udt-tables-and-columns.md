---
title: Определение определяемого пользователем ТИПА таблицы и столбцы | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 11
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7fb463a9cf7cde943357ae7b1f3da8ed1dbfb253
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32919229"
---
# <a name="working-with-user-defined-types---defining-udt-tables-and-columns"></a>Работа с пользовательскими типами - определение определяемого пользователем ТИПА таблицы и столбцы
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  После сборки, содержащей определяемый пользователем тип (UDT) определение был зарегистрирован в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных, он может использоваться в определении столбца.  
  
## <a name="creating-tables-with-udts"></a>Создание таблиц с использованием определяемых пользователем типов  
 Не существует специального синтаксиса для создания в таблице столбца определяемого пользователем типа. Можно использовать в определении столбца имя определяемого пользователем типа, как если бы он был одним из внутренних типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В следующей ТАБЛИЦЕ, СОЗДАЙТЕ [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкция создает таблицу с именем **точки**, со столбцом с именем **идентификатор,** определяется как **int** столбца идентификаторов и первичный ключ для таблицы. Второй столбец называется **PointValue**, с типом данных **точки**. Имя схемы, используемой в этом примере — **dbo**. Обратите внимание, что требуется иметь соответствующие разрешения на указание имени схемы. Если имя схемы опущено, используется схема по умолчанию для пользователя базы данных.  
  
```  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a>Создание индексов по столбцам определяемых пользователем типов  
 Существует два параметра для индексирования столбца определяемого пользователем типа:  
  
-   Индекс полного значения. В этом случае, если определяемый пользователем тип поддерживает двоичный режим упорядочивания, можно создать индекс для всего столбца определяемого пользователем типа при помощи инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX.  
  
-   Индекс выражений определяемого пользователем типа. Можно создать индексы материализованных вычисляемых столбцов при помощи выражений определяемого пользователем типа. Выражение определяемого пользователем типа может быть полем, методом или свойством определяемого пользователем типа. Выражение должно быть детерминированным и не осуществлять доступ к данным.  
  
 Дополнительные сведения см. в разделе [определяемые пользователем типы](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) и [CREATE INDEX & #40; Transact-SQL & #41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Работа с пользовательскими типами в SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)  
  
  
