---
title: Позволяет установить пакеты R на службы обучения машины SQL Server T-SQL (Создание ВНЕШНЕЙ БИБЛИОТЕКИ) | Документы Microsoft
description: Добавление новых пакетов R обучения машины службы (в базе данных) для SQL Server 2017 г.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/30/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7a5a0c394e9a26244661a4ae712d20583c1f1c99
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/02/2018
ms.locfileid: "34585486"
---
# <a name="use-t-sql-create-external-library-to-install-r-packages-on-sql-server-2017-machine-learning-services"></a>Используйте T-SQL (Создание ВНЕШНЕЙ БИБЛИОТЕКИ) для установки R-пакетов в службах SQL Server 2017 г. машин обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается установка нового R-пакетов в экземпляре SQL Server, где включена машинного обучения. Существует несколько подходов для выбора. С помощью T-SQL лучше всего подходит для администраторов сервера, не знакомых с R.

**Область применения:**  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

[Создать ВНЕШНЮЮ БИБЛИОТЕКУ](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) инструкция делает возможным добавление пакета или набора пакетов экземпляра или определенной базы данных без выполнения R или Python code напрямую. Однако этот метод требует подготовки пакета и разрешения дополнительные базы данных.

+ Все пакеты должны быть доступны как локальный ZIP-файл, а не загруженные по запросу из Интернета.

+ Все зависимости необходимо определить по имени и версии и включены в ZIP-файл. Выполнение инструкции завершается неудачно, если требуемые пакеты недоступны, включая зависимости пакетов подчиненных. 

+ Должно быть **db_owner** или иметь разрешение на создание ВНЕШНЕЙ БИБЛИОТЕКИ в роль базы данных. Дополнительные сведения см. в разделе [создать ВНЕШНЮЮ БИБЛИОТЕКУ](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="download-packages-in-archive-format"></a>Загрузить пакеты в формате архива

При установке одного пакета, загрузите пакет в ZIP-формате.

Это чаще всего для установки нескольких пакетов из-за зависимости пакетов. Если пакет требует другие пакеты, необходимо проверить, все они доступны друг с другом во время установки. Мы рекомендуем [Создание локального репозитория](create-a-local-package-repository-using-minicran.md) с помощью [miniCRAN](http://andrie.github.io/miniCRAN/) сборка представляет собой полный набор пакетов, а также [igraph](http://igraph.org/r/) для анализа зависимостей пакетов. Неверная версия пакета установки или пропуск зависимость пакета может привести к ошибке инструкции, создание ВНЕШНЕЙ БИБЛИОТЕКИ. 

## <a name="copy-the-file-to-a-local-folder"></a>Скопируйте файл в локальную папку

Скопируйте ZIP-файл, содержащий все пакеты в локальную папку на сервере. Если на сервере нет доступа к файловой системе, можно также передать полный пакет как переменную, с использованием двоичного формата. Дополнительные сведения см. в разделе [создать ВНЕШНЮЮ БИБЛИОТЕКУ](../../t-sql/statements/create-external-library-transact-sql.md).

## <a name="run-the-statement-to-upload-packages"></a>Выполните инструкцию, чтобы отправить пакеты

Откройте **запроса** окно, используя учетную запись с правами администратора.

Выполните инструкцию T-SQL `CREATE EXTERNAL LIBRARY` для передачи коллекции ZIP-пакета в базе данных.

Например, следующая инструкция называет в качестве источника пакета в репозиторий miniCRAN, содержащее **randomForest** пакет, вместе с его зависимости. 

```SQL
CREATE EXTERNAL LIBRARY randomForest
FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
WITH (LANGUAGE = 'R');
```

Нельзя использовать произвольное имя; Имя внешней библиотеки должен иметь же имя, которое будет использоваться при загрузке или при вызове пакета.

## <a name="verify-package-installation"></a>Проверка установки пакета

Если библиотеке успешно создан, можно запускать пакет в SQL Server, путем вызова внутри хранимой процедуры.
    
```SQL
EXEC sp_execute_external_script
@language =N'R',
@script=N'library(randomForest)'
```

## <a name="see-also"></a>См. также

+ [Получение сведений о пакете](determine-which-packages-are-installed-on-sql-server.md)
+ [Учебники R](../tutorials/sql-server-r-tutorials.md)
+ [Практические руководства](sql-server-machine-learning-tasks.md)