---
title: "Установка пакетов R и управление ими | Документация Майкрософт"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ae30bfc42e42b69158dbba5a38b0bccbe93523b4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="installing-and-managing-r-packages"></a>Установка пакетов R и управление ими
 Любое решение R, выполняющееся в [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], должно использовать пакеты, установленные в библиотеке R по умолчанию. Чаще всего решения R ссылаются на библиотеки пользователя, указывая путь к файлу в коде R, что не рекомендуется для рабочей среды.

Таким образом, за установку всех необходимых пакетов в экземпляре [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] отвечает администратор базы данных или другой администратор сервера. Если у вас нет прав администратора на компьютере, где размещен экземпляр [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], вы можете предоставить администратору общие сведения об установке пакетов R, а также доступ к защищенному репозиторию пакетов, где можно получить пакеты, запрашиваемые пользователями. Все это подробно описано здесь. 

> [!TIP]
> [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] предоставляет новые функции установки пакетов и управления ими, что дает администратору базы данных и специалисту по обработке и анализу данных большую свободу и контроль над использованием пакетов и их установкой. Дополнительные сведения см. в статье [Управление пакетами R для служб R SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md). 

## <a name="installed-packages"></a>Устанавливаемые пакеты
При установке [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] по умолчанию устанавливаются **базовые** пакеты R, например `stats` и `utils`. Они устанавливаются вместе с пакетом **RevoScaleR**, который поддерживает подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 
> [!NOTE]  
>  Список пакетов, устанавливаемых по умолчанию, см. [здесь](https://mran.microsoft.com/rro/installed/).  

 Если вам нужен дополнительный пакет из CRAN или другого репозитория, скачайте его и установите на своей рабочей станции.  
  
 Если необходимо запустить новый пакет в контексте сервера, администратор базы данных должен установить его на сервере.   
   
## <a name="where-and-how-to-get-new-packages"></a>Где и как получить новые пакеты  
 Существует несколько источников R-пакетов, самые известные — CRAN и Bioconductor. На официальном сайте для языка R ([https://www.r-project.org/](https://www.r-project.org/)) перечислены многие такие ресурсы. Кроме того, многие пакеты публикуются на портале GitHub, где можно получить исходный код. Однако вам также могут предоставить R-пакеты, разработанные в вашей организации.  
  
 Независимо от источника пакеты для установки должны быть предоставлены в виде ZIP-архива. Кроме того, чтобы использовать пакет с [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], необходимо получить ZIP-файл в двоичном формате Windows. (Некоторые пакеты не поддерживают этот формат.) Дополнительные сведения о содержимом ZIP-архива и создании пакета R можно найти в [руководстве по созданию пакетов R](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf), подготовленном Фридрихом Ляйшем (Freidrich Leisch). Его можно скачать в формате PDF на сайте проекта R. 
  
 Как правило, пакеты R легко устанавливаются из командной строки без предварительного скачивания, если есть доступ к Интернету.  С серверами под управлением [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] все по-другому.  Таким образом, чтобы установить пакет R на компьютер, на котором **нет** доступа к Интернету, предварительно скачайте пакет в правильном формате ZIP, а затем скопируйте ZIP-файлы в папку, доступную для компьютера. 
 
 В приведенных ниже статьях описываются два способа установки пакетов в автономном режиме. 

+ [Создание автономного репозитория пакетов с помощью miniCRAN](../../advanced-analytics/r-services/create-a-local-package-repository-using-minicran.md)

  Описывается, как использовать **miniCRAN** для пакетов R, чтобы создать автономный репозиторий. Это, вероятно, самый эффективный метод, если вам необходимо установить пакеты на несколько серверов и управлять репозиторием из единого расположения. 
+ [Установка новых пакетов R из Интернета](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)

  Содержатся инструкции по установке пакетов в автономном режиме с помощью копирования ZIP-файлов вручную.   

## <a name="permissions-required-for-installing-r-packages"></a>Разрешения, необходимые для установки R-пакетов  
  
Чтобы установить новый пакет R на компьютере с [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], необходимо иметь права администратора на этом компьютере.   

Если у вас нет этих прав, обратитесь к администратору и предоставьте ему сведения о нужном пакете.  
  

Если вы устанавливаете новый пакет R на компьютере, который используется в качестве рабочей станции R и на котором **не** установлен экземпляр [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], для установки пакета по-прежнему требуются права администратора на компьютере. После установки пакета его можно выполнять локально.  
 
> [!NOTE]
> В [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] добавлены новые роли базы данных, чтобы поддерживать определение разрешений на установку пакетов на уровне экземпляра и базы данных. Дополнительные сведения см. в статье [Управление пакетами R для служб R SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md).
 

### <a name="location-of-default-r-library-location-for-r-services"></a>Расположение библиотеки R по умолчанию для служб R

Если вы установили [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] с помощью экземпляра по умолчанию, библиотека пакетов R, используемая экземпляром, будет находиться в папке экземпляра [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Например: 

+ Экземпляр по умолчанию _MSSQLSERVER_:
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`
+ Именованный экземпляр _MyNamedInstance_:
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library` 


Вы можете выполнить приведенную ниже инструкцию, чтобы проверить библиотеку по умолчанию для текущего экземпляра R. 
~~~~
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
~~~~

Дополнительные сведения см. в статье [Определение установленных пакетов на SQL Server](../../advanced-analytics/r-services/determine-which-packages-are-installed-on-sql-server.md).

## <a name="managing-installed-packages"></a>Управление установленными пакетами

[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] предоставляет новые функции установки пакетов и управления ими, что дает администратору базы данных и специалисту по обработке и анализу данных большую свободу и контроль над использованием пакетов и их установкой. Дополнительные сведения см. в статье [Управление пакетами R для служб R SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md). 

Если вы используете службы R SQL Server 2016, новые функции управления пакетами будут пока недоступны. А сейчас, чтобы определить, какие пакеты установлены на компьютере [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], используйте одно из действий, приведенных ниже.

+ Просмотрите библиотеку по умолчанию, если у вас есть доступ к папке.
+ Выполните команду в командной строке R, чтобы получить список пакетов в расположении библиотеки R_SERVICES.
+ Используйте в экземпляре хранимую процедуру, например:
   ```SQL
   EXECUTE sp_execute_external_script  @language=N'R'  
        ,@script = N'str(OutputDataSet);  
        packagematrix <- installed.packages();  
        NameOnly <- packagematrix[,1];  
        OutputDataSet <- as.data.frame(NameOnly);'  
        ,@input_data_1 = N'SELECT 1 as col'  
        WITH RESULT SETS ((PackageName nvarchar(250) ))   
   ```


 ## <a name="see-also"></a>См. также:  
 [Мониторинг решений R и управление ими](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  

