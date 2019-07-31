---
ms.openlocfilehash: 327fd6bac9bc1036a0dd07f7b955ee92cb7e40c8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68223543"
---
  Начиная с SQL Server 2005 поведение схем изменилось. В результате программный код, предполагающий, что схемы эквивалентны пользователям базы данных, возможно, не будет более возвращать правильные результаты. Старые представления каталога, включая sysobjects, не должны использоваться в той базе данных, где когда-либо выполнялась любая из следующих инструкций DDL: CREATE SCHEMA, ALTER SCHEMA, DROP SCHEMA, CREATE USER, ALTER USER, DROP USER, CREATE ROLE, ALTER ROLE, DROP ROLE, CREATE APPROLE, ALTER APPROLE, DROP APPROLE, ALTER AUTHORIZATION. В таких базах данных необходимо использовать новые представления каталога. Новые представления каталога учитывают разделение участников и схем, введенное в SQL Server 2005. Дополнительные сведения о представлениях каталогов см. в статье [Представления системных каталогов (Transact-SQL)](../relational-databases/system-catalog-views/catalog-views-transact-sql.md).
   