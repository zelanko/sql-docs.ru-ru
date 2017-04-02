---
title: "Учебники по службам SQL Server R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 5ccc75f6-6703-47d9-b879-9a740569b45e
caps.latest.revision: 31
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 27
---
# Учебники по службам SQL Server R Services
В этих руководствах содержится информация о [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] и сценариях обработки и анализа данных, поддерживаемых этими службами, включая следующую.

+ Разработка моделей в среде R и их развертывание в SQL Server.
+ Ввод кода на языке R в эксплуатацию путем развертывания решения, разработанного специалистом по обработке и анализу данных, на сервере или в другой рабочей среде.
+ Перемещение данных между средами R и SQL Server.
+ Использование удаленных и локальных контекстов вычисления.
  

## <a name="a-namebkmkend-to-endadeveloping-an-end-to-end-advanced-analytics-solution"></a><a name="bkmk_end-to-end"></a>Разработка полнофункционального решения для расширенной аналитики  

[Пошаговое руководство по обработке и анализу данных](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md) 

Полное погружение в процесс обработки и анализа данных — от получения данных до их оценки. Использование данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и ввод моделей в эксплуатацию путем их сохранения в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
Вы импортируете набор данных по работе такси в Нью-Йорке в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью PowerShell и изучите их с использованием R. 

Затем вы создадите прогнозную модель на R и развернете ее в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для оценки в пакетном режиме и в режиме единичного прогноза. 

  
Это руководство предназначено для пользователей, имеющих некоторый опыт работы с R, а также со средствами разработки, такими как PowerShell и среда SQL Server Management Studio. Вы должны иметь доступ к среде разработки R и знать команды R. 
  
## <a name="a-namebkmkdatascienceadata-science-deep-dive"></a><a name="bkmk_dataScience"></a>Глубокое погружение в обработку и анализ данных  

