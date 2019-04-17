---
title: Загрузка SQL Server Data Tools (SSDT) | Документация Майкрософт
ms.custom: ''
ms.date: 04/05/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssdt
ms.topic: conceptual
keywords:
- установка SSDT, скачивание SSDT, последняя версия SSDT
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: b336589f59bef9087392ff141a4bd64df1ed76c8
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59243508"
---
# <a name="download-and-install-sql-server-data-tools-ssdt-for-visual-studio"></a>Скачивание и установка SQL Server Data Tools (SSDT) для Visual Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


**SQL Server Data Tools** — это современное средство разработки, позволяющее создавать реляционные базы данных SQL Server, базы данных SQL Azure, модели данных Analysis Services (AS), пакеты Integration Services (IS) и отчеты Reporting Services (RS). С помощью SSDT вы можете проектировать и развертывать любые типы содержимого SQL Server так же просто, как разрабатывать приложения в Visual Studio.


## <a name="changes-in-ssdt-for-visual-studio-2019"></a>Изменения в SSDT для Visual Studio 2019 ##

С выходом Visual Studio 2019 требуемые функции для поддержки Analysis Services, Integration Services и Reporting Services перемещены в соответствующие расширения Visual Studio. Основные функции SSDT для создания проектов баз данных остаются неотъемлемой частью Visual Studio (во время установки нужно выбрать рабочую нагрузку "Хранение и обработка данных").  Теперь не нужно устанавливать SSDT отдельно. 

Если у вас есть лицензия на Visual Studio 2019, сделайте следующее:
- Для проектов Базы данных SQL установите рабочую нагрузку "Хранение и обработка данных" в Visual Studio.
- Для проектов Analysis Services, Integration Services или Reporting Services установите соответствующие расширения из Marketplace.

Если у вас нет лицензии на Visual Studio 2019, сделайте следующее:
- Установите [Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&utm_campaign=tailored+install&utm_source=docs.microsoft.com&utm_medium=microsoft&utm_content=sqlssdt&rid=35007). 
- При необходимости установите Analysis Services, Integration Services и Reporting Services.

## <a name="changes-in-ssdt-for-visual-studio-2017"></a>Изменения в SSDT для Visual Studio 2017 ##

Начиная с Visual Studio 2017, функции создания проектов баз данных входят в пакет установки Visual Studio. Не нужно устанавливать автономный установщик SSDT для использования основных возможностей SSDT. Но для создания проектов Integration Services, Analysis Services и Reporting Services по-прежнему требуется автономный установщик SSDT. 

- Для проектов баз данных установите рабочую нагрузку "Хранение и обработка данных" для Visual Studio.
- Для проектов Analysis Services, Integration Services или Reporting Services скачайте и установите [SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-2017).




## <a name="install-ssdt-with-visual-studio-2017"></a>Установка SSDT с Visual Studio 2017

