---
title: Позволяет установить пакеты R на службы обучения машины SQL Server T-SQL (Создание ВНЕШНЕЙ БИБЛИОТЕКИ) | Документы Microsoft
description: Добавление новых пакетов R обучения машины службы (в базе данных) для SQL Server 2017 г.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/20/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: bbc1adf4868cbfbd02afe5cae3a38fd6223e2d4d
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="use-t-sql-create-external-library-to-install-r-packages-on-sql-server-2017-machine-learning-services"></a>Используйте T-SQL (Создание ВНЕШНЕЙ БИБЛИОТЕКИ) для установки R-пакетов в службах SQL Server 2017 г. машин обучения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается установка нового R-пакетов в экземпляр SQL Server, где включена машинного обучения. Существует несколько подходов для выбора. Такой подход лучше всего подходит для администраторов сервера, не знакомых с R.

**Область применения:**  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

[Создать ВНЕШНЮЮ БИБЛИОТЕКУ](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) инструкция делает возможным добавление пакета или набора пакетов экземпляра или определенной базы данных без выполнения R или Python code напрямую. Однако этот метод требует подготовки пакета и разрешения дополнительные базы данных.

+ Все пакеты должны быть доступны в качестве локальный ZIP-файл, а не загружаться по запросу из Интернета.

+ Все зависимости необходимо определить по имени и версии и включены в ZIP-файл. Выполнение инструкции завершается неудачно, если требуемые пакеты недоступны, включая зависимости пакетов подчиненных. 

+ Необходимо иметь соответствующие разрешения в базе данных. Дополнительные сведения см. в разделе [создать ВНЕШНЮЮ БИБЛИОТЕКУ](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="download-packages-in-archive-format"></a>Загрузить пакеты в формате архива

При установке одного пакета, загрузите пакет в ZIP-формате.

Если пакет требует любых других пакетов, необходимо убедиться, что доступны необходимые пакеты. MiniCRAN можно использовать для анализа целевой пакет и определения его зависимостей. Мы рекомендуем использовать [ **miniCRAN** ](create-a-local-package-repository-using-minicran.md) или [ **igraph** ](http://igraph.org/r/) для анализа зависимостей пакетов. Установка Неверная версия пакета или зависимость пакета также может вызвать ошибку выполнения инструкции. 

## <a name="copy-the-file-to-a-local-folder"></a>Скопируйте файл в локальную папку

Скопируйте ZIP-файл, содержащий все пакеты в локальную папку на сервере. Если на сервере нет доступа к файловой системе, можно также передать полный пакет как переменную, с использованием двоичного формата. Дополнительные сведения см. в разделе [создать ВНЕШНЮЮ БИБЛИОТЕКУ](../../t-sql/statements/create-external-library-transact-sql.md).

## <a name="run-the-statement-to-upload-packages"></a>Выполните инструкцию, чтобы отправить пакеты

Откройте **запроса** окно, используя учетную запись с правами администратора.

Выполните инструкцию T-SQL `CREATE EXTERNAL LIBRARY` для передачи коллекции ZIP-пакета в базе данных.

    For example, the following statement names as the package source a miniCRAN repository containing the **randomForest** package, together with its dependencies. 

    ```R
    CREATE EXTERNAL LIBRARY randomForest
    FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
    WITH (LANGUAGE = 'R');
    ```

    You cannot use an arbitrary name; the external library name must have the same name that you expect to use when loading or calling the package.

## <a name="verify-package-installation"></a>Проверка установки пакета

Если библиотеке успешно создан, можно запускать пакет в SQL Server, путем вызова внутри хранимой процедуры.
    
    ```SQL
    EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    library(randomForest)'
    ```

