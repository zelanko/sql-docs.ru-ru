---
title: Загрузка SQL Server Data Tools (SSDT) | Документация Майкрософт
ms.custom: ''
ms.date: 07/02/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssdt
ms.reviewer: ''
ms.suite: sql
ms.technology: ssdt
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords:
- установка SSDT, скачивание SSDT, последняя версия SSDT
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 78eb769a8f37ca055628a89aeebe7dd444673434
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37988226"
---
# <a name="download-and-install-sql-server-data-tools-ssdt-for-visual-studio"></a>Скачивание и установка SQL Server Data Tools (SSDT) для Visual Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
**SQL Server Data Tools** — это современное средство разработки, позволяющее создавать реляционные базы данных SQL Server, базы данных SQL Azure, модели данных Analysis Services (AS), пакеты Integration Services (IS) и отчеты Reporting Services (RS). С помощью SSDT вы можете проектировать и развертывать любые типы содержимого SQL Server так же просто, как разрабатывать приложения в Visual Studio.

*Для большинства пользователей SQL Server Data Tools (SSDT) устанавливается во время установки Visual Studio. При установке SSDT с помощью установщика Visual Studio добавляется лишь базовая функциональность для SSDT, поэтому для получения средств AS, IS и RS по-прежнему необходимо запускать [автономный установщик SSDT](#ssdt-for-vs-2017-standalone-installer).*

## <a name="install-ssdt-with-visual-studio-2017"></a>Установка SSDT с Visual Studio 2017

Чтобы установить SSDT во время [установки Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio), выберите рабочую нагрузку **Хранение и обработка данных**, а затем выберите **SQL Server Data Tools**. Если среда Visual Studio уже установлена, вы можете [изменить список рабочих нагрузок](https://docs.microsoft.com/visualstudio/install/modify-visual-studio) для включения SSDT. ![Рабочая нагрузка хранения и обработки данных](../ssdt/media/download-sql-server-data-tools-ssdt/data-workload.png)



## <a name="install-analysis-services-integration-services-and-reporting-services-tools"></a>Установка средств Analysis Services, Integration Services и Reporting Services
Чтобы установить поддержку проектов AS, IS и RS, запустите [автономный установщик SSDT](#ssdt-for-vs-2017-standalone-installer). 

Установщик выводит список доступных экземпляров Visual Studio, в которые будут добавлены средства SSDT. Если среда Visual Studio не установлена, при выборе параметра **Установить новый экземпляр SQL Server Data Tools** выполняется установка SSDT с минимальной версией Visual Studio. Для получения наилучших результатов рекомендуется использовать SSDT с [последней версией Visual Studio](https://www.visualstudio.com/downloads). 

![выбор AS, IS, RS](../ssdt/media/download-sql-server-data-tools-ssdt/select-services.png)



## <a name="ssdt-for-vs-2017-standalone-installer"></a>SSDT для VS 2017 (автономный установщик)

[![скачать](../ssdt/media/download.png) Скачать SSDT для Visual Studio 2017 (15.7.1)](https://go.microsoft.com/fwlink/?linkid=875613) 

> [!IMPORTANT]
> - Перед установкой SSDT для Visual Studio 2017 (15.7.1) удалите расширения *Проекты Analysis Services* и *Проекты Reporting Services*, если они уже установлены, а затем закройте все экземпляры Visual Studio.
> - При установке SSDT в Windows 10 и выборе **установки нового экземпляра SQL Server Data Tools для Visual Studio 2017** снимите все флажки и сначала установите новый экземпляр. Установив новый экземпляр, перезагрузите компьютер и откройте установщик SSDT еще раз, чтобы продолжить установку.  



**Сведения о версии**  
  
Номер выпуска: 15.7.1  
Номер сборки: 14.0.16167.0  
Дата выпуска: 2 июня 2018 г.  

Полный список изменений доступен в [журнале изменений](changelog-for-sql-server-data-tools-ssdt.md).

SSDT для Visual Studio 2017 имеет те же [требования к системе](https://docs.microsoft.com/visualstudio/productinfo/vs2017-system-requirements-vs), что и Visual Studio.  

### <a name="available-languages---ssdt-for-vs-2017"></a>Доступные языки — SSDT для VS 2017

Этот выпуск **SSDT для Visual Studio 2017** можно установить на следующих языках:  

[Китайский (КНР)]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x804) | 
[Китайский (Тайвань)]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x404) | 
[Английский (США)]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x409) | 
[Французский]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x40c)  
[Немецкий]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x407) | 
[Итальянский]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x410) | 
[Японский]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x411) | 
[Корейский]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x412) | 
[Португальский (Бразилия)]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x416) | 
[Русский]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x419) | 
[Испанский]( https://go.microsoft.com/fwlink/?linkid=875613&clcid=0x40a)  



## <a name="ssdt-for-vs-2015-standalone-installer"></a>SSDT для VS 2015 (автономный установщик)

[![скачать](../ssdt/media/download.png) Скачать SSDT для Visual Studio 2015 (17.4)](https://go.microsoft.com/fwlink/?linkid=863440)

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



## <a name="supported-sql-versions"></a>Поддерживаемые версии SQL
  
|Шаблоны проектов|Поддерживаемые платформы SQL|  
|-------------------|--------------------|  
реляционные базы данных|  SQL Server 2005 * — SQL Server 2017<br> (используйте SSDT 17.x или SSDT for Visual Studio 2017 для подключения к [SQL Server на Linux](../linux/sql-server-linux-overview.md))<br /><br />База данных SQL Azure<br /><br />Хранилище данных SQL Azure (поддерживает только запросы, но пока не поддерживает проекты базы данных)<br /><br />  * Версия SQL Server 2005 не поддерживается,<br /><br /> перейдите к официально поддерживаемой версии SQL.|
  |Модели служб Analysis Services<br /><br />Reporting Services, отчеты служб | SQL Server 2008 — SQL Server 2017|
  |пакеты служб Integration Services| SQL Server 2012 — SQL Server 2017    |
  
## <a name="dacfx"></a>DacFx
SSDT для Visual Studio 2015 и SSDT для Visual Studio 2017 используют DacFx 17.4.1: [скачайте Data-Tier Application Framework (DacFx) 17.4.1](https://www.microsoft.com/download/details.aspx?id=56508).


## <a name="next-steps"></a>Следующие шаги  
После установки SSDT ознакомьтесь с этими руководствами, чтобы узнать, как создать базы данных, пакеты, модели данных и отчеты в SSDT:  

- [Разработка базы данных вне сети с учетом проекта](project-oriented-offline-database-development.md)  
- [Руководство по службам SSIS. Создание простого ETL-пакета](../integration-services/ssis-how-to-create-an-etl-package.md)  
- [Руководства по службам Analysis Services](../analysis-services/analysis-services-tutorials-ssas.md)  
- [Создание простого табличного отчета (учебник по службам SSRS)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]


## <a name="see-also"></a>См. также:  
[Форум MSDN по SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Блог группы разработчиков SSDT](http://blogs.msdn.com/b/ssdt/)  
[Справочник по API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Скачивание SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  