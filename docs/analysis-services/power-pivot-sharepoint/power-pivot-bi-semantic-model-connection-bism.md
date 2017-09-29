---
title: "Питание соединение семантической модели бизнес-Аналитики Pivot (bism) | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08828eec-4f8c-4f34-a145-e442f7b7031d
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 41cfa6b2ca110803ca4b63abf683edf7d508c027
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="power-pivot-bi-semantic-model-connection-bism"></a>Соединение семантической модели бизнес-аналитики Power Pivot (BISM-файлы)
  Соединение семантической модели бизнес-аналитики (BISM-файл) — это переносимое соединение, связывающее отчеты Excel или Power View с базой данных табличной модели Analysis Services или экземпляром служб Analysis Services в многомерном режиме. Определение и использование BISM-файлов в определенной степени аналогично файлам подключения к данным Оffice (ODC).  
  
 Создание семантической модели бизнес-аналитики и доступ к ней через SharePoint. Создание соединения семантической модели бизнес-аналитики позволяет использовать команды быстрого запуска соединения семантической модели с библиотекой. Команды быстрого запуска открывают новую книгу Excel или параметры файла соединения. При установке служб Reporting Services также появится команда для создания отчета [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] .  
  
 ![Команда быстрого запуска экрана BISM](../../analysis-services/power-pivot-sharepoint/media/ssas-bism-quicklaunch.gif "команда быстрого запуска экрана BISM")  
  
##  <a name="bkmk_prereq"></a> Поддерживаемые базы данных  
 Соединение семантической модели бизнес-аналитики указывает на данные табличной модели. Существует три источника этих данных.  
  
