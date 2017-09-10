---
title: "Создание локального репозитория пакетов с помощью miniCRAN | Документация Майкрософт"
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27f2a1ce-316f-4347-b206-8a1b9eebe90b
caps.latest.revision: 4
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e8af93b3e132290eef4b43da568b9381ff8e5a04
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-a-local-package-repository-using-minicran"></a>Создание локального репозитория пакетов с помощью miniCRAN
Эта статья содержит сведения о создании локального репозитория пакетов R с помощью пакета R **miniCRAN**. 

Экземпляры [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] обычно размещаются на сервере, который не подключен к Интернету, поэтому стандартный способ установки пакетов R (с помощью команды R `install.packages()`) может не работать, так как установщик пакетов не может получить доступ к CRAN или другим зеркальным сайтам.

Существует два варианта установки пакетов из локальной папки или репозитория:

+ Создайте необходимый локальный репозиторий пакетов с помощью пакета miniCRAN, а затем выполните установку из этого репозитория. В этой статье описывается метод с использованием miniCRAN.

+ Скачайте необходимые пакеты и их зависимости в виде ZIP-файлов, сохраните их в локальной папке, а затем скопируйте эту папку на компьютер [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Дополнительные сведения о методе копирования вручную см. в статье [Установка дополнительных пакетов R на SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md).


## <a name="step-1-install-minicran-and-download-packages"></a>Шаг 1. Установка miniCRAN и скачивание пакетов 


1. Установите пакет miniCRAN на компьютер, имеющий доступ к Интернету.

   ~~~~
   # Install miniCRAN and igraph

   if(!require("miniCRAN")) install.packages("miniCRAN")
   if(!require("igraph")) install.packages("igraph")
   library(miniCRAN)

   # Define the package source: a CRAN mirror, or an MRAN snapshot
   CRAN_mirror <- c(CRAN = "https://mran.microsoft.com/snapshot/2016-04-01")

   # Define the local download location
   local_repo <- "~/miniCRAN"
   ~~~~

2. Скачайте или установите необходимые пакеты на этот компьютер с помощью скрипта R, приведенного ниже. Таким образом, будет создана структура папки, которая потребуется позже для копирования пакетов в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

   ~~~~
   # List the packages to get. Do not specify dependencies.
   pkgs_needed <- c("ggplot2", "ggdendro")
   # Plot the dependency graph 
   plot(makeDepGraph(pkgs_needed)) 
   
   # Create the local repo 
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror) 
   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.2") 

   # List local packages 
   pdb <- as.data.frame( 
     pkgAvail(local_repo, type = "win.binary", Rversion = "3.2"),  
     stringsAsFactors = FALSE) 
   head(pdb) 
   pdb$Package 
   pdb[, c("Package", "Version", "License")] 
   ~~~~


## <a name="step-2-copy-the-minicran-repository-to-the-sql-server-computer"></a>Шаг 2. Копирование репозитория miniCRAN на компьютер SQL Server 

Скопируйте репозиторий miniCRAN в библиотеку R_SERVICES экземпляра [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

+ Для SQL Server 2016 по умолчанию используется папка `C:/Program Files/Microsoft SQL Server/MSSQL13.MSSQLSERVER/R_SERVICES/library1`.
+ Папка по умолчанию для 2017 г. SQL Server — `C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library1`.

Если вы установили службы R с помощью именованного экземпляра, не забудьте включить в путь его имя, чтобы обеспечить установку библиотеки на правильный экземпляр. Например, если именованный экземпляр имеет имя RTEST02, по умолчанию для него будет использоваться путь `C:\Program Files\Microsoft SQL Server\MSSQL13.RTEST02\R_SERVICES\library`.

Если вы установили SQL Server на другой диск или внесли другие изменения, касающиеся пути установки, не забудьте отразить их.

## <a name="step-3-install-the-packages-on-sql-server-using-the-minicran-repository"></a>Шаг 3. Установка пакетов на SQL Server с помощью репозитория miniCRAN

На компьютере [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] откройте командную строку R или RGUI с правами администратора. 
  
> [!TIP]
> Компьютер может содержать несколько библиотек R. Чтобы пакеты были установлены на правильном экземпляре, используйте копию RGUI или RTerm конкретного экземпляра, на котором необходимо установить пакеты.
  
Когда вам будет предложено указать репозиторий, выберите папку, содержащую только что скопированные файлы, то есть локальный репозиторий miniCRAN.

   ~~~~
   # Run this R code as administrator on the SQL Server computer 
   pkgs_needed <- c("ggplot2", "ggdendro") 
   local_repo  <- "~/miniCRAN" 

   # OPTIONAL: If you are not running R from the instance library as recommended, you must specify the path
   #   .libPaths()[1] 
   # "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library " 
   # lib <- .libPaths()[1]
   
   install.packages(pkgs_needed,  
                    repos = file.path("file://", normalizePath(local_repo, winslash = "/")), 
                    lib = lib, 
                    type = "win.binary", 
                    dependencies = TRUE 
                    ) 
   installed.packages() 
   ~~~~

Убедитесь, что пакеты установлены.
   ~~~~
   installed.packages()
   ~~~~



## <a name="acknowledgements"></a>Подтверждения

Эта статья основана на статье Андре де Врие (Andre de Vries), одного из разработчиков пакета miniCRAN. Дополнительные сведения и пошаговое руководство см. в статье [How to install R packages on an off-line SQL Server 2016 instance](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html) (Как установить пакеты R в автономном экземпляре SQL Server 2016).

