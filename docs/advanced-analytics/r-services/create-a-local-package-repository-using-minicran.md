---
title: "Создание локального пакета репозитория при помощи miniCRAN | Microsoft Docs"
ms.custom: ""
ms.date: "05/27/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27f2a1ce-316f-4347-b206-8a1b9eebe90b
caps.latest.revision: 4
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 4
---
# Создание локального пакета репозитория при помощи miniCRAN
В этом разделе описывается, как можно создать локальный репозиторий пакетов R, с помощью пакета R **miniCRAN**. 

Поскольку [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] экземпляров обычно размещаются на сервере, который не подключен к Интернету, стандартный способ установки пакетов R (команды R `install.packages()`) могут не работать, как пакет установщика не может получать доступ к CRAN или другие узлы зеркальной.

Существует два варианта установки пакетов из локальной папки или репозиторий:

+ Используйте пакет miniCRAN для создания локального репозитория пакетов, вы должны, а затем установить из этого репозитория. В этом разделе описывается метод miniCRAN.

+ Загрузить необходимые пакеты и их зависимости, как ZIP-файлы и сохранять их в локальную папку и скопируйте эту папку для [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] компьютера. Дополнительные сведения о методе ручное копирование см [установить дополнительные пакеты на сервере SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md).


## Шаг 1. Установка miniCRAN и загрузить пакеты 


1. Установите пакет miniCRAN на компьютере, который имеет доступ к Интернету.

   ~~~~
   # Install miniCRAN ---------------------------------------------------

   if(!require("miniCRAN")) install.packages("miniCRAN")
   if(!require("igraph")) install.packages("igraph")
   library(miniCRAN)

   # Define the package source: a CRAN mirror, or an MRAN snapshot
   CRAN_mirror <- c(CRAN = "https://mran.microsoft.com/snapshot/2016-04-01")

   # Define the local download location
   local_repo <- "~/miniCRAN"
   ~~~~

2. Загрузить или установить пакеты, необходимые для этого компьютера. Это создаст структуру папок, необходимо скопировать пакеты [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] позже.

   ~~~~
   # List the packages you need 
   # Do not specify dependencies
   pkgs_needed <- c("ggplot2", "ggdendro")
   ~~~~

3. Скопируйте репозиторий miniCRAN в библиотеке R_SERVICES на [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] экземпляра.

## Шаг 2. Установить пакеты на компьютере SQL Server 

4. На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] компьютере, выполните команду R  `install.packages()`. Можно использовать один из средств R, которые устанавливаются вместе с [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], такие как Rgui.exe, или выполните команду как часть [!INCLUDE[tsql_md](../../includes/tsql-md.md)] хранимой процедуры.
5. В командной строке укажите репозиторий, выберите папку, содержащую файлы были скопированы; хранилище локального miniCRAN.

   ~~~~
   pkgs_needed <- c("ggplot2", "ggdendro")
   local_repo  <- "~/miniCRAN"
   
   .libPaths()[1]
   "C:/Program Files/Microsoft SQL Server/130/R_SERVER/library"

   lib <- .libPaths()[1]

   install.packages(pkgs_needed, 
                 repos = file.path("file://", normalizePath(local_repo, winslash = "/")),
                 lib = lib,
                 type = "win.binary",
                 dependencies = TRUE
                 )
   ~~~~

6. Убедитесь, что нужные пакеты были установлены при выполнении этого кода.
   ~~~~
   installed.packages()
   ~~~~



## Подтверждения

Источник для получения этих сведений — этой статье Андре де Врие разработчиком miniCRAN пакета. Дополнительные сведения и полный пример см. в разделе  [пакеты как установить R на автономный экземпляр SQL Server 2016](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html)