---
title: "Приступая к работе со службами SQL Server R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "12/07/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: 5b28a663-effe-41f6-9bda-eda95f0c6943
caps.latest.revision: 34
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 32
---
# Приступая к работе со службами SQL Server R Services
 Типичный рабочий процесс для построения аналитического решения начинается с изучения данных и прогнозного моделирования, тогда как специалисты по анализу данных разрабатывают и используют скрипты и модели R, показавшие свою эффективность для решения поставленной задачи. Готовые скрипты и модели можно развернуть в производственной среде и интегрировать в существующие или новые приложения.   
  
Для выполнения таких задач по анализу данных предназначены службы R SQL Server. Вы можете продолжать работать со знакомыми средствами R или SQL и при этом обрабатывать миллиарды записей без дополнительного оборудования, повышая производительность и исключая ненужное перемещение данных. Теперь вы можете вводить код R в рабочую среду, не переписывая его на другом языке. Кроме того, R упрощает выполнение статистических вычислений, проведение которых с помощью SQL может вызывать трудности. В то же время эффективные возможности SQL Server, такие как ядро СУБД в памяти и индексы columnstore, позволяют достичь максимальной производительности.  
  
В следующих разделах приводится обзор ряда стандартных аналитических рабочих процессов и описывается их реализация с помощью служб R SQL Server.  

