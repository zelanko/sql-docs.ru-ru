---
title: "Определение установленных пакетов на SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "08/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a7f7e43-b568-406c-9434-5a2ec64ec5f5
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# Определение установленных пакетов на SQL Server
  В этом разделе описывается, как определить, какие пакеты R установлены на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] экземпляра.  
  
По умолчанию при установке [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] создает библиотеку пакет R, связанные с каждым экземпляром. Таким образом чтобы узнать, какие пакеты установлены на компьютере, необходимо запустить этот запрос на каждый отдельный экземпляр, где установлены службы R. Обратите внимание, что пакет библиотеки **не** совместно используется экземплярами, поэтому возможна разные пакеты должны быть установлены на разных экземплярах.

Сведения о том, как определить папку библиотеки по умолчанию для экземпляра в разделе [Установка и управление пакетов R](../../advanced-analytics/r-services/installing-and-managing-r-packages.md).   
   
 
## Получение списка установленных пакетов с помощью R  
 Существует несколько способов получить список установленных или загруженных пакетов, с помощью средства R и R-функции.  
  
+   Многие инструменты разработки R предоставляют обозреватель объектов или список пакетов, которые были установлены или загружены в текущую рабочую область R.  

+ Мы рекомендуем вычислительные из пакета RevoScaleR следующие функции, предоставляемые специально для управления пакетами в контекстах:
  - [rxFindPackage](https://msdn.microsoft.com/microsoft-r/scaler/rxfindpackage)
  - [rxInstalledPackages](https://msdn.microsoft.com/microsoft-r/scaler/rxInstalledPackages)   
  
+   Можно использовать функцию R, например `installed.packages()`, содержащуюся в установленном пакете `utils` . Функция проверяет файлы ОПИСАНИЯ каждого пакета, который был найден в указанной библиотеке и возвращает матрицу имена пакетов, пути к библиотекам и номера версий.  
 
### Примеры  
В следующем примере используется функция `rxInstalledPackages` для получения списка пакетов, доступных в указанный контекст вычисления для SQL Server.

~~~~
sqlServerCompute <- RxInSqlServer(connectionString = 
"Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
     sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
     sqlPackages
~~~~

 В следующем примере используется базовый R-функцию `installed.packages()` в [!INCLUDE[tsql](../../includes/tsql-md.md)] хранимой процедуры для получения матрицы пакетов, которые были установлены в библиотеке R_SERVICES для текущего экземпляра. Чтобы избежать анализа полей в файле DESCRIPTION, возвращается только имя.  
  
```  
EXECUTE sp_execute_external_script  
@language=N'R'  
,@script = N'str(OutputDataSet);  
packagematrix <- installed.packages();  
NameOnly <- packagematrix[,1];  
OutputDataSet <- as.data.frame(NameOnly);'  
,@input_data_1 = N'SELECT 1 as col'  
WITH RESULT SETS ((PackageName nvarchar(250) ))  
```  
  
 Дополнительные сведения о необязательных полей в файле ОПИСАНИЯ пакета R и по умолчанию в разделе [https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file](https://cran.r-project.org/doc/manuals/R-exts.html).  
  
## См. также:  
 [Установка дополнительных R-пакетов в SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)  
  
  