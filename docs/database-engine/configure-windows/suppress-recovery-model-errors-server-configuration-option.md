---
description: Подавление ошибок модели восстановления — параметр конфигурации сервера
title: Подавление ошибок модели восстановления — параметр конфигурации сервера | Документация Майкрософт
ms.custom: ''
ms.date: 07/20/2020
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 942dfc62bd55d1843babb78d89b95ad602f3d938
ms.sourcegitcommit: 2f868a77903c1f1c4cecf4ea1c181deee12d5b15
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2020
ms.locfileid: "91670747"
---
# <a name="suppress-recovery-model-errors-server-configuration-option"></a>Параметр конфигурации сервера для подавления ошибок модели восстановления

[!INCLUDE[tsql-appliesto-xxxxxx-asdbmi-xxxx-xxx-md.md](../../includes/tsql-appliesto-xxxxxx-asdbmi-xxxx-xxx-md.md)]

[Модели восстановления](../../relational-databases/backup-restore/recovery-models-sql-server.md) SQL Server управляют обслуживанием журнала транзакций. Модель полного восстановления гарантирует, что никакая работа не будет потеряна из-за потерянного или поврежденного файла данных, и поддерживает восстановление на произвольный момент времени в рамках политики хранения резервных копий. Модель полного восстановления используется по умолчанию и является единственной моделью восстановления, поддерживаемой в Управляемом экземпляре SQL. При попытке изменить модель восстановления в Управляемом экземпляре SQL будет возвращено сообщение об ошибке.

Используйте дополнительный параметр конфигурации **suppress recovery model errors**, чтобы указать, будут ли команды для изменения модели восстановления базы данных, выполняемые в Управляемом экземпляре SQL, возвращать только предупреждение или ошибку. Если для этого параметра задано значение 1 (включен) в Управляемом экземпляре SQL, выполнение команды ALTER DATABASE SET RECOVERY не приведет к изменению модели восстановления базы данных, но при этом будет возвращено не сообщение об ошибке, а предупреждение. Если для этого параметра задано значение 0 (отключен) в Управляемом экземпляре SQL, при выполнении команды ALTER DATABASE SET RECOVERY будет возвращено сообщение об ошибке.

Параметр **suppress recovery model errors** полезен в случаях, когда устаревшие или сторонние приложения пытаются изменить модель восстановления на простое или неполное протоколирование, даже если это не критическое или обязательное требование. Если изменение модели восстановления является единственным препятствием для использования Управляемого экземпляра SQL, включение параметра конфигурации для подавления ошибок модели восстановления позволяет устранить его. Этот параметр особенно полезен, если альтернативное решение для изменения кода приложения нецелесообразно или недоступно.

## <a name="examples"></a>Примеры

Следующий пример включает подавление сообщений об ошибках, связанных с изменением модели восстановления базы данных, а затем выполняет команду для изменения модели восстановления базы данных, возвращая только предупреждение. Сама модель восстановления не изменяется. Не забудьте заменить *my_database* фактическим именем базы данных.

```sql
-- Turn advanced configuration options on:
sp_configure 'show advanced options', 1 ;  
GO
RECONFIGURE ;  
GO

-- Enable suppression of error messages for recovery model change:
sp_configure 'suppress recovery model errors', 1 ;  
GO
RECONFIGURE ;  
GO

-- Execute command for changing recovery model to Simple:
ALTER DATABASE my_database SET RECOVERY SIMPLE;
GO
```

## <a name="see-also"></a>См. также раздел

[Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)

[sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)

[RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)