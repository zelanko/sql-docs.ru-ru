---
title: "Новые возможности служб SQL Server R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6aff043a-8b37-4f3f-9827-10a671e1ad1c
caps.latest.revision: 36
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 35
---
# Новые возможности служб SQL Server R Services
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] — это компонент в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и SQL Server vNext, поддерживающий обработку и анализ данных корпоративного уровня.  R — это наиболее распространенный язык программирования для расширенной аналитики, который предлагает очень широкий спектр пакетов и активное и быстро развивающееся сообщество разработчиков. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] помогает использовать очень популярный язык R с открытым исходным кодом в бизнесе. 
  
 > [!TIP] Уже используете службы SQL Server 2016 R Services?
 > Теперь вы можете установить последнюю версию Microsoft R Server на экземпляры SQL Server 2016, чтобы чаще обновлять компоненты R. Дополнительные сведения см. в статье [What's New in R Server 9.0.1](https://msdn.microsoft.com/microsoft-r/rserver-whats-new) (Новые возможности R Server 9.0.1).  

## <a name="whats-new-in-sql-server-vnext"></a>Новые возможности в SQL Server vNext
  
+ Знакомство с пакетом **MicrosoftML**

   MicrosoftML — это новый пакет машинного обучения для языка R от групп разработчиков Microsoft R Server и решений для обработки и анализа данных Майкрософт. MicrosoftML повышает скорость, производительность и масштабируемость, обеспечивая обработку больших объемов текстовых и многомерных категориальных данных в моделях R с помощью всего лишь нескольких строк кода. Кроме того, клиенты Microsoft R Server получают доступ к пяти быстрым, очень точным модулям обучения, входящим в состав службы Машинного обучения Azure. 
   
   Дополнительные сведения см. в разделе [Использование пакета MicrosoftML со службами R Services SQL Server](../../advanced-analytics/r-services/using-the-microsoftml-package-with-sql-server-r-services.md).
   
+ Упрощенное управление пакетами для пользователей

  Вам больше не нужно обращаться к администратору базы данных для установки необходимых пакетов R в SQL Server. Новые функции установки и удаления пакетов в **RevoScaleR** позволяют легко устанавливать и обновлять пакеты в службах R с клиентского компьютера. 
  
  Для администраторов баз данных в [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] включены новые роли для управления разрешениями, связанными с пакетами, как на уровне экземпляра, так и на уровне базы данных. 
  
  Дополнительные сведения см. в разделе [Управление пакетами R для служб R Services SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md). 
     
+ Новые функции в **RevoScaleR** для чтения и записи объектов модели R

  RevoScaleR включает новые функции сериализации и более компактный формат хранения модели, позволяющий ускорить загрузку и чтение модели. 
  
  Дополнительные сведения см. в разделе [Сохранение и загрузка объектов R из SQL Server с помощью ODBC](../../advanced-analytics/r-services/save-and-load-r-objects-from-sql-server-using-odbc.md). 

+ Пакет **sqlrutils** для упрощения интеграции с SQL

  Этот пакет R помогает создавать вызовы хранимых процедур SQL в коде на языке R. Созданные хранимые процедуры SQL затем можно использовать в службах R SQL Server. Предоставляются примеры, помогающие консолидировать код R в функцию, которую можно параметризовать в хранимой процедуре SQL.
  
  Дополнительные сведения см. в разделе [Создание хранимой процедуры R для кода R с помощью пакета sqlrutils](../../advanced-analytics/r-services/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md). 
  

+ Пакет **olapR** для упрощения подключения к службам SQL Server Analysis Services

   Этот пакет предоставляет новое измерение подключения для среды R и служб SQL Server Analysis Services, которое упрощает использование данных OLAP для анализа в R. Вы можете выполнять существующие запросы MDX и получать кадры данных R или создавать простые инструкции MDX, определяя оси и срезы кубов в коде R. 
   
   Дополнительные сведения см. в разделе [Использование данных из кубов OLAP в R](../../advanced-analytics/r-services/using-data-from-olap-cubes-in-r.md).
   

  
## <a name="features-in-sql-server-2016-r-services-and-sql-server-vnext"></a>Функции служб R SQL Server 2016 и SQL Server vNext  
  
- Пакет **RevoScaleR** для быстрого параллелизуемого машинного обучения с использованием языка R.

-   Поддерживает как имена входа SQL, так и встроенную проверку подлинности Windows.  
    
-   Значительные улучшения в плане производительности, включая оптимизацию вспомогательных процессов SQL, которые обеспечивают подключение R и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], поддержку подкачки для обработки больших объемов данных и потоковую передачу для быстрой обработки миллионов строк. 
  
