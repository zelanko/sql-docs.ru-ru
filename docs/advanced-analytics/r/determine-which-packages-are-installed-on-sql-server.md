---
title: "Определить, какие пакеты R установлены на сервере SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 10/09/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a7f7e43-b568-406c-9434-5a2ec64ec5f5
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 138368a3ca212cb4c176df57d78d02b6f41c4344
ms.contentlocale: ru-ru
ms.lasthandoff: 10/10/2017

---
# <a name="determine-which-r-packages-are-installed-on-sql-server"></a>Определить, какие пакеты R установлены на сервере SQL Server

При установке машинного обучения в SQL Server с параметром языка R, программа установки создает библиотеку пакет R, связанные с экземпляром. Каждый экземпляр имеет отдельный пакет библиотеки. Пакет библиотеки, **не** совместно используется экземплярами, в этом случае возможно, что разные пакеты для установки на различных экземплярах.

В этой статье описывается, как определить, какие пакеты R устанавливаются для конкретного экземпляра.

## <a name="generate-r-package-list-using-a-stored-procedure"></a>Создать список пакетов R, с помощью хранимой процедуры

В следующем примере используется функция R `installed.packages()` в [!INCLUDE [tsql](..\..\includes\tsql-md.md)] хранимую процедуру, чтобы получить таблицу пакетов, которые были установлены в библиотеке R_SERVICES для текущего экземпляра. Чтобы избежать анализа полей в файле DESCRIPTION, возвращается только имя.

```SQL
EXECUTE sp_execute_external_script
@language=N'R'  
,@script = N'str(OutputDataSet);  
packagematrix <- installed.packages();  
NameOnly <- packagematrix[,1];  
OutputDataSet <- as.data.frame(NameOnly);'  
,@input_data_1 = N'SELECT 1 as col'  
WITH RESULT SETS ((PackageName nvarchar(250) ))  
```

Дополнительные сведения о необязательный и поля по умолчанию для файла ОПИСАНИЯ пакета R см. в разделе [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).

## <a name="verify-whether-a-package-is-installed-with-an-instance"></a>Проверьте, установлен ли пакет с помощью экземпляра

Если вы установили пакет и хотели бы убедиться, что он доступен для конкретного экземпляра SQL Server, можно выполнить следующий вызов хранимой процедуры для загрузки пакета и вернуть только сообщения.

```SQL
EXEC sp_execute_external_script  @language =N'R',
@script=N'library("RevoScaleR")'
GO
```

В этом примере ищет и загружает библиотеку RevoScaleR.

+ Если найти пакет, сообщение, возвращенное должны выглядеть как «Команд выполнена успешно».

+ Если найти или загрузить пакет невозможно, возникает сообщение об ошибке, следующим образом: «произошла ошибка во внешнем сценарии: ошибка в library("RevoScaleR"): не найден пакет называется RevoScaleR»

## <a name="get-a-list-of-installed-packages-using-r"></a>Получение списка установленных пакетов с помощью R

Существует несколько способов получить список установленных или загруженных пакетов с помощью средств и функций R. Многие инструменты разработки R предоставляют обозреватель объектов или список пакетов, которые были установлены или загружены в текущую рабочую область R.

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
## <a name="see-also"></a>См. также:

[Установка дополнительных пакетов R в SQL Server](install-additional-r-packages-on-sql-server.md)