Чтобы установить SSDT во время [установки Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio), выберите рабочую нагрузку **Хранение и обработка данных**, а затем выберите **SQL Server Data Tools**. Если среда Visual Studio уже установлена, вы можете [изменить список рабочих нагрузок](https://docs.microsoft.com/visualstudio/install/modify-visual-studio) для включения SSDT. ![Рабочая нагрузка "Хранение и обработка данных"](../ssdt/media/download-sql-server-data-tools-ssdt/data-workload.png)

## <a name="install-analysis-services-integration-services-and-reporting-services-tools"></a>Установка средств Analysis Services, Integration Services и Reporting Services

Чтобы установить поддержку проектов AS, IS и RS, запустите [автономный установщик SSDT](#ssdt-for-vs-2017-standalone-installer). 

Установщик выводит список доступных экземпляров Visual Studio, в которые будут добавлены средства SSDT. Если среда Visual Studio не установлена, при выборе параметра **Установить новый экземпляр SQL Server Data Tools** выполняется установка SSDT с минимальной версией Visual Studio. Для получения наилучших результатов рекомендуется использовать SSDT с [последней версией Visual Studio](https://www.visualstudio.com/downloads). 

![выбор AS, IS, RS](../ssdt/media/download-sql-server-data-tools-ssdt/select-services.png)



## <a name="ssdt-for-vs-2017-standalone-installer"></a>SSDT для VS 2017 (автономный установщик)

[![dСкачать](../ssdt/media/download.png) Скачайте SSDT для Visual Studio 2017 (15.9.0)](https://go.microsoft.com/fwlink/?linkid=2052454) 

> [!IMPORTANT]
> - Перед установкой SSDT для Visual Studio 2017 (15.9.0) удалите расширения *Проекты Analysis Services* и *Проекты Reporting Services*, если они установлены, а затем закройте все экземпляры Visual Studio.
> - Используйте SSDT для Visual Studio 2017 вплоть до версии 15.8.0, чтобы создавать пакеты служб Integration Services, содержащие источники или назначения Teradata. С помощью SSDT для Visual Studio 2017 версий после15.8.0 нельзя создавать пакеты служб Integration Services, содержащие источники или назначения Teradata.


**Сведения о версии**  
  
Номер выпуска: 15.9.0  
Номер сборки: 14.0.16186.0  
Дата выпуска: 28 января 2019 г.  

Полный список изменений см. в [заметках о выпуске для SQL Server Data Tools (SSDT)](release-notes-ssdt.md).

SSDT для Visual Studio 2017 имеет те же [требования к системе](https://docs.microsoft.com/visualstudio/productinfo/vs2017-system-requirements-vs), что и Visual Studio.  

### <a name="available-languages---ssdt-for-vs-2017"></a>Доступные языки — SSDT для VS 2017

Этот выпуск **SSDT для Visual Studio 2017** можно установить на следующих языках:

- [Китайский (упрощенное письмо)]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x804)
- [Китайский (традиционный)]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x404)
- [Английский (США)]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x409)
- [Французский]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x40c)
- [Немецкий]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x407)
- [Итальянский]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x410)
- [Японский]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x411)
- [Корейский]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x412)
- [Португальский (Бразилия)]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x416)
- [Русский]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x419)
- [Испанский]( https://go.microsoft.com/fwlink/?linkid=2052454&clcid=0x40a)

## <a name="offline-install"></a>Автономная установка

Если вы не подключены к Интернету, следуйте инструкциям в этом разделе, чтобы установить SSDT. Дополнительные сведения см. в разделе [Создание сетевого подключения в Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/create-a-network-installation-of-visual-studio).

После подключения к Интернету первым делом выполните следующие действия.

1. [Скачайте автономный установщик SSDT](#ssdt-for-vs-2017-standalone-installer).
2. [Скачайте vs_sql.exe](https://aka.ms/vs/15/release/vs_sql.exe).
3. Не отключаясь от Интернета, выполните одну из следующих команд, чтобы скачать все файлы, необходимые для автономной установки. Обязательно используйте параметр `--layout`, чтобы непосредственно скачать файлы для автономной установки. Замените `<filepath>` на фактический путь макетов, чтобы сохранить файлы.

   
   A.   Для установки конкретного языка передайте локаль: `vs_sql.exe --layout c:\<filepath> --lang en-us` (размер версии с одним языком — примерно 1 ГБ)  
   Б. Для установки всех языков пропустите аргумент `--lang`: `vs_sql.exe --layout c:\<filepath>` (размер версии со всеми языками — примерно 3,9 ГБ).

4. Выполните `SSDT-Setup-ENU.exe /layout c:\<filepath>`, чтобы извлечь полезные данные SSDT в то же место `<filepath>`, куда были скачаны файлы VS2017. Это гарантирует, что все файлы будут находиться в одной папке макетов.

Дальнейшие действия можно выполнить в автономном режиме.

1. Запустите `vs_setup.exe --NoWeb`, чтобы установить оболочку VS2017 Shell и SQL Server Data Project.
2. В папке макетов запустите `SSDT-Setup-ENU.exe /install` и выберите SSIS/SSRS/SSAS.

   - Для автоматической установки выполните команду `SSDT-Setup-ENU.exe /INSTALLALL[:vsinstances] /passive`  

Для отображения доступных параметров выполните команду `SSDT-Setup-ENU.exe /help`

> [!NOTE]
> При использовании полной версии Visual Studio 2017 создайте автономную папку только для SSDT и запустите `SSDT-Setup-ENU.exe` из нее (не добавляйте SSDT в другой автономный макет Visual Studio 2017). При добавлении макета SSDT в существующий автономный макет Visual Studio необходимые компоненты времени выполнения (.exe) не создаются.

## <a name="supported-sql-versions"></a>Поддерживаемые версии SQL
  
|Шаблоны проектов|Поддерживаемые платформы SQL|  
|-------------------|--------------------|  
|реляционные базы данных|  SQL Server 2005\* — SQL Server 2017<br> (используйте SSDT 17.x или SSDT for Visual Studio 2017 для подключения к [SQL Server на Linux](../linux/sql-server-linux-overview.md))<br /><br />База данных SQL Azure<br /><br />Хранилище данных SQL Azure (поддерживает только запросы, но пока не поддерживает проекты базы данных)<br /><br /> \* Версия SQL Server 2005 не поддерживается,<br /><br /> перейдите к официально поддерживаемой версии SQL.|
|Модели служб Analysis Services<br /><br />Reporting Services, отчеты служб | SQL Server 2008 — SQL Server 2017|
|пакеты служб Integration Services| SQL Server 2012 — SQL Server 2019 |
  
## <a name="dacfx"></a>DacFx

SSDT для Visual Studio 2015 и SSDT для Visual Studio 2017 используют DacFx 17.4.1: [Скачать Data-Tier Application Framework (DacFx) 17.4.1](https://www.microsoft.com/download/details.aspx?id=56508).

## <a name="previous-versions"></a>Предыдущие версии

Чтобы скачать и установить SSDT для Visual Studio 2015 или более старую версию SSDT, см. [Предыдущие выпуски SQL Server Data Tools (SSDT и SSDT-BI)](previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi.md).

## <a name="next-steps"></a>Следующие шаги

После установки SSDT ознакомьтесь с этими руководствами, чтобы узнать, как создать базы данных, пакеты, модели данных и отчеты в SSDT:  

- [Разработка базы данных вне сети с учетом проекта](project-oriented-offline-database-development.md)  
- [Руководство по службам SSIS. Создание простого ETL-пакета](../integration-services/ssis-how-to-create-an-etl-package.md)  
- [Руководства по службам Analysis Services](../analysis-services/analysis-services-tutorials-ssas.md)  
- [Создание простого табличного отчета (учебник по службам SSRS)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

## <a name="see-also"></a>См. также:

[Форум MSDN по SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Блог группы разработчиков SSDT](https://blogs.msdn.com/b/ssdt/)  
[Справочник по API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Скачивание SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  