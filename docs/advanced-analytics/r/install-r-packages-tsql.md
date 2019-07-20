---
title: Использование T-SQL (создание внешней библиотеки) для установки пакетов R
description: Добавьте новые пакеты R в службы SQL Server 2016 R или SQL Server 2017 Службы машинного обучения (в базе данных).
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/12/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: f681634b9f57a5fd459e3f6452c04aba024bd297
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345313"
---
# <a name="use-t-sql-create-external-library-to-install-r-packages-on-sql-server"></a>Использование T-SQL (создание внешней библиотеки) для установки пакетов R на SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье объясняется, как установить новые пакеты R на экземпляре SQL Server, где включено машинное обучение. Существует несколько подходов к выбору. Использование T-SQL лучше подходит администраторам сервера, которые не знакомы с R.

**Применимо к:** [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)]  [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Инструкция [CREATE External Library](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) позволяет добавить пакет или набор пакетов в экземпляр или конкретную базу данных без непосредственного запуска кода R или Python. Однако этот метод требует подготовки пакета и дополнительных разрешений базы данных.

+ Все пакеты должны быть доступны в виде локального ZIP-файла, а не загружаются по запросу из Интернета.

+ Все зависимости должны быть идентифицированы по имени и версии и включаться в ZIP-файл. Инструкция завершается ошибкой, если требуемые пакеты недоступны, включая подчиненные зависимости пакетов. 

+ Необходимо иметь разрешение **db_owner** или обладать разрешением на создание внешней библиотеки в роли базы данных. Дополнительные сведения см. в разделе [Создание внешней библиотеки](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="download-packages-in-archive-format"></a>Скачать пакеты в формате архива

При установке одного пакета Скачайте пакет в формате ZIP.

Чаще всего устанавливается несколько пакетов из-за зависимостей пакетов. Если пакету требуются другие пакеты, необходимо убедиться, что все они доступны во время установки. Рекомендуется [создать локальный репозиторий](create-a-local-package-repository-using-minicran.md) с помощью [miniCRAN](https://andrie.github.io/miniCRAN/) , чтобы собрать полную коллекцию пакетов, а также [ИГРАФ](https://igraph.org/r/) для анализа зависимостей пакетов. Установка неверной версии пакета или пропуск зависимости пакета может привести к сбою инструкции CREATE EXTERNAL LIBRARY. 

## <a name="copy-the-file-to-a-local-folder"></a>Копирование файла в локальную папку

Скопируйте сжатый ZIP-файл, содержащий все пакеты, в локальную папку на сервере. Если у вас нет доступа к файловой системе на сервере, можно также передать полный пакет в виде переменной, используя двоичный формат. Дополнительные сведения см. в разделе [Создание внешней библиотеки](../../t-sql/statements/create-external-library-transact-sql.md).

## <a name="run-the-statement-to-upload-packages"></a>Выполнение инструкции для отправки пакетов

Откройте окно **запроса** , используя учетную запись с правами администратора.

Выполните инструкцию `CREATE EXTERNAL LIBRARY` T-SQL, чтобы отправить упакованную ZIP-коллекцию пакетов в базу данных.

Например, следующие инструкции наименают в качестве источника пакета репозиторий miniCRAN, содержащий пакет **randomForest** , а также его зависимости. 

```sql
CREATE EXTERNAL LIBRARY randomForest
FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
WITH (LANGUAGE = 'R');
```

Нельзя использовать произвольное имя; имя внешней библиотеки должно иметь то же имя, которое вы планируете использовать при загрузке или вызове пакета.

## <a name="verify-package-installation"></a>Проверка установки пакета

Если библиотека создана успешно, можно запустить пакет в SQL Server, вызвав его внутри хранимой процедуры.
    
```sql
EXEC sp_execute_external_script
@language =N'R',
@script=N'library(randomForest)'
```

## <a name="see-also"></a>См. также

+ [Получение сведений о пакете](../package-management/installed-package-information.md)
+ [Учебники по R](../tutorials/sql-server-r-tutorials.md)
