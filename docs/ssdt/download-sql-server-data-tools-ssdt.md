---
title: "Загрузка SQL Server Data Tools (SSDT) | Документация Майкрософт"
ms.custom: 
ms.date: 01/05/2018
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssdt
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssdt
ms.tgt_pltfrm: 
ms.topic: article
keywords: "установка SSDT, скачивание SSDT, последняя версия SSDT"
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
caps.latest.revision: "113"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: 36b87035d4a578622d9bff9bb2b4aea159cf55b2
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="download-sql-server-data-tools-ssdt"></a>Скачать SQL Server Data Tools (SSDT)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
**[SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)** — это современное средство разработки, позволяющее создавать реляционные базы данных SQL Server, базы данных SQL Azure, пакеты Integration Services, модели данных Analysis Services и отчеты Reporting Services. Вы можете скачать его бесплатно. С помощью SSDT вы можете проектировать и развертывать любые типы содержимого SQL Server так же просто, как разрабатывать приложения в Visual Studio. 

Средства SSDT для Visual Studio 2017 (15.5.1) прошли этап предварительной версии и стали первым общедоступным выпуском. В этом выпуске имеется поддержка автономной установки с веб-интерфейсом для проектов баз данных SQL Server, Analysis Services, Reporting Services и Integration Services в Visual Studio 2017 15.5 и более поздних версиях.