-   Табличный шаблон базы данных, запущенный на отдельном экземпляре служб Analysis Services в режиме табличного сервера. Развертывание отдельного экземпляра служб Analysis Services выполняется вне пределов фермы. Для доступа к источникам данных, находящимся за пределами фермы, требуются дополнительные разрешения, о которых можно прочитать в следующем разделе: [Создание подключения между семантической моделью бизнес-аналитики и книгой PowerPivot](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-tabular-model-database.md).  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , сохраненные в SharePoint. Базы данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , внедренные в книги Excel, эквивалентны табличным шаблонам баз данных, запущенным на отдельном сервере Analysis Services в табличном режиме. Если [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для Excel и [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint уже используются, то можно определить соединение семантической модели бизнес-аналитики, указывающее на книги [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] из библиотеки SharePoint, и создавать отчеты [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] с использованием существующих данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  Можно использовать книги, созданные в версиях SQL Server 2008 R2 или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для Excel.  
  
-   Многомерная модель данных в экземпляре служб Analysis Services.  
  
 Сравнение источников данных см. в материалах сообщества [Understanding the SQL Server 2012 BI Semantic Model (BISM)](http://www.mssqltips.com/sqlservertip/2818/understanding-the-sql-server-2012-bi-semantic-model-bism/)(Общие сведения о семантической модели бизнес-аналитики SQL Server 2012 (BISM-файл)).  
  
## <a name="understanding-the-connection-sequence-for-bi-semantic-connections"></a>Основные сведения о последовательности соединения для семантической модели бизнес-аналитики  
 В этом разделе описывается работа соединений между различными клиентскими приложениями, в том числе Excel или клиентом отчетов Power View в SharePoint, и базой данных табличной модели, находящейся в пределах или вне пределов фермы SharePoint.  
  
 Все соединения с базой данных табличной модели устанавливаются с учетными данными пользователя, запрашивающего данные. Однако механизм соединения различается в зависимости от того, устанавливается ли оно в пределах фермы, состоит ли из одного или двух этапов и включен ли протокол Kerberos. Дополнительные сведения об аутентификации соединений между SharePoint и серверными источниками данных см. в разделе [Double-hop authentication: Why NTLM fails and Kerberos works](http://go.microsoft.com/fwlink/?LinkId=237137)(Двухэтапная аутентификация: почему Kerberos работает, а NTLM — нет).  
  
 **Соединение с табличными данными из Excel по сети**  
  
 Когда пользователь Excel указывает соединение семантической модели бизнес-аналитики в качестве источника данных, сведения о соединении в BISM-файле загружаются в клиентское приложение, которое затем создает собственный прямой запрос к базе данных табличной модели в службах Analysis Services. Для доступа к BISM-соединению пользователь Excel должен быть пользователем SharePoint с разрешениями на чтение BISM-файла соединения. После загрузки сведений о соединении все последующие соединения устанавливаются без участия SharePoint, непосредственно от Excel к серверной базе данных табличной модели.  
  
 На следующем рисунке показана эта последовательность соединения. Она начинается с запроса BISM-соединения, затем сведения о соединении загружаются на клиент, и, наконец, устанавливается одноэтапное соединение с базой данных. Соединение устанавливается с использованием учетных данных Windows пользователя Excel, обладающего разрешениями на чтение базы данных служб Analysis Services. Поскольку соединение устанавливается в один этап, то, даже когда включен протокол Kerberos, он необязателен в таком сценарии.  
  
 ![Соединения из Excel с базой данных табличной модели](../../analysis-services/power-pivot-sharepoint/media/ssas-powerpivotbismconnection-1.gif "соединения из Excel с базой данных табличной модели")  
  
 **Соединение с табличными данными из Power View по сети**  
  
 Когда пользователь SharePoint выбирает соединение семантической модели бизнес-аналитики в библиотеке документов, то немедленно запускается приложение Power View (если оно установлено) и открывает соединение с базой данных табличной модели.  
  
 В соединениях между Power View и базой данных табличной модели применяется двухэтапная последовательность проверки подлинности, когда удостоверение пользователя передается от клиента в SharePoint, а затем от SharePoint в серверную базу данных табличной модели служб Analysis Services, которая работает вне фермы. Клиентская библиотека ADOMD.NET, которая обрабатывает запрос на соединение, сначала всегда применяет протокол Kerberos. Если настроен протокол Kerberos, то выполняется олицетворение пользователя в соединении с базой данных табличной модели и подключение устанавливается успешно.  
  
 Если протокол Kerberos не настроен и первый запрос соединения не выполняется, то службы Reporting Services создают второй запрос. В этом случае клиентская библиотека подключается к службам Analysis Services с использованием удостоверения службы Reporting Services и проверки подлинности NTLM. Удостоверение пользователя Power View передается в строке подключения в параметре **effectiveusername** .  
  
 Только член роли системного администратора в экземпляре служб Analysis Services имеет разрешение на подключение с параметром **effectiveusername** и олицетворение другого пользователя в экземпляре сервера. Поэтому учетная запись выполнения для общей службы Reporting Services должна иметь права администратора в экземпляре служб Analysis Services.  Инструкции по предоставлению административных разрешений учетной записи службы приведены в подразделе [Создание подключения между семантической моделью бизнес-аналитики и книгой PowerPivot](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)этого раздела.  
  
 На следующем рисунке показана последовательность, в которой для каждого соединения используется одно и то же удостоверение пользователя Windows. Последнее соединение со службами Analysis Services устанавливается удостоверением приложения службы Reporting Services без удостоверения пользователя Windows. Для этого используется параметр **effectiveusername**.  
  
 ![Олицетворенное соединение с табличной БД](../../analysis-services/power-pivot-sharepoint/media/ssas-powerpivotbismconnection-2.gif "олицетворенное соединение с табличной базы данных")  
  
 **Соединение с данными [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в SharePoint из Power View**  
  
 Когда пользователь SharePoint выбирает соединение семантической модели бизнес-аналитики, которое указывает на книгу [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] на той же ферме, то соединение выполняется в контексте среды SharePoint. Приложение службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] обрабатывает запрос на соединение и направляет его в экземпляр служб Analysis Services на том же компьютере. Экземпляр служб Analysis Services извлекает данные [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] из книги и загружает их. Все последующие соединения управляются приложением службы [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] на ферме.  
  
 В этом случае все соединения устанавливаются в пределах фермы и нет необходимости применять протокол Kerberos или ограниченное делегирование.  
  
##  <a name="bkmk_rel"></a> Связанные задачи  
 [Добавление типа содержимого соединения для семантической модели бизнес-аналитики в библиотеку (PowerPivot для SharePoint)](../../analysis-services/power-pivot-sharepoint/add-bi-semantic-model-connection-content-type-to-library.md)  
  
 [Создание подключения между семантической моделью бизнес-аналитики и книгой PowerPivot](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md)  
  
 [Создание подключения между семантической моделью бизнес-аналитики и книгой PowerPivot](../../analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)  
  
 [Использование соединения семантической модели бизнес-аналитики в службах Excel или Reporting Services](../../analysis-services/power-pivot-sharepoint/use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md)  
  
## <a name="see-also"></a>См. также  
 [Определение режима работы сервера экземпляра служб Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Подключение к службам Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  
