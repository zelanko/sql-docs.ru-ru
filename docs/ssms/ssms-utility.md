---
title: "Программа SSMS | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], opening
- command prompt utilities [SQL Server], sqlwb
- sqlwb utility
- Management Studio command line
- opening SQL Server Management Studio
ms.assetid: aafda520-9e2a-4e1e-b936-1b165f1684e8
caps.latest.revision: "50"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e308a64f82ddb822bc5535c6cae7dc076265d212
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="ssms-utility"></a>Программа SSMS
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Служебная программа **Ssms** открывает [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Если указано, программа **Ssms** также устанавливает подключение к серверу и открывает запросы, скрипты, файлы, проекты и решения.  
  
 Можно указать файлы, содержащие запросы, проекты или решения. Файлы, содержащие запросы, автоматически подключаются к серверу в случае наличия сведений для соединения и в том случае, если сервер связан с этим типом файлов. Например, SQL-файлы в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]откроются в окне редактора SQL-запросов, а MDX-файлы откроются в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]в окне редактора запросов многомерных выражений. **Решения и проекты SQL Server** открываются в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
> [!NOTE]  
>  Программа **Ssms** не выполняет запросы. Для запуска запросов из командной строки используйте программу **sqlcmd** .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Ssms  
    [scriptfile] [projectfile] [solutionfile]  
    [-S servername] [-d databasename] [-U username] [-P password]   
    [-E] [-nosplash] [-log [filename]?] [-?]  
```  
  
## <a name="arguments"></a>Аргументы  
 *scriptfile*  
 Указывает один или более файлов скрипта для открытия. Этот параметр должен содержать полный путь к файлам.  
  
 *projectfile*  
 Задает открываемый проект скрипта. Этот параметр должен содержать полный путь к файлу проекта скрипта.  
  
 *solutionfile*  
 Задает открываемое решение. Этот параметр должен содержать полный путь к файлу решения.  
  
 [**-S** *servername*]  
 Имя сервера  
  
 [**-d** *databasename*]  
 Имя базы данных  
  
 [**-U** *username*]  
 Имя пользователя при соединении с использованием проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 [**-P** *password*]  
 Пароль при соединении с использованием проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 [**-E**]  
 Подключение с помощью проверки подлинности Windows  
  
 [**-nosplash**]  
 Отключает отображение экрана-заставки при открытии среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] . Используйте этот параметр при соединении с компьютером, где среда [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] работает с помощью служб терминалов, через соединение с ограниченной пропускной способностью. При записи этого аргумента регистр символов не учитывается, он может быть указан до или после других аргументов  
  
 [**-log***[filename]?*]  
 Записывает действия среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] в указанный файл для диагностики неисправностей  
  
 [**-?**]  
 Отображает справку командной строки.  
  
## <a name="remarks"></a>Замечания  
 Все ключи являются необязательными и разделяются пробелами, за исключением файлов, которые разделяются запятыми. Если не указан ни один ключ, программа **Ssms** откроет [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] в соответствии с настройками пункта **Параметры** в меню **Сервис** . Например, если для параметра **При запуске** на странице **Среда — Общие** задано значение **Открывать новое окно запроса**, программа **Ssms** откроется с пустым окном редактора запросов.  
  
 Ключ **-log** должен отображаться в конце командной строки после всех остальных ключей. Аргумент filename является необязательным. Если указано имя файла, а файл не существует, то он будет создан. Если файл создать невозможно, например, из-за недостаточных прав доступа, журнал будет записан в нелокализованное расположение APPDATA (см. ниже). Если аргумент filename не задан, в папку нелокализованных данных приложения текущего пользователя записываются два файла. Папку нелокализованных данных приложения для SQL Server можно найти по переменной среды APPDATA. Например, для SQL Server 2012 это папка \<системный_диск>:\Users\\<имя_пользователя\>\AppData\Roaming\Microsoft\AppEnv\10.0\\. Два файла имеют имена по умолчанию ActivityLog.xml и ActivityLog.xsl. Первый содержит данные журнала действий, а второй ― это таблица стилей XML, которая обеспечивает более удобный просмотр XML-файла. Для просмотра файла журнала в установленном по умолчанию средстве просмотра XML, например Internet Explorer, выполните следующие действия. Нажмите кнопку "Пуск", выберите "Выполнить...", затем в открывшемся поле введите \<системный_диск>:\Users\\<имя_пользователя\>\AppData\Roaming\Microsoft\AppEnv\10.0\ActivityLog.xml, после чего нажмите клавишу ВВОД.  
  
 Файлы, содержащие запросы, выведут запрос о подключении к серверу, если имеются сведения о соединении, а тип файла связан с этим типом сервера. Например, SQL-файлы в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]откроются в окне редактора SQL-запросов, а MDX-файлы откроются в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]в окне редактора запросов многомерных выражений. **Решения и проекты SQL Server** открываются в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 Следующая таблица показывает сопоставление типов серверов и расширений имен файлов.  
  
|Тип сервера|Расширение|  
|-----------------|---------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|.sql|  
|службы SQL Server Analysis Services|MDX<br /><br /> XMLA|  
  
## <a name="examples"></a>Примеры  
 Следующий скрипт открывает среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] из командной строки с настройками по умолчанию:  
  
```  
Ssms  
  
```  
  
 Следующий скрипт открывает среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] из командной строки с применением проверки подлинности Windows и с редактором кода, настроенным для сервера `ACCTG and the database AdventureWorks2012,` без показа экрана-заставки:  
  
```  
Ssms -E -S ACCTG -d AdventureWorks2012 -nosplash  
  
```  
  
 Следующий скрипт открывает среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] из командной строки и открывает скрипт MonthEndQuery:  
  
```  
Ssms "C:\Documents and Settings\username\My Documents\SQL Server Management Studio Projects\FinanceScripts\FinanceScripts\MonthEndQuery.sql"  
  
```  
  
 Следующий скрипт открывает среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] из командной строки и открывает проект NewReportsProject на компьютере с именем `developer`:  
  
```  
Ssms "\\developer\fin\ReportProj\ReportProj\NewReportProj.ssmssqlproj"  
  
```  
  
 Следующий скрипт открывает среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] из командной строки и открывает решение MonthlyReports:  
  
```  
Ssms "C:\solutionsfolder\ReportProj\MonthlyReports.ssmssln"  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование среды SQL Server Management Studio](http://msdn.microsoft.com/library/f289e978-14ca-46ef-9e61-e1fe5fd593be)  
  
  
