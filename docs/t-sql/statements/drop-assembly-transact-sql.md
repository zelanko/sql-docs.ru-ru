---
title: DROP ASSEMBLY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP ASSEMBLY
- DROP_ASSEMBLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- removing assemblies
- DROP ASSEMBLY statement
- deleting assemblies
- assemblies [CLR integration], removing
- dropping assemblies
- WITH NO DEPENDENTS option
ms.assetid: 452d181a-a8e6-44a3-975d-29966d01b18d
caps.latest.revision: 32
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: eeb5fa894d92c6e7718066b1107ad9ef8e09b8a1
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/04/2018
ms.locfileid: "37780985"
---
# <a name="drop-assembly-transact-sql"></a>DROP ASSEMBLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет сборку и все связанные с ней файлы из текущей базы данных. Сборки создаются с помощью инструкции [CREATE ASSEMBLY](../../t-sql/statements/create-assembly-transact-sql.md) и изменяются с помощью инструкции [ALTER ASSEMBLY](../../t-sql/statements/alter-assembly-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP ASSEMBLY [ IF EXISTS ] assembly_name [ ,...n ]  
[ WITH NO DEPENDENTS ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *IF EXISTS*  
 **Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условное удаление сборки только в том случае, если она уже существует.  
  
 *assembly_name*  
 Имя сборки, которую нужно удалить.  
  
 WITH NO DEPENDENTS  
 Если указано, удаляется только сборка *assembly_name*, и ни одна из зависимых сборок, ссылки на которые в ней содержатся, не удаляется. Если не указано, инструкция DROP ASSEMBLY удаляет *assembly_name* и все зависимые сборки.  
  
## <a name="remarks"></a>Remarks  
 При удалении сборки из базы данных удаляются и все связанные с ней файлы, такие как исходный код и файлы отладки.  
  
 Если ключевое слово WITH NO DEPENDENTS не указано, инструкция DROP ASSEMBLY удаляет *assembly_name* и все зависимые сборки. Если попытка удалить какую-либо зависимую сборку не удается, инструкция DROP ASSEMBLY возвращает ошибку.  
  
 Инструкция DROP ASSEMBLY возвращает ошибку, если на сборку ссылается другая существующая в базе данных сборка или если она используется функциями, процедурами, триггерами, пользовательскими типами или статистическими функциями среды CLR в данной базе данных.  
  
 Инструкция DROP ASSEMBLY не взаимодействует с кодом, ссылающимся на сборку, выполняемую в данный момент. Однако после выполнения инструкции DROP ASSEMBLY любые попытки вызова кода сборки будут безуспешными.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть владельцем сборки или иметь на нее разрешение CONTROL.  
  
## <a name="examples"></a>Примеры  
 В следующем примере предполагается, что сборка `HelloWorld` уже создана в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
DROP ASSEMBLY Helloworld ;  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE ASSEMBLY (Transact-SQL)](../../t-sql/statements/create-assembly-transact-sql.md)   
 [ALTER ASSEMBLY (Transact-SQL)](../../t-sql/statements/alter-assembly-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [Получение сведений о сборках](../../relational-databases/clr-integration/assemblies-getting-information.md)  
  
  
