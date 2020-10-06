---
description: REFERENTIAL_CONSTRAINTS (Transact-SQL)
title: REFERENTIAL_CONSTRAINTS (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- REFERENTIAL_CONSTRAINTS
- REFERENTIAL_CONSTRAINTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.REFERENTIAL_CONSTRAINTS view
- REFERENTIAL_CONSTRAINTS view
ms.assetid: 5d358f18-0a85-4b55-af4b-98d5f4cd1020
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 42ebb05e1ec3bf70426cb0cef662623e2beb57f7
ms.sourcegitcommit: 968969b62bc158b9843aba5034c9d913519bc4a7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/06/2020
ms.locfileid: "91753962"
---
# <a name="referential_constraints-transact-sql"></a>REFERENTIAL_CONSTRAINTS (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает одну строку для каждого ограничения FOREIGN KEY в текущей базе данных. Это представление информационной схемы возвращает сведения об объектах, на которые у текущего пользователя есть разрешения.  
  
 Чтобы получить сведения из этих представлений, укажите полное имя **INFORMATION_SCHEMA.** _view_name_.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**CONSTRAINT_CATALOG**|**nvarchar (** 128 **)**|Квалификатор ограничения.|  
|**CONSTRAINT_SCHEMA**|**nvarchar (** 128 **)**|Имя схемы, содержащей ограничение.<br /><br /> **&#42;&#42; важно &#42;&#42;** Не используйте INFORMATION_SCHEMA представления для определения схемы объекта. INFORMATION_SCHEMA представления представляют только подмножество метаданных объекта. Единственный надежный способ найти схему объекта — направить запрос к представлению каталога sys.objects.|  
|**CONSTRAINT_NAME**|**sysname**|Имя ограничения.|  
|**UNIQUE_CONSTRAINT_CATALOG**|**nvarchar (** 128 **)**|Квалификатор ограничения UNIQUE.|  
|**UNIQUE_CONSTRAINT_SCHEMA**|**nvarchar (** 128 **)**|Имя схемы, содержащей ограничение UNIQUE.<br /><br /> **&#42;&#42; важно &#42;&#42;** Не используйте INFORMATION_SCHEMA представления для определения схемы объекта. INFORMATION_SCHEMA представления представляют только подмножество метаданных объекта. Единственный надежный способ найти схему объекта — направить запрос к представлению каталога sys.objects.|  
|**UNIQUE_CONSTRAINT_NAME**|**sysname**|Ограничение UNIQUE.|  
|**MATCH_OPTION**|**varchar (** 7 **)**|Ссылочные условия, соответствующие ограничению. Всегда возвращает SIMPLE. Это означает, что не определено никакого соответствия. Предполагается, что условие соответствует ограничению, если выполняется одно из следующих требований.<br /><br /> Хотя бы одно значение внешнего ключевого столбца равно NULL.<br /><br /> Все значения внешнего ключевого столбца не равны NULL, и в таблице первичного ключа имеется строка с таким же ключом.|  
|**UPDATE_RULE**|**varchar (** 11 **)**|Операция принимается, если инструкция языка [!INCLUDE[tsql](../../includes/tsql-md.md)] нарушает ссылочную целостность, определенную этим ограничением. Возвращает одно из следующих значений. <br />NO ACTION<br />CASCADE<br />SET NULL<br />SET DEFAULT<br /><br /> Если на ON UPDATE для этого ограничения указывается NO ACTION, обновление первичного ключа, на который выполняется ссылка в ограничении, не будет распространяться на внешний ключ. Если такое обновление первичного ключа будет вызывать нарушение ссылочной целостности, так как по крайней мере один внешний ключ содержит такое же значение, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не будет выполнять изменений в родительских и ссылающихся на них таблицах. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также возникнет ошибка.<br /><br /> Если на ON UPDATE для этого ограничения указывается CASCADE, любое изменение первичного ключа автоматически распространяется на значение внешнего ключа.|  
|**DELETE_RULE**|**varchar (** 11 **)**|Операция принимается, если инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] нарушает ссылочную целостность, определенную этим ограничением. Возвращает одно из следующих значений. <br />NO ACTION<br />CASCADE<br />SET NULL<br />SET DEFAULT<br /><br /> Если на ON DELETE для этого ограничения указывается NO ACTION, удаление на первичном ключе, на который выполняется ссылка в ограничении, не будет распространяться на внешний ключ. Если такое удаление первичного ключа будет вызывать нарушение ссылочной целостности, так как по крайней мере один внешний ключ содержит такое же значение, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не будет выполнять изменений в родительских и ссылающихся на них таблицах. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также возникнет ошибка.<br /><br /> Если на ON DELETE для этого ограничения указывается CASCADE, любое изменение значения первичного ключа автоматически распространяется на значение внешнего ключа.|  
  
## <a name="see-also"></a>См. также  
 [Системные представления &#40;&#41;Transact-SQL ](../../t-sql/language-reference.md)   
 [Представления информационной схемы &#40;&#41;Transact-SQL ](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.foreign_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-foreign-keys-transact-sql.md)  
  
