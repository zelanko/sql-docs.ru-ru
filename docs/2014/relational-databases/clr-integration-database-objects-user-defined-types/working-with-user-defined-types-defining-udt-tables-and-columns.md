---
title: Определение Пользовательских таблиц и столбцов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
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
ms.openlocfilehash: 360715f3b239347aedcae2b50a0e21f7a2943125
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37351806"
---
# <a name="defining-udt-tables-and-columns"></a>Определение таблиц и столбцов определяемых пользователем типов
  После сборки, содержащей определяемого пользователем типа (UDT) определения регистрации в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных, он может использоваться в определении столбца.  
  
## <a name="creating-tables-with-udts"></a>Создание таблиц с использованием определяемых пользователем типов  
 Не существует специального синтаксиса для создания в таблице столбца определяемого пользователем типа. Можно использовать в определении столбца имя определяемого пользователем типа, как если бы он был одним из внутренних типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В следующей ТАБЛИЦЕ, СОЗДАЙТЕ [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкция создает таблицу с именем **точки**, со столбцом с именем **идентификатор,** определяется как `int` столбец идентификаторов и \ первичный ключ для таблицы. Второй столбец называется **PointValue**, с типом данных **точки**. Имя схемы, используемой в этом примере является **dbo**. Обратите внимание, что требуется иметь соответствующие разрешения на указание имени схемы. Если имя схемы опущено, используется схема по умолчанию для пользователя базы данных.  
  
```  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a>Создание индексов по столбцам определяемых пользователем типов  
 Существует два параметра для индексирования столбца определяемого пользователем типа:  
  
-   Индекс полного значения. В этом случае, если определяемый пользователем тип поддерживает двоичный режим упорядочивания, можно создать индекс для всего столбца определяемого пользователем типа при помощи инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX.  
  
-   Индекс выражений определяемого пользователем типа. Можно создать индексы материализованных вычисляемых столбцов при помощи выражений определяемого пользователем типа. Выражение определяемого пользователем типа может быть полем, методом или свойством определяемого пользователем типа. Выражение должно быть детерминированным и не осуществлять доступ к данным.  
  
 Дополнительные сведения см. в разделе [определяемые пользователем типы](clr-user-defined-types.md) и [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).  
  
## <a name="see-also"></a>См. также  
 [Работа с определяемыми пользователем типами в SQL Server](working-with-user-defined-types-in-sql-server.md)  
  
  