| SSDT для Visual Studio 2017 | SSDT для Visual Studio 2015 | 
|:--|:--|
|[![скачать](../ssdt/media/download.png) Скачать SSDT для Visual Studio 2017 (15.5.1)](https://go.microsoft.com/fwlink/?LinkId=865748) | [![скачать](../ssdt/media/download.png) Скачать SSDT для Visual Studio 2015 (17.4)](https://go.microsoft.com/fwlink/?linkid=863440)|
|||

> [!IMPORTANT]
> Выпуск Visual Studio 2017 (15.5.1) аналогичен версии 15.5.0 за исключением исправления нескольких ошибок в установщике. Так как это практически одинаковые выпуски, не пытайтесь обновлять версию 15.5.0 до 15.5.1. Если у вас уже установлена версия Visual Studio 2017 (15.5.0), переходить на версию 15.5.1 нет смысла, так как проблемы с установщиком вам уже удалось решить. 
> 
> Перед установкой SSDT для Visual Studio 2017 (15.5.1) удалите расширения "Проекты служб Microsoft Analysis Services" и "Проекты служб Microsoft Reporting Services", если они уже установлены в Visual Studio 2017, и закройте все экземпляры Visual Studio. 
> 
> Локализованные версии SSDT для Visual Studio 2017 15.5.1 не поддерживают обновление с предварительной версии 15.4.0 на английском языке. Перед установкой версии 15.5.1 на других языках необходимо удалить предварительную версию 15.4.0 на английском языке. 


SSDT для Visual Studio 2015 и SSDT для Visual Studio 2017 используют DacFx 17.4: [скачайте Data-Tier Application Framework (DacFx) 17.4](https://www.microsoft.com/download/details.aspx?id=56356)



## <a name="ssdt-for-visual-studio-2017"></a>SSDT для Visual Studio 2017
**Сведения о версии**  
  
Номер выпуска: 15.5.1  
Номер сборки для этого выпуска: 14.0.16148.0

Полный список изменений доступен в [журнале изменений](changelog-for-sql-server-data-tools-ssdt.md).

К установке SSDT для Visual Studio 2017 предъявляются те же системные требования, что и к установке VS. Поддерживаемые операционные системы: Windows 7 с пакетом обновления 1 (SP1), Windows 8.1, Windows Server 2012 R2, Windows 10 или Windows Server 2016.  

### <a name="available-languages---ssdt-for-vs-2017"></a>Доступные языки — SSDT для VS 2017
  
Этот выпуск **SSDT для Visual Studio 2017** можно установить на следующих языках:  

[Китайский (КНР)]( https://go.microsoft.com/fwlink/?linkid=865748&clcid=0x804) | 
[Китайский (Тайвань)]( https://go.microsoft.com/fwlink/?linkid=865748&clcid=0x404) | 
[Английский (США)]( https://go.microsoft.com/fwlink/?linkid=865748&clcid=0x409) | 
[Французский]( https://go.microsoft.com/fwlink/?linkid=865748&clcid=0x40c)  
[Немецкий]( https://go.microsoft.com/fwlink/?linkid=865748&clcid=0x407) | 
[Итальянский]( https://go.microsoft.com/fwlink/?linkid=865748&clcid=0x410) | 
[Японский]( https://go.microsoft.com/fwlink/?linkid=865748&clcid=0x411) | 
[Корейский]( https://go.microsoft.com/fwlink/?linkid=865748&clcid=0x412) | 
[Португальский (Бразилия)]( https://go.microsoft.com/fwlink/?linkid=865748&clcid=0x416) | 
[Русский]( https://go.microsoft.com/fwlink/?linkid=865748&clcid=0x419) | 
[Испанский]( https://go.microsoft.com/fwlink/?linkid=865748&clcid=0x40a)  

## <a name="ssdt-for-visual-studio-2015"></a>SSDT для Visual Studio 2015
**Сведения о версии**  
  
Номер выпуска: 17.4

Номер сборки для этого выпуска: 14.0.61712.050
  
Полный список изменений доступен в [журнале изменений](changelog-for-sql-server-data-tools-ssdt.md).

### <a name="available-languages---ssdt-for-vs-2015"></a>Доступные языки — SSDT для VS 2015
  
Этот выпуск **SSDT для Visual Studio 2015** можно установить на следующих языках:  

[Китайский (КНР)]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x804) | 
[Китайский (Тайвань)]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x404) | 
[Английский (США)]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x409) | 
[Французский]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x40c)  
[Немецкий]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x407) | 
[Итальянский]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x410) | 
[Японский]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x411) | 
[Корейский]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x412) | 
[Португальский (Бразилия)]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x416) | 
[Русский]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x419) | 
[Испанский]( https://go.microsoft.com/fwlink/?linkid=863440&clcid=0x40a)  

### <a name="iso-images---ssdt-for-vs-2015"></a>Образы ISO — SSDT для VS 2015

ISO-образ SSDT можно использовать в качестве альтернативного способа установки SSDT или для настройки административной точки установки. ISO-образ представляет собой автономный файл, который содержит все компоненты, необходимые для SSDT, и его можно скачать с помощью диспетчера возобновляемой загрузки, который требуется при ограниченной или менее надежной пропускной способности сети. После скачивания ISO-образ можно подключить как диск или записать на DVD-диск.

> [!NOTE]
> Теперь доступны ISO-образы SSDT для VS 2015 версии 17.4.

[Китайский (КНР)]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x804) |
[Китайский (Тайвань)]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x404) |
[Английский (США)]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x409) |
[Французский]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x40c)  
[Немецкий]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x407) |
[Итальянский]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x410) |
[Японский]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x411) |
[Корейский]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x412) |
[Португальский (Бразилия)]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x416) |
[Русский]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x419) |
[Испанский]( https://go.microsoft.com/fwlink/?linkid=863443&clcid=0x40a)


## <a name="download-visual-studio"></a>Скачивание Visual Studio

* [**Скачивание Visual Studio**](https://www.visualstudio.com/downloads)

## <a name="installing-ssdt-without-visual-studio-pre-installed"></a>Установка SSDT без предварительной установки Visual Studio

Если на вашем компьютере не установлена среда Visual Studio, то при установке SSDT для Visual Studio будет также установлена минимальная версия Visual Studio. Эта версия Visual Studio бесплатна, и ее можно устанавливать и использовать на любом количестве компьютеров. В ней можно использовать все типы проектов SQL Server, а также *обозреватель объектов SQL Server* и другие инструменты SQL.

Если у вас уже установлена среда Visual Studio 2015 (или более поздняя версия), то при установке SSDT к среде Visual Studio будет добавлен полный набор инструментов SQL Server. Visual Studio содержит множество функций, которые стоит использовать, например, интеграция с системами управления версиями и поддержка языков, отличных от SQL. Для получения наилучших результатов при разработке с T-SQL рекомендуем использовать Visual Studio 2015 или более позднюю версию.


## <a name="supported-sql-versions"></a>Поддерживаемые версии SQL
  
|Шаблоны проектов|Поддерживаемые платформы SQL|  
|-------------------|--------------------|  
реляционные базы данных|  SQL Server 2005 * — SQL Server 2017 <br /><br />База данных SQL Azure<br /><br />Хранилище данных SQL Azure (поддерживает только запросы, но пока не поддерживает проекты базы данных)<br /><br />  * Версия SQL Server 2005 не поддерживается,<br /><br /> перейдите к официально поддерживаемой версии SQL.|
  |Модели служб Analysis Services<br /><br />Reporting Services, отчеты служб | SQL Server 2008 — SQL Server 2017|
  |пакеты служб Integration Services| SQL Server 2012 — SQL Server 2017    |
  
## <a name="next-steps"></a>Следующие шаги  
После установки SSDT ознакомьтесь с этими руководствами, чтобы узнать, как создать базы данных, пакеты, модели данных и отчеты в SSDT:  
  
-   [Разработка базы данных вне сети с учетом проекта](https://msdn.microsoft.com/library/hh272702(v=vs.103).aspx)  
  
-   [Руководство по службам SSIS. Создание простого ETL-пакета](../integration-services/ssis-how-to-create-an-etl-package.md)  
  
-   [Руководства по службам Analysis Services](../analysis-services/analysis-services-tutorials-ssas.md)  
  
-   [Создание простого табличного отчета (учебник по службам SSRS)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  
  

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]


## <a name="see-also"></a>См. также:  
[SQL Server Data Tools в Visual Studio](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[Форум MSDN по SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Блог группы разработчиков SSDT](http://blogs.msdn.com/b/ssdt/)  
[Документация по SSDT](https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx)  
[Справочник по API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Скачивание SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
