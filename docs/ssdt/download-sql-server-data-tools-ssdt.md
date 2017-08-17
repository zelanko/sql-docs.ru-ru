---
title: "Загрузка SQL Server Data Tools (SSDT) | Документация Майкрософт"
ms.custom: 
ms.date: 08/07/2017
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
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 3f12671ace99d5fefc199c7b1c2db31e5b3cfade
ms.openlocfilehash: 4bcceaeca15c3fa20cd797bda0182cf48f73a730
ms.contentlocale: ru-ru
ms.lasthandoff: 08/08/2017

---
# <a name="download-sql-server-data-tools-ssdt"></a>Скачать SQL Server Data Tools (SSDT)

**[SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)** — это современное средство разработки ПО, которое можно бесплатно скачать для создания реляционных баз данных SQL Server, баз данных SQL Azure, пакетов служб Integration Services, моделей данных служб Analysis Services и отчетов служб Reporting Services. С помощью SSDT вы можете проектировать и развертывать любые типы содержимого SQL Server так же просто, как разрабатывать приложения в Visual Studio. Этот выпуск поддерживает версии от SQL Server 2017 до SQL Server 2005 и предоставляет среду проектирования для добавления новых компонентов SQL Server.  
    
    
![скачать](../ssdt/media/download.png) [Скачать SQL Server Data Tools 17.2 для Visual Studio 2015](https://go.microsoft.com/fwlink/?linkid=852922)

![скачать](../ssdt/media/download.png) [Скачать Data-Tier Application Framework (DacFx) 17.2](https://www.microsoft.com/download/details.aspx?id=55713)

## <a name="sql-server-data-tools"></a>SQL Server Data Tools   
**Сведения о версии**  
  
Номер выпуска: 17.2  
Номер сборки для этого выпуска: 14.0.61707.300
  
**Новые возможности**

**Службы Analysis Services**

- В диалоговом окне "Роли" теперь можно настроить защиту на уровне объектов, чтобы повысить безопасность табличных моделей с уровнем совместимости 1400.
- Новая возможность выбора пользователей, не имеющих адресов электронной почты, в качестве участников ролей AAD в моделях Analysis Services Azure в проектах SSDT Analysis Services для Visual Studio 2017.
- Новое свойство "Всегда запрашивать" проектов Analysis Services Azure в табличных проектах SSDT Analysis Services, позволяющее настраивать кэширование учетных данных ADAL.


**Известные проблемы**

- Полный список изменений доступен в [журнале изменений](changelog-for-sql-server-data-tools-ssdt.md).
- Сообщить о проблемах можно на сайте [SSDT Connect Feedback](https://connect.microsoft.com/SQLServer/Feedback).

> [!NOTE]
> Для использования SQL Server Data Tools в Visual Studio 2017 обратитесь к [следующему](#use-ssdt-in-visual-studio-2017) разделу.

  **Доступные языки**  
  
 Этот выпуск SSDT можно установить на следующих языках.  
[Китайский (КНР)]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x804) | 
[Китайский (Тайвань)]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x404) | 
[Английский (США)]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x409) | 
[Французский]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x40c)  
[Немецкий]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x407) | 
[Итальянский]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x410) | 
[Японский]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x411) | 
[Корейский]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x412) | 
[Португальский (Бразилия)]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x416) | 
[Русский]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x419) | 
[Испанский]( https://go.microsoft.com/fwlink/?linkid=852922&clcid=0x40a)  

**ISO-образы**

ISO-образ SSDT можно использовать в качестве альтернативного способа установки SSDT или для настройки административной точки установки. ISO-образ представляет собой автономный файл, который содержит все компоненты, необходимые для SSDT, и его можно скачать с помощью диспетчера возобновляемой загрузки, который требуется при ограниченной или менее надежной пропускной способности сети. После скачивания ISO-образ можно подключить как диск или записать на DVD-диск.

[Китайский (КНР)]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x804) |
[Китайский (Тайвань)]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x404) |
[Английский (США)]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x409) |
[Французский]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x40c)  
[Немецкий]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x407) |
[Итальянский]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x410) |
[Японский]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x411) |
[Корейский]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x412) |
[Португальский (Бразилия)]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x416) |
[Русский]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x419) |
[Испанский]( https://go.microsoft.com/fwlink/?linkid=852942&clcid=0x40a)

## <a name="download-visual-studio"></a>Скачивание Visual Studio

* [**Скачать Visual Studio Community 2015**](https://www.visualstudio.com/products/visual-studio-community-vs.aspx)

## <a name="installing-ssdt-without-visual-studio-pre-installed"></a>Установка SSDT без предварительной установки Visual Studio

Если на вашем компьютере не установлена среда Visual Studio, то при установке SSDT для Visual Studio 2015 также будет установлена минимальная версия Visual Studio 2015 с "интегрированной оболочкой". Эта версия Visual Studio бесплатна, и ее можно устанавливать и использовать на любом количестве компьютеров. В ней можно использовать все типы проектов SQL Server, а также обозреватель объектов SQL Server и другие средства SQL.

Если на вашем компьютере установлена среда [Visual Studio 2015 Community Edition (или более поздняя версия)](https://www.visualstudio.com/products/visual-studio-community-vs.aspx), то при установке SSDT к установленной среде Visual Studio будет добавлен полный набор средств SQL Server. Visual Studio содержит множество функций, которые стоит использовать, например, интеграция с системами управления версиями и поддержка языков, отличных от SQL. Для получения наилучших результатов при разработке с T-SQL мы рекомендуем использовать Visual Studio 2015 Community или более позднюю версию.

## <a name="supported-sql-versions"></a>Поддерживаемые версии SQL
  
|Шаблоны проектов|Поддерживаемые платформы SQL|  
|-------------------|--------------------|  
реляционные базы данных|  SQL Server 2005 * — SQL Server 2017 <br /><br />База данных SQL Azure<br /><br />Хранилище данных SQL Azure (поддерживает только запросы, но пока не поддерживает проекты базы данных)<br /><br />  * Версия SQL Server 2005 не поддерживается,<br /><br /> перейдите к официально поддерживаемой версии SQL.|
  |Модели служб Analysis Services<br /><br />Reporting Services, отчеты служб | SQL Server 2008 — SQL Server 2017|
  |пакеты служб Integration Services| SQL Server 2012 — SQL Server 2017    |
  
## <a name="next-steps"></a>Следующие шаги  
После установки SSDT ознакомьтесь с этими руководствами, чтобы узнать, как создать базы данных, пакеты, модели данных и отчеты в SSDT:  
  
-   [Разработка базы данных вне сети с учетом проекта](https://msdn.microsoft.com/library/hh272702(v=vs.103).aspx)  
  
-   [Руководство по службам SSIS. Создание простого ETL-пакета](https://msdn.microsoft.com/library/ms169917.aspx)  
  
-   [Руководства по службам Analysis Services](https://msdn.microsoft.com/library/hh231701.aspx)  
  
-   [Создание простого табличного отчета (учебник по службам SSRS)](https://msdn.microsoft.com/library/ms167305.aspx)  
  
## <a name="use-ssdt-in-visual-studio-2017"></a>Использование SSDT в Visual Studio 2017 

* [**Скачать Visual Studio 2017**](https://www.visualstudio.com/) ([сравнение функций Visual Studio 2017 по выпускам](https://www.visualstudio.com/vs/compare/))

Чтобы использовать проекты реляционной базы данных, мы рекомендуем выбрать рабочую нагрузку **хранения и обработки данных** во время установки. Поддержка проекта базы данных SSDT также реализована в числе других рабочих нагрузок, таких как *Azure*, *разработка ASP.Net и веб-разработка*, а также *кроссплатформенная разработка .Net Core*.

> [!NOTE]
> Проекты базы данных SSDT в Visual Studio 2017 сейчас поддерживают выпуски SQL Server до SQL Server 2016 включительно.  Поддержка SQL Server 2017 будет добавлена в предстоящем обновлении Visual Studio 2017.

Если используется SSDT со средой Visual Studio 2017, установите компоненты AS и RS:
* [службы Analysis Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects);
* [службы Reporting Services](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio)


## <a name="see-also"></a>См. также:  
[SQL Server Data Tools в Visual Studio](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[Форум MSDN по SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Блог группы разработчиков SSDT](http://blogs.msdn.com/b/ssdt/)  
[Отзыв о SSDT в Connect](https://connect.microsoft.com/SQLServer/Feedback)  
[Документация по SSDT](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[Справочник по API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Скачивание SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  