-   Управляйте памятью, используемой процессами R, с помощью пулов ресурсов SQL Server. Дополнительные сведения см. в разделе [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md).  
  

### <a name="tools-and-setup"></a>Средства и программа установки

-   Простая установка всех компонентов. Мастер установки SQL Server может установить **службы SQL Server R (в базе данных)** или сервер **Microsoft R Server (изолированный)**.   При запуске мастера установки выберите службы R, если вы настраиваете экземпляр SQL Server, или сервер R Server (изолированный), если вы настраиваете рабочую станцию обработки и анализа данных.   Дополнительные сведения о параметрах установки см. в разделе [Установка служб SQL Server R Services &#40;в базе данных&#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md) или [Создание изолированного сервера R Server](../../advanced-analytics/r-services/create-a-standalone-r-server.md).  

-   Если вам не нужно работать с данными в SQL Server, рекомендуем использовать сервер [!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)], который работает на различных платформах и обеспечивает масштабируемость и производительность корпоративного уровня для популярно языка R с открытым исходным кодом. [!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)]. Подробные сведения см. в статье [R Server &#40;изолированный&#41;](../../advanced-analytics/r-services/r-server-standalone.md) или [Знакомство с R Server](https://msdn.microsoft.com/microsoft-r/rserver) на сайте MSDN.

- Чтобы обновить экземпляр SQL Server 2016 для использования Microsoft R Server 9.0.1, используйте [служебную программу SqlBindR.exe](https://msdn.microsoft.com/library/mt791781.aspx).  

- [Клиент Microsoft R](https://msdn.microsoft.com/microsoft-r/r-client-install) — это бесплатная среда R, которая включает все средства и библиотеки, необходимые для создания решений R, работающих в службах R или на сервере R Server.  

-   Средства R для Visual Studio — это бесплатный подключаемый модуль для Visual Studio с широкой поддержкой языка R, включая стандартные интерактивные окна и окна переменных R, Intellisense для функций R, возможность отладки, файл R Markdown, а также возможность экспорта в Word и HTML.  Дополнительные сведения см. в справочнике [Средства R для Visual Studio](https://www.visualstudio.com/vs/rtvs/).  

## <a name="learn-more"></a>Дополнительные сведения
  
-  Доступны ресурсы как для специалистов по обработке и анализу данных, желающих ознакомиться с возможностями интеграции с SQL Server, так и для разработчиков SQL, которые хотят создавать решения R, используя язык T-SQL и знакомую среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 
   + [Руководства по службам SQL Server R Services](https://msdn.microsoft.com/library/mt591993.aspx)
   + [Бесплатная электронная: обработка и анализ данных с помощью SQL Server 2016](https://mva.microsoft.com/ebooks/)
 
+ Если вам нужны готовые решения, воспользуйтесь [шаблонами машинного обучения](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/) от группы разработчиков решений для обработки и анализа данных Майкрософт. Они позволяют на практике ознакомиться с выполнением стандартных аналитических задач, включая превентивное обслуживание и предотвращение оттока пользователей.
 

  
## <a name="see-also"></a>См. также:  
[Новые возможности в SQL Server vNext](../../sql-server/what-s-new-in-sql-server-vnext.md)
  