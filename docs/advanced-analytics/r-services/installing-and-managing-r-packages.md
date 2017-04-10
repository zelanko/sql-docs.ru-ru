---
title: "Установка и управление пакетами R | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# Установка и управление пакетами R
 Любое решение R, работающий в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] необходимо использовать пакеты, установленные в библиотеке R по умолчанию. Как правило R решения будет ссылаться на библиотеки пользователя, указав путь к файлу в код R, но это не рекомендуется для рабочей среды.

Таким образом, это задача, администратор базы данных или другого администратора на сервере, чтобы убедиться, что установлены все необходимые пакеты на [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] экземпляра. Если у вас права администратора на компьютере, на котором размещена [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]  экземпляр, можно предоставлять данные администратора о том, как устанавливать пакеты R и предоставления доступа к безопасной пакета репозитория, где можно получить пакеты, необходимые пользователям. В этом разделе обеспечивает такую информацию. 

> [!TIP]
> [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] предоставляет новые возможности для установки и управления пакетами R, которые предоставляют администратору базы данных и большую свободу по обработке и анализу данных и контролировать использование пакета и программы установки. Дополнительные сведения см. в разделе [R пакет управления для SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md). 

## <a name="installed-packages"></a>Установленные пакеты
При установке  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)],  по умолчанию R **базового** устанавливаются пакеты, такие как `stats` и `utils`, вместе с **RevoScaleR** пакет, который поддерживает подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 
> [!NOTE]  
>  Список пакетов, установленных по умолчанию см. в разделе [пакетов устанавливается вместе с Microsoft R Open](https://mran.microsoft.com/rro/installed/).  

 Если требуется дополнительный пакет из CRAN или другой репозиторий, необходимо загрузить пакет и установить его на рабочей станции.  
  
 Если необходимо запустить новый пакет в контексте сервера, администратор должен установить его на сервере.   
   
## <a name="where-and-how-to-get-new-packages"></a>Где и как получить новые пакеты  
 Существует несколько источников R-пакетов, самые известные — CRAN и Bioconductor. Официальный сайт языка R ([https://www.r-project.org/](https://www.r-project.org/)) перечислены многие из этих ресурсов. Кроме того, многие пакеты публикуются на портале GitHub, где можно получить исходный код. Однако вам также могут предоставить R-пакеты, разработанные в вашей организации.  
  
 Независимо от источника пакеты для установки должны быть предоставлены в виде ZIP-архива. Кроме того чтобы использовать пакет с [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], не забудьте получить ZIP-файл в двоичном формате Windows. (Некоторые пакеты могут не поддерживать этот формат). Дополнительные сведения о содержимом файловый формат zip, и как создать пакет R, мы рекомендуем этого учебника, который можно загрузить в формате PDF из узла проекта R: [Freidrich Leisch: создание пакетов R](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf). 
  
 Как правило пакеты R можно установить легко из командной строки без загрузки их заранее, если компьютер имеет доступ к Интернету.  Обычно это не так с серверами, использующими [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] .  Таким образом Чтобы установить пакет R на компьютер, выполняющий **не** имеют доступ к Интернету, необходимо загрузить пакет в правильном формате ZIP-заранее и скопируйте ZIP-файлы в папку, доступную на компьютере. 
 
 В следующих разделах описываются два способа установки пакетов в автономном режиме: 

+ [Создание автономных пакетов репозитория с помощью miniCRAN](../../advanced-analytics/r-services/create-a-local-package-repository-using-minicran.md)

  Описывает, как использовать пакет R **miniCRAN** для создания автономного хранилища. Это, вероятно, наиболее эффективный метод, если требуется установить пакеты на несколько серверов и управление хранилище из одного места. 
+ [Установка новых пакетов R из Интернета](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)

  Приводятся инструкции по установке пакетов в автономном режиме путем ручного копирования ZIP-файлов.   

## <a name="permissions-required-for-installing-r-packages"></a>Разрешения, необходимые для установки R-пакетов  
  
Чтобы установить новый R-пакет на компьютере, на котором выполняется [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], необходимо иметь права администратора на этом компьютере.   

Если у вас нет этих прав, обратитесь к администратору и предоставьте ему сведения о нужном пакете.  
  

Если вы устанавливаете новый пакет R на компьютере, который используется R рабочей станции и выполняется **не** в экземпляре [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] установлен, по-прежнему требуется права администратора на компьютере для установки пакета. После установки пакета его можно выполнять локально.  
 
> [!NOTE]
> В [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)], были добавлены новые роли базы данных для поддержки области видимости пакета установки разрешений на уровне экземпляра и базы данных. Дополнительные сведения см. в разделе [R пакет управления для SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md).
 

### <a name="location-of-default-r-library-location-for-r-services"></a>Место расположения библиотеки по умолчанию R для служб R

Если вы установили  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] экземпляра по умолчанию, библиотеки пакет R, используемые экземпляром находится в [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] папку экземпляра. Например: 

+ Экземпляр по умолчанию _MSSQLSERVER_
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`
+ Именованный экземпляр _Мойименованныйэкземпляр_
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library` 


Можно выполнить следующую инструкцию, чтобы проверить библиотеки по умолчанию для текущего экземпляра R. 
~~~~
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
~~~~

Дополнительные сведения см. в разделе [определить, что пакеты устанавливаются на сервере SQL Server](../../advanced-analytics/r-services/determine-which-packages-are-installed-on-sql-server.md).

## <a name="managing-installed-packages"></a>Управление установленных пакетов

[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] предоставляет новые возможности для установки и управления пакетами R, которые предоставляют администратору базы данных и большую свободу по обработке и анализу данных и контролировать использование пакета и программы установки. Дополнительные сведения см. в разделе [R пакет управления для SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md). 

При использовании служб SQL Server 2106 R новые возможности пакета управления доступны не в данный момент. В то же время, что у вас есть эти параметры для определения, какие пакеты установлены на [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] компьютере, используйте один из следующих вариантов:

+ Просмотр библиотеки по умолчанию, при наличии разрешений на папку.
+ Выполнение команды из команды R для перечисления пакетов в расположение библиотеки R_SERVICES
+ На экземпляре, используйте хранимую процедуру как показано ниже:
   ```SQL
   EXECUTE sp_execute_external_script  @language=N'R'  
        ,@script = N'str(OutputDataSet);  
        packagematrix <- installed.packages();  
        NameOnly <- packagematrix[,1];  
        OutputDataSet <- as.data.frame(NameOnly);'  
        ,@input_data_1 = N'SELECT 1 as col'  
        WITH RESULT SETS ((PackageName nvarchar(250) ))   
   ```


 ## <a name="see-also"></a>См. также  
 [Управление и мониторинг R решения](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  