---
title: "Службы R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "12/20/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 341e80f5-3b59-4122-bbaa-969d7904297d
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 20
---
# Службы R Services
  Службы R корпорации Майкрософт предоставляют две серверные платформы для интеграции в бизнес-приложения популярного языка R с открытым исходным кодом: **службы R SQL Server (в базе данных)** для интеграции с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и **Microsoft R Server**.  
  
-   **Службы R (в базе данных)**  
  
     [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] предназначены для быстрой разработки, развертывания и ввода в эксплуатацию решений, использующих язык R, платформу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и связанные с ней службы.  
  
     [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] обеспечивают возможности вычислений на основе данных, позволяя коду R выполняться на одном компьютере с базой данных. Они включают в себя службу базы данных, которая выполняется вне процесса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и безопасно взаимодействует со средой выполнения R. Вы можете обучать модели R, создавать графики R, выполнять оценку и легко перемещать данные между средой R и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Специалисты по обработке и анализу данных при проверке и разработке решений могут взаимодействовать с сервером с удаленного исследовательского компьютера и выполнять код R на сервере, а затем развертывать готовые решения в SQL Server путем внедрения вызовов R в хранимые процедуры.  
  
     Предлагаемый для скачивания файл содержит распространяемый пакет языка R с открытым исходным кодом, а также ScaleR — набор высокопроизводительных и масштабируемых пакетов R. Кроме того, в нем есть поставщики для удобного и быстрого подключения любых технологий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     Дополнительные сведения см. в разделе [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md). Примеры сценариев см. в разделе [Учебники по службам SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md).  
  
-   **Microsoft R Server**  
  
     Эта автономная серверная система поддерживает распределенные и масштабируемые решения R на нескольких платформах с использованием нескольких корпоративных источников данных, включая Hadoop, Teradata и Linux.  
  
     Дополнительные сведения см. в статье [Microsoft R Server (MSDN)](https://msdn.microsoft.com/microsoft-r/index).  
  
## <a name="related-technologies"></a>Связанные технологии  
 Корпорация Майкрософт широко поддерживает экосистему языка R с открытым кодом, в том числе предоставляет средства, поставщики, улучшенные пакеты R и интегрированные среды разработки.  
  
-   **cредства R для Visual Studio**.  
  
     Visual Studio предоставляет полнофункциональную среду разработки для языка R. Подключаемый модуль включает редактор, интерактивное окно, средство построения, отладчик и многое другое. Вы можете обращаться к языкам .NET из R или вызывать R из .NET через библиотеки c открытым исходным кодом, например R.NET или rClr.  
  
     Дополнительные сведения см. в справочнике [Средства R для Visual Studio](https://www.visualstudio.com/vs/rtvs/).  
  
-   **Использование R в машинном обучении Azure**  
  
     Создайте собственную рабочую область в студии машинного обучения Microsoft Azure, и вы сможете использовать более 400 предварительно загруженных пакетов R. Соберите и обучите модели для развертывания веб-службы или создайте свои сценарии для преобразования данных. Вы можете создать собственные пакеты R, передать их в Azure и выполнять как пользовательские модули, а также публиковать решения в [Marketplace машинного обучения](http://datamarket.azure.com/browse/data?category=machine-learning).  
  
     Дополнительные сведения см. в статьях [Расширение возможностей эксперимента с помощью R](https://docs.microsoft.com/azure/machine-learning/machine-learning-extend-your-experiment-with-r) и [Создание пользовательских R-модулей в Машинном обучении Azure](https://docs.microsoft.com/azure/machine-learning/machine-learning-custom-r-modules).  
  
-   **Виртуальные машины обработки и анализа данных**  
  
     Вы можете развернуть в Microsoft Azure предварительно установленную и настроенную версию [!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)]. Это позволит быстро приступить к исследованию данных и моделированию в облаке, не тратя силы на полную настройку системы на локальном компьютере.  
  
     В Azure Marketplace есть несколько виртуальных машин, поддерживающих обработку и анализ данных:
     + **Виртуальная машина обработки и анализа данных Майкрософт** включает в себя Microsoft R Server, а также Python (дистрибутив Anaconda), сервер записных книжек Jupyter, выпуск Visual Studio Community, Power BI Desktop, пакет Azure SDK и экспресс-выпуск SQL Server. 
     + **Microsoft R Server 2016 для Linux** содержит последнюю версию R Server (9.0.1). Для CentOS версии 7.2 и Ubuntu версии 16.04 доступны отдельные виртуальные машины. 
     + Виртуальная машина **SQL Server 2016 Enterprise только с R Server** включает в себя автономный установщик R Server 9.0.1, который поддерживает новую модель лицензирования на основе современного жизненного цикла программного обеспечения.
 

## <a name="see-also"></a>См. также  
[Приступая к работе со службами SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md) 

[Приступая к работе с Microsoft R Server](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  

 [Установка ядра СУБД SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md)  
  
  