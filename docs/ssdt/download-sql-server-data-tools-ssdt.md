---
title: "Загрузка SQL Server Data Tools (SSDT) | Документация Майкрософт"
ms.custom: 
ms.date: 03/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssdt
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "установка SSDT, скачивание SSDT, последняя версия SSDT"
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 681ad2f6d7aeb88db45dde3f2e695db672b97dbd
ms.lasthandoff: 04/11/2017

---
# <a name="download-sql-server-data-tools-ssdt"></a>Скачать SQL Server Data Tools (SSDT)

**[SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/mt186501)** — это современное средство разработки ПО, которое можно бесплатно скачать для создания реляционных баз данных SQL Server, баз данных SQL Azure, пакетов служб Integration Services, моделей данных служб Analysis Services и отчетов служб Reporting Services. С помощью SSDT вы можете проектировать и развертывать любые типы содержимого SQL Server так же просто, как разрабатывать приложения в Visual Studio. Этот выпуск поддерживает версии от SQL Server 2016 до SQL Server 2005 и предоставляет среду проектирования для добавления компонентов, новых для SQL Server 2016.  
    
    
| ![скачиваемого файла](../ssdt/media/download.png) Скачать SQL Server Data Tools для Visual Studio 2015  | Скачать Data-Tier Application Framework (DacFx) ||
|:---|:---|:---|
|**[Скачать SQL Server Data Tools (16.5)](https://msdn.microsoft.com/mt186501)**|[**Скачать DacFx и SqlPackage.exe (16.5)**](https://www.microsoft.com/download/details.aspx?id=54106) |Текущий выпуск общедоступной версии для использования в рабочей среде.|
|[**Скачать SQL Server Data Tools — релиз-кандидат**](../ssdt/sql-server-data-tools-ssdt-release-candidate.md)| [**Скачать DacFx и SqlPackage.exe — релиз-кандидат**](../ssdt/sql-server-data-tools-ssdt-release-candidate.md) |Включает поддержку SQL Server vNext.|



## <a name="download-visual-studio"></a>Скачивание Visual Studio

* [**Скачать Visual Studio Community 2015**](https://www.visualstudio.com/products/visual-studio-community-vs.aspx)

### <a name="use-ssdt-in-visual-studio-2017"></a>Использование SSDT в Visual Studio 2017

* [**Скачать Visual Studio 2017**](https://www.visualstudio.com/) ([сравнение функций Visual Studio 2017 по выпускам](https://www.visualstudio.com/vs/compare/))

Чтобы использовать проекты реляционной базы данных, мы рекомендуем выбрать рабочую нагрузку **хранения и обработки данных** во время установки. Поддержка проекта базы данных SSDT также реализована в числе других рабочих нагрузок, таких как *Azure*, *разработка ASP.Net и веб-разработка*, а также *кроссплатформенная разработка .Net Core*.

Если используется SSDT со средой Visual Studio 2017, установите компоненты AS и RS:
* [службы Analysis Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects);
* [службы Reporting Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio).


## <a name="installing-ssdt-without-visual-studio-pre-installed"></a>Установка SSDT без предварительной установки Visual Studio

Если на вашем компьютере не установлена среда Visual Studio, то при установке SSDT для Visual Studio 2015 также будет установлена минимальная версия Visual Studio 2015 с "интегрированной оболочкой". Эта версия Visual Studio бесплатна, и ее можно устанавливать и использовать на любом количестве компьютеров. В ней можно использовать все типы проектов SQL Server, а также обозреватель объектов SQL Server и другие средства SQL.

Если на вашем компьютере установлена среда [Visual Studio 2015 Community Edition (или более поздняя версия)](https://www.visualstudio.com/products/visual-studio-community-vs.aspx), то при установке SSDT к установленной среде Visual Studio будет добавлен полный набор средств SQL Server. Visual Studio содержит множество функций, которые стоит использовать, например, интеграция с системами управления версиями и поддержка языков, отличных от SQL. Для получения наилучших результатов при разработке с T-SQL мы рекомендуем использовать Visual Studio 2015 Community или более позднюю версию.

## <a name="supported-sql-versions"></a>Поддерживаемые версии SQL
  
|Шаблоны проектов|Поддерживаемые платформы SQL|  
|-------------------|--------------------|  
реляционные базы данных|  SQL Server 2005* — SQL Server 2016 <br /><br />База данных SQL Azure<br /><br />Хранилище данных SQL Azure (поддерживает только запросы, но пока не поддерживает проекты базы данных)<br /><br />  * Версия SQL Server 2005 не поддерживается,<br /><br /> перейдите к официально поддерживаемой версии SQL.|
  |Модели служб Analysis Services<br /><br />Reporting Services, отчеты служб | SQL Server 2008 — SQL Server 2016|
  |пакеты служб Integration Services| SQL Server 2012 — SQL Server 2016    |
  
## <a name="next-steps"></a>Следующие шаги  
После установки SSDT ознакомьтесь с этими руководствами, чтобы узнать, как создать базы данных, пакеты, модели данных и отчеты в SSDT:  
  
-   [Разработка базы данных вне сети с учетом проекта](https://msdn.microsoft.com/library/hh272702(v=vs.103).aspx)  
  
-   [Руководство по службам SSIS. Создание простого ETL-пакета](https://msdn.microsoft.com/library/ms169917.aspx)  
  
-   [Руководства по службам Analysis Services](https://msdn.microsoft.com/library/hh231701.aspx)  
  
-   [Создание простого табличного отчета (учебник по службам SSRS)](https://msdn.microsoft.com/library/ms167305.aspx)  
  
## <a name="see-also"></a>См. также:  
[SQL Server Data Tools в Visual Studio](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[Форум MSDN по SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Блог группы разработчиков SSDT](http://blogs.msdn.com/b/ssdt/)  
[Отзыв о SSDT в Connect](https://connect.microsoft.com/SQLServer/Feedback)  
[Документация по SSDT](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[Справочник по API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Скачивание SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  

