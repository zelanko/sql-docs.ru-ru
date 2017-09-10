---
title: "Определение установленных пакетов на SQL Server | Документация Майкрософт"
ms.custom: 
ms.date: 08/31/2016
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
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 90e7146bde123ca8ac8a8e6ff3e11d212fd4a35a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="determine-which-packages-are-installed-on-sql-server"></a>Определение установленных пакетов на SQL Server
  Здесь описывается, как определить установленные пакеты R на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
По умолчанию при установке [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] создается библиотека пакетов R, связанная с каждым экземпляром. Таким образом, чтобы узнать, какие пакеты установлены на компьютере, необходимо выполнить соответствующий запрос на каждом экземпляре, где установлены службы R. Обратите внимание, что библиотеки пакетов **не** используются совместно разными экземплярами, поэтому разные пакеты могут быть установлены на разных экземплярах.

Дополнительные сведения об определении расположения библиотеки по умолчанию для экземпляра см. в статье [Установка пакетов R и управление ими](../../advanced-analytics/r-services/installing-and-managing-r-packages.md).   
   
 
## <a name="get-a-list-of-installed-packages-using-r"></a>Получение списка установленных пакетов с помощью R  
 Существует несколько способов получить список установленных или загруженных пакетов с помощью средств и функций R.  
  
+   Многие инструменты разработки R предоставляют обозреватель объектов или список пакетов, которые были установлены или загружены в текущую рабочую область R.  

+ Мы советуем использовать следующие функции из пакета RevoScaleR, предоставляемые специально для управления пакетами в контекстах вычислений:
  - [rxFindPackage](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxfindpackage);
  - [rxInstalledPackages](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxinstalledpackages).   
  
+   Можно использовать функцию R, например `installed.packages()`, содержащуюся в установленном пакете `utils` . Функция проверяет файлы DESCRIPTION каждого пакета, который был найден в указанной библиотеке, и возвращает таблицу с именами пакетов, путями к библиотекам и номерами версий.  
 
### <a name="examples"></a>Примеры  
В следующем примере используется функция `rxInstalledPackages` для получения списка пакетов, доступных в указанном контексте вычислений SQL Server.

~~~~
sqlServerCompute <- RxInSqlServer(connectionString = 
"Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
     sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
     sqlPackages
~~~~

 В приведенном ниже примере используется базовая функция R `installed.packages()` в хранимой процедуре [!INCLUDE[tsql](../../includes/tsql-md.md)], чтобы получить таблицу пакетов, которые были установлены в библиотеке R_SERVICES для текущего экземпляра. Чтобы избежать анализа полей в файле DESCRIPTION, возвращается только имя.  
  
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
  
 Описание необязательных полей и полей по умолчанию для файла DESCRIPTION пакета R см. по адресу [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).  
  
## <a name="see-also"></a>См. также:  
 [Установка дополнительных пакетов R на SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)  
  
  

