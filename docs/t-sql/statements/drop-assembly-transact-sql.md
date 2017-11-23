---
title: "DROP сборки (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP ASSEMBLY
- DROP_ASSEMBLY_TSQL
dev_langs: TSQL
helpviewer_keywords:
- removing assemblies
- DROP ASSEMBLY statement
- deleting assemblies
- assemblies [CLR integration], removing
- dropping assemblies
- WITH NO DEPENDENTS option
ms.assetid: 452d181a-a8e6-44a3-975d-29966d01b18d
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7e466c9be38de4706493f3d181ca1648c9027a19
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="drop-assembly-transact-sql"></a>DROP ASSEMBLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет сборку и все связанные с ней файлы из текущей базы данных. Сборки создаются с помощью [CREATE ASSEMBLY](../../t-sql/statements/create-assembly-transact-sql.md) и изменяются с помощью [ALTER ASSEMBLY](../../t-sql/statements/alter-assembly-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP ASSEMBLY [ IF EXISTS ] assembly_name [ ,...n ]  
[ WITH NO DEPENDENTS ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *ЕСЛИ СУЩЕСТВУЕТ*  
 **Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условно удаляет сборку только в том случае, если он уже существует.  
  
 *assembly_name*  
 Имя сборки, которую нужно удалить.  
  
 WITH NO DEPENDENTS  
 Если указано, удаляется только *assembly_name* и ни один из зависимых сборок, на которые ссылается сборка. Если не указан, инструкция DROP ASSEMBLY удаляет *assembly_name* и все зависимые сборки.  
  
## <a name="remarks"></a>Замечания  
 При удалении сборки из базы данных удаляются и все связанные с ней файлы, такие как исходный код и файлы отладки.  
  
 Если WITH NO DEPENDENTS не указано, инструкция DROP ASSEMBLY удаляет *assembly_name* и все зависимые сборки. Если попытка удалить какую-либо зависимую сборку не удается, инструкция DROP ASSEMBLY возвращает ошибку.  
  
 Инструкция DROP ASSEMBLY возвращает ошибку, если на сборку ссылается другая существующая в базе данных сборка или если она используется функциями, процедурами, триггерами, пользовательскими типами или статистическими функциями среды CLR в данной базе данных.  
  
 Инструкция DROP ASSEMBLY не взаимодействует с кодом, ссылающимся на сборку, выполняемую в данный момент. Однако после выполнения инструкции DROP ASSEMBLY любые попытки вызова кода сборки будут безуспешными.  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть владельцем сборки или иметь на нее разрешение CONTROL.  
  
## <a name="examples"></a>Примеры  
 В следующем примере предполагается, что сборка `HelloWorld` уже создана в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
DROP ASSEMBLY Helloworld ;  
```  
  
## <a name="see-also"></a>См. также:  
 [СОЗДАТЬ СБОРКУ &#40; Transact-SQL &#41;](../../t-sql/statements/create-assembly-transact-sql.md)   
 [Инструкцию ALTER ASSEMBLY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-assembly-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Получение сведений о сборках](../../relational-databases/clr-integration/assemblies-getting-information.md)  
  
  
