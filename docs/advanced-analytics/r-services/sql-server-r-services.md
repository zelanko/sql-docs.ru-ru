---
title: "Службы R SQL Server | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba1dea65-40ea-484a-b767-53680c954934
caps.latest.revision: 38
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 36
---
# Службы R SQL Server
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] предоставляет платформу для разработки интеллектуальных приложений (и их развертывания), предназначенных для получения новой ценной информации. Вы можете использовать функциональный и эффективный язык R и множество пакетов от сообщества, чтобы создавать модели и делать прогнозы с использованием данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Поскольку [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] интегрирует язык R с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], аналитику можно приблизить к самим данным, избежав затрат и рисков, связанных с их перемещением.  
  
 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] поддерживает язык R с открытым исходным кодом с исчерпывающим набором инструментов и технологий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], обеспечивающих превосходную производительность, защищенность, надежность и управляемость. Вы можете развертывать решения R с помощью удобных и привычных средств, а ваши рабочие приложения могут вызывать среду выполнения R и получать прогнозы и визуальные элементы с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]. Вы также получаете библиотеки [ScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler), которые повышают масштабируемость и улучшают производительность решений на R.  
  
Через программу установки SQL Server можно установить как серверные, так и клиентские компоненты.  
  
+   **Службы R (для баз данных):** установите этот компонент во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы обеспечить безопасное выполнение скриптов R на компьютере с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     При выборе этого компонента в ядре СУБД устанавливаются расширения, поддерживающие выполнение R-скриптов, а также создается новая служба, [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], управляющая взаимодействием между средой выполнения R и экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
+   **Сервер Microsoft R Server (отдельный):** в этом компоненте R с открытым исходным кодом сочетается с проприетарными пакетами, которые обеспечивают поддержку параллельной обработки данных, а также улучшают производительность и другими способами. Как службы R (работающие в базе данных), так и отдельный сервер Microsoft R Server включают в себя базовые среду выполнения R и пакеты, а также библиотеки **ScaleR** для расширения возможностей связи и улучшения производительности. 
  
+    [Клиент Microsoft R](https://msdn.microsoft.com/microsoft-r/index#mrc) доступен как отдельный и бесплатный установщик.  Клиент Microsoft R можно использовать для разработки решений, которые могут быть развернуты в службы R на SQL Server или на сервер Microsoft R Server в Windows, Teradata или Hadoop. 
     

  > [!NOTE] Если код R необходимо выполнять в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], установите [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] (процесс установки описан [здесь](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)).
  >  
  > \(Отдельный\) сервер Microsoft R Server представляет собой компонент, предназначенный для использования библиотек ScaleR на компьютере с Windows, на котором нет SQL Server. 
>   
>  При наличии выпуска Enterprise Edition мы рекомендуем установить \(отдельный\) сервер Microsoft R Server на ноутбуке или другом компьютере, используемом для разработки ПО на языке R, с целью создания решений R, которые затем можно развернуть в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] со службами R (\(в базе данных\)).
  
## <a name="additional-resources"></a>Дополнительные ресурсы  
  
 [Приступая к работе со службами SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)   
 Описывает распространенные схемы использования R совместно с SQL Server.  
  
[Установка служб SQL Server R Services (в базе данных)](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
Установка R и связанных компонентов для баз данных в процессе установки SQL Server.  
  
[Руководства по службам SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
Информация о том, как создавать источники данных SQL Server в коде R и использовать контексты удаленных вычислений. Другие руководства предназначены для разработчиков SQL и демонстрируют, как обучить и развернуть модель R в SQL Server.  
  
## <a name="see-also"></a>См. также  
  
 [Приступая к работе с изолированным сервером Microsoft R Server](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
 
 [Создание изолированного сервера R Server](../../advanced-analytics/r-services/create-a-standalone-r-server.md) 
  