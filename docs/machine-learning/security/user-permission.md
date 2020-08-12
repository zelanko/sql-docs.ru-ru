---
title: Предоставление разрешений на выполнение скриптов Python и R
description: Узнайте, как предоставлять пользователям разрешения на выполнение внешних скриптов Python и R в Службах машинного обучения SQL Server и предоставление разрешений на чтение, запись или инструкции на языке описания данных (DDL) для баз данных.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 06/03/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019, contperfq4
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: da601b8c83e6e226da0329ec8d8c732d9877656a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775360"
---
# <a name="grant-users-permission-to-execute-python-and-r-scripts-with-sql-server-machine-learning-services"></a>Предоставление пользователям разрешения на выполнение скриптов Python и R с помощью Службы машинного обучения SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Узнайте, как предоставлять пользователям разрешения на выполнение внешних скриптов Python и R в [Службах машинного обучения SQL Server](../sql-server-machine-learning-services.md) и предоставление разрешений на чтение, запись или инструкции на языке описания данных (DDL) для баз данных.

Дополнительные сведения см. в подразделе "Разрешения" раздела [Общие сведения о безопасности для платформы расширяемости](../../machine-learning/concepts/security.md#permissions).

<a name="permissions-external-script"></a>

## <a name="permission-to-run-scripts"></a>Разрешение на выполнение скриптов

Каждому пользователю, запускающему скрипты Python или R со Службами машинного обучения SQL Server и не являющемуся администратором, необходимо предоставить разрешение на выполнение внешних скриптов в каждой базе данных, где используется этот язык.

Чтобы предоставить разрешение на выполнение внешнего скрипта, выполните следующий скрипт:

```sql
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT TO [UserName]
```

> [!NOTE]
> Разрешения не относятся к конкретному поддерживаемому языку скриптов. Иными словами, не существует отдельных уровней разрешений для скриптов R и скриптов Python.

<a name="permissions-db"></a>

## <a name="grant-databases-permissions"></a>Предоставление разрешений на базу данных

Когда пользователь выполняет скрипты, ему может потребоваться считывать данные из других баз данных. Пользователю также может потребоваться создавать новые таблицы для хранения результатов и записывать данные в таблицы.

Необходимо убедиться, что у каждой учетной записи пользователя Windows или имени входа SQL, выполняющего скрипты R или Python, имеются соответствующие разрешения для конкретной базы данных: 

+ `db_datareader` для чтения данных.
+ `db_datawriter` для сохранения объектов в базе данных.
+ `db_ddladmin` для создания таких объектов, как хранимые процедуры или таблицы, содержащие обученные и сериализованные данные.

Например, приведенная ниже инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] предоставляет имени входа SQL *MySQLLogin* права на выполнение запросов T-SQL в базе данных *ML_Samples*. Для выполнения этой инструкции имя входа SQL уже должно существовать в контексте безопасности сервера.

```sql
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о разрешениях, включенных в каждую роль, см. в разделе [Роли уровня базы данных](../../relational-databases/security/authentication-access/database-level-roles.md).