[Начало работы с RevoScaleR и SQL Server](http://go.microsoft.com/fwlink/?LinkID=691640&clcid=0x809)  

Это пошаговое руководство — хорошее начало для специалистов по обработке и анализу данных и разработчиков, которые уже знакомы с языком R и хотят получить информацию о дополнительных пакетах R и функциях Microsoft R, предоставляемых Revolution Analytics. 

Вы узнаете об использовании функций в пакетах ScaleR для перемещения данных между R и SQL, а также о переключении контекстов вычислений в соответствии с конкретной задачей. Кроме того, вы создадите несколько моделей и диаграмм и научитесь перемещать их между средой разработки и SQL Server.  
  
Это руководство предназначено для пользователей, которые уже используют R и хотят узнать больше о том, как RevoScaleR и SQL Server могут повысить эффективность работы с R.

## <a name="in-database-advanced-analytics-for-the-sql-developer"></a>Дополнительные аналитические функции в базе данных для разработчиков SQL  
  
[Дополнительные аналитические функции в базе данных для разработчиков SQL (руководство)](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)

Вы создадите и развернете готовое и сложное решение для анализа данных при помощи [!INCLUDE[tsql](../../includes/tsql-md.md)]. В этом примере рассматривается интеграция функций R с открытым исходным кодом с ядром СУБД [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Вы узнаете, как включить код на языке R в хранимую процедуру, сохранить модель R в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и выполнять параметризованные вызовы модели R для составления прогнозов. 
  
Это руководство предназначено для разработчиков SQL, разработчиков приложений или администраторов баз данных SQL, которые будут заниматься поддержкой решений R и хотят научиться развертывать модели R в SQL Server.  Среда R не требуется. Весь необходимый код на языке R предоставляется, и готовое решение можно создать, используя лишь среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и знакомые средства разработки и бизнес-аналитики SQL.   

## <a name="use-r-services-in-an-application"></a>Использование служб R в приложении

[Создание интеллектуальных приложений с помощью SQL Server и R](https://www.microsoft.com/sql-server/developer-get-started/r)

В этом учебнике описывается использование машинного обучения для прогнозирования будущих заказов в компании проката лыж, что позволяет создать бизнес-план и организовать работу с учетом будущего спроса.


## <a name="using-r-code-in-t-sql"></a>Использование кода на языке R в T-SQL  

[Использование кода на языке R в Transact-SQL (службы SQL Server R Services)](../../advanced-analytics/r-services/using-r-code-in-transact-sql-sql-server-r-services.md)  

Это ряд коротких отдельных примеров, в которых демонстрируются основные особенности синтаксиса, необходимого для использования языка R в [!INCLUDE[tsql](../../includes/tsql-md.md)]. 

Вы узнаете, как вызывать среду выполнения R в SQL, переносить функции R в код SQL и выполнять хранимую процедуру, которая сохраняет выходные данные R в таблице SQL, а также получите сведения об основных различиях в типах данных для R и SQL.
  
Это руководство предназначено для тех, кто не знаком со службами R Services и хочет изучить основы вызова кода R при помощи T-SQL. Опыт работы с R не требуется. Однако необходимо знать, как использовать среду SQL Server Management Studio или любой другой инструмент, который может подключаться к базе данных и выполнять простые запросы T-SQL.

  
## <a name="a-namebkmkprerequisitesaprerequisites"></a><a name="bkmk_Prerequisites"></a>Предварительные требования
  
Перед тем как приступать к работе, скачайте и установите **службы R Services (в базе данных)**, как описано в статье [Установка служб SQL Server R Services (в базе данных)](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).

После запуска программы установки SQL Server нужно выполнить указанные далее дополнительные действия.
+ Включите службы R Services с помощью процедуры *sp_configure*.
+ Перезагрузите сервер
+ Убедитесь, что служба, которая вызывает среду выполнения R, имеет необходимые разрешения.
+ Убедитесь, что имя для входа SQL или учетная запись пользователя Windows, которая будет использоваться для работы с кодом R, имеет необходимые разрешения для подключения к серверу и его базам данных.

При возникновении сложностей см. описание некоторых распространенных проблем в статье [Обновление и установка служб SQL Server R Services](../../advanced-analytics/r-services/upgrade-and-installation-faq-sql-server-r-services.md).

Если предпочтительная среда разработки R отсутствует, можно установить один из приведенных ниже инструментов, который поможет приступить к работе:

+ [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started);
+ [cредства R для Visual Studio](https://www.visualstudio.com/vs/rtvs/).

Обратите внимание, что для использования этих руководств недостаточно иметь стандартные библиотеки R. В средах разработки R и на сервере SQL Server с R должны находиться пакеты ScaleR от Майкрософт. Дополнительные сведения о функциях и продуктах в Microsoft R см. в статье [Microsoft R Products](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started#compare-prods) (Продукты Microsoft R).

## <a name="additional-resources"></a>Дополнительные ресурсы

Завершив изучение этих руководств, воспользуйтесь приведенными ниже ссылками для просмотра более сложных сценариев и примеров.
  
### <a name="end-to-end-solution-templates-for-key-machine-learning-tasks"></a>Шаблоны готовых решений для основных задач машинного обучения  

[Шаблоны машинного обучения для служб SQL Server 2016 R Services](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/).  

Рабочая группа Майкрософт по машинному обучению предоставила ряд настраиваемых шаблонов, позволяющих быстро создавать решения для выполнения следующих ключевых в сфере машинного обучения задач:  
* обнаружение мошенничества;  
* прогнозирование ухода клиентов;  
* профилактическое обслуживание.  
  
Предоставляется весь необходимый код на языках T-SQL и R, а также инструкции по обучению и развертыванию модели для оценки с использованием хранимых процедур SQL Server. 

### <a name="sample-data-and-sample-scripts"></a>Образцы данных и скриптов  
Образцы продуктов для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно скачать в Центре загрузки Майкрософт. Чтобы получить образцы только для служб [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], выберите ZIP-файл и откройте папку **Advanced Analytics**.  Некоторые инструкции предназначены для более ранних версий. Однако здесь доступна демонстрация случая обнаружения мошенничества в области страхования на основе закона Бенфорда и простое пошаговое руководство по прогнозной модели для очень маленького набора данных (набор данных Iris), которые могут быть полезны в целях демонстрации.
  
[Образцы для SQL Server 2016](https://www.microsoft.com/en-us/download/details.aspx?id=49502)  
### <a name="learn-more-about-r"></a>Дополнительные сведения о языке R  
Чтобы получить дополнительные сведения о языке R в целом, воспользуйтесь отличными ресурсами, перечисленными в следующей статье: [Ресурсы по языку R](http://revolutionanalytics.com/r-language-resources).  
  
Дополнительные сведения о пакетах R, предоставляемых в службах [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], см. на [сайте Revolution Analytics](http://go.microsoft.com/fwlink/?LinkId=691541).  
  
В этой записи блога описывается процесс использования пакетов и функций R, предоставляемых службами [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] , для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]и приводятся образцы кода: [Использование языка R в SQL Server](http://blog.revolutionanalytics.com/2015/10/previewing-using-revolution-r-enterprise-inside-sql-server.html).  
  
## <a name="see-also"></a>См. также:  
[Приступая к работе со службами SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
[Возможности и задачи служб SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-features-and-tasks.md)  
  
