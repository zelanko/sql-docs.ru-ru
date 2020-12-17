---
title: Использование инструкции T-SQL (CREATE EXTERNAL LIBRARY) для установки пакетов R
description: Добавление новых пакетов R в службы SQL Server 2016 R Services или Службы машинного обучения SQL Server (в базе данных)
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/20/2019
ms.topic: how-to
author: garyericson
ms.author: garye
monikerRange: =sql-server-2017
ms.openlocfilehash: 61917bb0c62bdcbee114843bdd78bde80ae17619
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97471015"
---
# <a name="use-t-sql-create-external-library-to-install-r-packages-on-sql-server"></a>Использование инструкции T-SQL (CREATE EXTERNAL LIBRARY) для установки пакетов R на SQL Server
[!INCLUDE [SQL Server 2017 only](../../includes/applies-to-version/sqlserver2017-only.md)]

В этой статье объясняется, как установить новые пакеты R на экземпляре SQL Server, где включено машинное обучение. Существует несколько подходов. Использование T-SQL лучше подходит администраторам сервера, которые не знакомы с R.

Инструкция [CREATE EXTERNAL LIBRARY](../../t-sql/statements/create-external-library-transact-sql.md) позволяет добавить пакет или набор пакетов в экземпляр или конкретную базу данных без непосредственного запуска кода R или Python. Тем не менее этот метод требует разрешений на подготовку пакета и дополнительных разрешений для базы данных.

+ Все пакеты должны быть доступны в виде локального ZIP-файла. Их не следует загружать по запросу из Интернета.

+ Все зависимости должны быть идентифицированы по имени и версии и быть добавлены в ZIP-файл. Инструкция завершается ошибкой, если требуемые пакеты недоступны, включая подчиненные зависимости пакетов. 

+ У вас должна быть роль **db_owner** или разрешение на создание внешней библиотеки в роли базы данных. Дополнительные сведения см. в статье [CREATE EXTERNAL LIBRARY (Transact-SQL)](../../t-sql/statements/create-external-library-transact-sql.md).

## <a name="download-packages-in-archive-format"></a>Скачивание пакета в формате архива

При установке одного пакета скачайте пакет в формате ZIP.

Чаще всего из-за зависимостей устанавливается несколько пакетов. Если пакету требуются другие пакеты, необходимо убедиться, что все они могут получить доступ друг к другу во время установки. Рекомендуется [создать локальный репозиторий](create-a-local-package-repository-using-minicran.md), используя [miniCRAN](https://andrie.github.io/miniCRAN/) для сборки полной коллекции пакетов и [igraph](https://igraph.org/r/) для анализа зависимостей пакетов. Установка неверной версии пакета или пропуск зависимости пакета может привести к сбою инструкции CREATE EXTERNAL LIBRARY. 

## <a name="copy-the-file-to-a-local-folder"></a>Копирование файла в локальную папку

Скопируйте сжатый ZIP-файл, содержащий все пакеты, в локальную папку на сервере. Если у вас нет доступа к файловой системе на сервере, можно также передать полный пакет в виде переменной, используя двоичный формат. Дополнительные сведения см. в разделе [CREATE EXTERNAL LANGUAGE](../../t-sql/statements/create-external-library-transact-sql.md).

## <a name="run-the-statement-to-upload-packages"></a>Выполнение инструкции для отправки пакетов

Откройте окно **Запрос**, используя учетную запись с правами администратора.

Выполните инструкцию T-SQL `CREATE EXTERNAL LIBRARY`, чтобы отправить ZIP-файл коллекции пакетов в базу данных.

Например, следующий оператор называет в качестве источника пакета репозиторий miniCRAN, содержащий пакет **randomForest**, вместе с его зависимостями. 

```sql
CREATE EXTERNAL LIBRARY [randomForest]
FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
WITH (LANGUAGE = 'R');
```

Нельзя использовать произвольное имя. Имя внешней библиотеки должно соответствовать имени, которое вы планируете использовать при загрузке или вызове пакета.

## <a name="verify-package-installation"></a>Проверка установки пакета

Если библиотека создана успешно, можно запустить пакет в SQL Server, вызвав его внутри хранимой процедуры.
    
```sql
EXEC sp_execute_external_script
@language =N'R',
@script=N'library(randomForest)'
```

## <a name="see-also"></a>См. также раздел

+ [Получение сведений о пакете R](r-package-information.md)
+ [Учебники по R](../tutorials/r-tutorials.md)