---
title: "Определить, какие пакеты R установлены на сервере SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a7f7e43-b568-406c-9434-5a2ec64ec5f5
caps.latest.revision: "11"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: e76a42ead115c8ee4fa89599b192d722ecfbb2ee
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="determine-which-r-packages-are-installed-on-sql-server"></a>Определить, какие пакеты R установлены на сервере SQL Server

При установке машинного обучения в SQL Server с параметром языка R, библиотеки пакета R создается специально для использования в экземпляре. Каждый экземпляр сервера имеет собственную библиотеку пакета. Пакет библиотеки не могут использоваться совместно экземпляров.

В этой статье описывается, как определить, какие пакеты R установлены для указанного экземпляра SQL Server.

## <a name="generate-r-package-list-using-a-stored-procedure"></a>Создать список пакетов R, с помощью хранимой процедуры

В следующем примере используется функция R `installed.packages()` в [!INCLUDE [tsql](..\..\includes\tsql-md.md)] хранимую процедуру, чтобы получить таблицу пакетов, которые были установлены в библиотеке R_SERVICES для текущего экземпляра. Чтобы избежать анализа полей в файле DESCRIPTION, возвращается только имя.

```SQL
EXECUTE sp_execute_external_script
@language=N'R'
,@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
NameOnly <- packagematrix[,1];
OutputDataSet <- as.data.frame(NameOnly);'
, @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250) ))
```

Дополнительные сведения о необязательный и поля по умолчанию для поля ОПИСАНИЯ пакета R см. в разделе [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).

## <a name="verify-whether-a-package-is-installed-with-an-instance"></a>Проверьте, установлен ли пакет с помощью экземпляра

Если вы установили пакет и хотели бы убедиться, что он доступен для конкретного экземпляра SQL Server, можно выполнить следующий вызов хранимой процедуры для загрузки пакета и вернуть только сообщения. В этом примере ищет и загружает библиотеку RevoScaleR, если он доступен.

```sql
EXEC sp_execute_external_script  @language =N'R',
@script=N'library("RevoScaleR")'
GO
```

+ Если найти пакет, будет возвращено сообщение: «Команд выполнена успешно».

+ Если найти или загрузить пакет невозможно, возникает ошибка, содержащий текст: «не найден пакет, который называется «MissingPackageName»»

## <a name="get-a-list-of-installed-packages-using-r"></a>Получение списка установленных пакетов с помощью R

Существует несколько способов получить список установленных или загруженных пакетов с помощью средств и функций R. Многие инструменты разработки R предоставляют обозреватель объектов или список пакетов, которые были установлены или загружены в текущую рабочую область R. Этот раздел содержит некоторые коротких команд, которые можно использовать из командной строки R или в пакете обновления\_выполнение\_внешних\_сценария.

+ Из локальной программу R, используйте базовая функция R, например `installed.packages()`, который входит в `utils` пакета. Чтобы получить список, который является точным для экземпляра, необходимо явно указать путь к библиотеке или использовать средства R, связанных с библиотекой экземпляра.

+ Чтобы проверить пакет в контексте конкретного вычислений, можно использовать следующие функции из пакета RevoScaleR. Эти функции помогают идентифицировать пакетов в контексте указанной вычислений:

+ [rxFindPackage](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxfindpackage);

+ [rxInstalledPackages](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxinstalledpackages).

Например выполните следующий код R для получения списка пакетов, доступных в заданном контексте вычислений SQL Server.

```r
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
sqlPackages
```

## <a name="get-library-location-and-version"></a>Получить расположение библиотеки и версии

Следующий пример возвращает расположение библиотеки в локальном контексте и версия пакета RevoScaleR.

```r
rxFindPackage(RevoScaleR, "local")
packageVersion("RevoScaleR")
```

## <a name="determine-path-of-library-used-by-sql-server"></a>Определить путь к библиотеке, используемый сервером SQL Server

Если вы обновили машинного обучения компонентов с помощью привязки, путь к библиотеке R может измениться. В этом случае предыдущих ярлыки средств R может ссылаться на более ранней версии. Чтобы версии путь и пакета, используемый сервером SQL Server, можно выполнить команду, подобную следующей:

```sql
EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    sql_r_path <- rxSqlLibPaths("local")
      print(sql_r_path)
    version_info <-packageVersion("RevoScaleR")
      print(version_info)'
```

**Результаты**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.2.1'
```
## <a name="see-also"></a>См. также:

[Установка дополнительных пакетов R в SQL Server](install-additional-r-packages-on-sql-server.md)