> [!TIP] В этом учебнике содержатся сведения по быстрому началу работы. Вы узнаете об использовании машинного обучения для прогнозирования будущих заказов в компании проката лыж и организации работы с учетом спроса.
> 
> [Создание интеллектуальных приложений с помощью SQL Server и R](https://www.microsoft.com/sql-server/developer-get-started/r)


  
-   **Разработка**  
  
     Специалисты по анализу данных обычно используют R для просмотра данных и построения прогнозных моделей с рабочей станции с помощью подходящего интерфейса IDE R. Специалист чередует тестирование и настройку, пока не получает хорошую прогнозную модель. 
     
     Клиентские компоненты [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] предоставляют специалисту все необходимые средства для экспериментов и разработки. Эти средства включают среду выполнения R, библиотеку математического ядра Intel для повышения производительности стандартных операций R и набор улучшенных пакетов R, поддерживающих выполнение кода R в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Специалисты могут подключаться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и передавать данные на клиент для локального анализа обычным образом. Но лучше использовать API **ScaleR** для принудительной отправки вычислений на компьютер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], избежав ресурсоемкого небезопасного перемещения данных.  
  
     Для разработки решений R специалисты могут использовать любую среду IDE для Windows, поддерживающую R, включая [средства R для Visual Studio](https://www.visualstudio.com/features/rtvs-vs.aspx) или RStudio.  
 
    ![rsql_keyscenario2](../../advanced-analytics/r-services/media/rsql-keyscenario2.PNG) 
 
     Дополнительные сведения см. в разделе [Data Exploration and Predictive Modeling with R](../../advanced-analytics/r-services/data-exploration-and-predictive-modeling-with-r.md).  

  
-   **Оптимизация**  
  
     При анализе больших наборов данных с помощью R специалисты часто сталкиваются с проблемами производительности и масштабирования, так как общая реализация среды выполнения является однопотоковой и может обрабатывать только те наборы данных, которые умещаются в памяти локального компьютера. Чтобы повысить производительность и работать с данными большего объема, специалист может использовать API **ScaleR**, входящие в состав [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Пакет **RevoScaleR** содержит реализации некоторых наиболее популярных функций R, переработанные для обеспечения параллелизма и масштабирования. Кроме того, пакет содержит функции, дополнительно повышающие производительность и масштабируемость за счет принудительной отправки вычислений на компьютер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который обычно обладает гораздо большим объемом памяти и вычислительных ресурсов.  
  
     Дополнительные сведения см. в разделе [Data Exploration and Predictive Modeling with R](../../advanced-analytics/r-services/data-exploration-and-predictive-modeling-with-r.md).  
  
-   **Развертывание**  
  
     Когда модель или скрипт R готовы к использованию в рабочей среде, разработчик баз данных может внедрить модель или код в хранимые процедуры и вызвать сохраненный код из приложения. Хранение и выполнение кода R в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет множество преимуществ: можно использовать удобный интерфейс [!INCLUDE[tsql](../../includes/tsql-md.md)], а все вычисления выполняются в базе данных без ненужного перемещения данных. [!INCLUDE[tsql](../../includes/tsql-md.md)] можно использовать, чтобы формировать оценки на основе прогнозной модели в рабочей среде или возвращать созданные R графики и представлять их в приложении, таком как [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
     Чтобы дополнительно оптимизировать код R, внедренный в системные хранимые процедуры, рекомендуется использовать API пакетов [ScaleR](https://msdn.microsoft.com/microsoft-r/rserver/rserver-scaler-getting-started), позволяющие работать с более крупными наборами данных. Эти пакеты поддерживают выполнение в базе данных и позволяют организовать многопоточные вычисления на базе нескольких ядер и процессов.  
  
     Когда требуется развернуть код R в рабочей среде, [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] позволяет использовать преимущества как R, так и SQL. Можно использовать R для статистических вычислений, которые трудно реализовать с помощью SQL, и при этом пользоваться всеми возможностями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для достижения максимальной производительности, например ядром СУБД в памяти и индексами columnstore.  
  
    ![rsql_keyscenario1](../../advanced-analytics/r-services/media/rsql-keyscenario1.PNG)  
  
     Дополнительные сведения см. в разделе [Ввод в эксплуатацию кода R](../../advanced-analytics/r-services/operationalizing-your-r-code.md).  
 
 > [!TIP] Дополнительные сведения об интеграции SQL Server с анализом данных см. в доступной для бесплатного скачивания на сайте Microsoft Virtual Academy книге: [Data Science with Microsoft SQL Server 2016](https://mva.microsoft.com/ebooks/) (Исследование данных в Microsoft SQL Server 2016).

-   **Управление и мониторинг**  
  
     [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] использует новую архитектуру расширяемости, которая обеспечивает безопасность ядра СУБД и изолирует сеансы R. Кроме того, вы можете контролировать пользователей, которым разрешено выполнять скрипты R, и указать, к каким базам данных может обращаться код R. Можно управлять объемом ресурсов, выделяемых для среды выполнения R, чтобы предотвратить негативное влияние масштабных вычислений на общую производительность сервера.  
  
     При выполнении заданий R в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно управлять данными, используемыми специалистами по анализу, и проводить их аудит, а также составлять расписания заданий и проектировать рабочие процессы со скриптами R, как и в случае с другими хранимыми процедурами.  
  
     Дополнительные сведения см. в разделе [Managing and Monitoring R Solutions](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md).  
  
  
-   **Интеграция**  
  
     Вам больше не нужно тратить ИТ-бюджет на обеспечение совместимости корпоративных средств с внешней средой выполнения R. Работайте в привычной среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а также разрабатывайте интегрированные рабочие процессы и решения для ведения отчетов с помощью [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
     Дополнительные сведения см. в разделе [Создание в SQL Server потоков, использующих R](../../advanced-analytics/r-services/creating-workflows-that-use-r-in-sql-server.md).  
  
  
## <a name="how-do-i-get-it"></a>Как получить доступ к службам?  
   
  
+   **Установка [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или более поздних версий и включение служб R Services (аналитики в базе данных)**)  
  
    [Настройка служб SQL Server R Services (в базе данных)](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
  
  
-   **Настройка клиентской рабочей станции**  
  
     [Настройка клиента обработки и анализа данных](../../advanced-analytics/r-services/set-up-a-data-science-client.md)  
   
> [!TIP]   
>   
> Требуется создать сервер для заданий R, но SQL Server не нужен? Попробуйте [Microsoft R Server](https://msdn.microsoft.com/library/mt674874.aspx).  
  
## <a name="how-to-run-r-code-using-sql-server-r-services"></a>Запуск кода R с помощью служб SQL Server R Services  
 После завершения установки можно запустить код R на сервере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] путем внедрения кода R в хранимые процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] или разработки произвольных скриптов R, работающих с данными [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Сведения о вызове кода R из инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] и получении результатов в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
     [Использование кода на языке R в Transact-SQL](../../advanced-analytics/r-services/using-r-code-in-transact-sql-sql-server-r-services.md)  
  
-   Понимание полной схемы по созданию решения расширенной аналитики и его развертыванию с помощью служб R SQL Server  
  
     [Пошаговое руководство по обработке и анализу данных](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md)  
  
-   Сведения об использовании пакета RevoScaleR для масштабируемого и высокопроизводительного анализа и о передаче вычислений R на компьютер SQL Server  
  
     [Глубокое погружение в обработку и анализ данных: использование пакетов RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
-   Внедрение рабочего скрипта R в хранимые процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] для вызова моделей для прогнозирования, повторного обучения моделей и получения прогнозов из приложений  
  
     [Дополнительные аналитические функции в базе данных для разработчиков SQL](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
  
-   Использование [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и связанных средств бизнес-аналитики в стеке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для автоматизации процессов машинного обучения. Подготовку данных и отчетов можно автоматизировать с помощью [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]; отображение графиков R вместе с другими отчетами с помощью служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или Power View.  
  
+ Дополнительные примеры, включая шаблоны решений и примеры кода R  
   [SQL Server R Services Tutorials](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md).  
  
## <a name="see-also"></a>См. также  
 [Службы R SQL Server](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [Приступая к работе с изолированным сервером Microsoft R Server](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
  
  