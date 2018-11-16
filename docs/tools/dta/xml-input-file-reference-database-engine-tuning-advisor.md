---
title: Справочник по входным файлам XML (помощник по настройке ядра СУБД) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], XML input files
- input file reference [Database Engine Tuning Advisor]
- XML input files [Database Engine Tuning Advisor]
ms.assetid: 05e5e5f0-d6df-4336-b18e-e9bc2835a766
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1fa942cf89221dcfb66e78e6be77bbdd882e91b8
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51656359"
---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a>Справочник по входным XML-файлам (помощник по настройке ядра СУБД)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] может настраивать базу данных с помощью входного файла XML-данных. Этот XML-файл определяет, какие базы данных, таблицы, файлы или таблицы рабочей нагрузки и параметры настройки должны быть использованы для сеанса настройки. Его можно также использовать в качестве пользовательской конфигурации для выполнения анализа вариантов.  
  
 Входной XML-файл помощника по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] содержит иерархию элементов XML, содержащих текстовые и прочие элементы, которые определяют параметры сеанса настройки. Входной XML-файл помощника по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] должен соответствовать стандартам XML-документов правильного формата, поэтому имена всех элементов обрабатываются с учетом регистра. Имена указываются в стиле языка Pascal, в котором принято, что первые буквы имен прописные, первая буква каждого из сцепленных слов прописная, а остальные — строчные.  
  
 Значения всех элементов должны соответствовать соглашениям об именах XML. Дополнительные сведения об этих соглашениях см. в статье [Текстовое содержимое XML](https://go.microsoft.com/fwlink/?LinkId=7614) библиотеки MSDN.  
  
 Обратите внимание, что этот справочник не является исчерпывающим. Дополнительные сведения обо всех элементах, используемых при определении входных данных XML, см. в XML-схеме помощника по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , файле DTASchema.xsd.  
  
## <a name="xml-declaration"></a>XML-декларация  
  
-   [Данные XML (SQL Server)](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a>Корневой элемент DTAXML  
  
-   [Элемент DTAXML (DTA)](../../tools/dta/dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a>Элементы DTAInput  
  
-   [Элемент DTAInput (DTA)](../../tools/dta/dtainput-element-dta.md)  
  
-   [Элемент Server (DTA)](../../tools/dta/server-element-dta.md)  
  
-   [Элемент Workload (DTA)](../../tools/dta/workload-element-dta.md)  
  
-   [Элемент TuningOptions (DTA)](../../tools/dta/tuningoptions-element-dta.md)  
  
-   [Элемент Configuration (DTA)](../../tools/dta/configuration-element-dta.md)  
  
## <a name="server-elements"></a>Элементы для описания сервера  
  
-   [Элемент Name описания сервера (DTA)](../../tools/dta/name-element-for-server-dta.md)  
  
-   [Элемент Database описания сервера (DTA)](../../tools/dta/database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a>Элементы рабочей нагрузки  
  
-   [Элемент File (DTA)](../../tools/dta/file-element-dta.md)  
  
-   [Элемент Database для рабочей нагрузки (DTA)](../../tools/dta/database-element-for-workload-dta.md)  
  
-   [Элемент EventString (DTA)](../../tools/dta/eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a>Элементы для описания параметров настройки  
  
-   [Элемент TuningTimeInMin (DTA)](../../tools/dta/tuningtimeinmin-element-dta.md)  
  
-   [Элемент StorageBoundInMB (DTA)](../../tools/dta/storageboundinmb-element-dta.md)  
  
-   [Элемент TestServer (DTA)](../../tools/dta/testserver-element-dta.md)  
  
-   [Элемент FeatureSet (DTA)](../../tools/dta/featureset-element-dta.md)  
  
-   [Элемент Partitioning (DTA)](../../tools/dta/partitioning-element-dta.md)  
  
-   [Элемент DropOnlyMode (DTA)](../../tools/dta/droponlymode-element-dta.md)  
  
-   [Элемент KeepExisting (DTA)](../../tools/dta/keepexisting-element-dta.md)  
  
-   [Элемент OnlineIndexOperation (DTA)](../../tools/dta/onlineindexoperation-element-dta.md)  
  
-   [Элемент DatabaseToConnect (DTA)](../../tools/dta/databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a>Элементы для описания конфигурации  
  
-   [Элемент Server описания конфигурации (DTA)](../../tools/dta/server-element-for-configuration-dta.md)  
  
-   [Элемент Database описания конфигурации (DTA)](../../tools/dta/database-element-for-configuration-dta.md)  
  
-   [Элемент Recommendation (DTA)](../../tools/dta/recommendation-element-dta.md)  
  
-   [Элемент Create (DTA)](../../tools/dta/create-element-dta.md)  
  
-   [Элемент Index (DTA)](../../tools/dta/index-element-dta.md)  
  
-   [Элемент Name описания индекса (DTA)](../../tools/dta/name-element-for-index-dta.md)  
  
-   [Элемент Column описания индекса (DTA)](../../tools/dta/column-element-for-index-dta.md)  
  
-   [Элемент Name описания столбца (DTA)](../../tools/dta/name-element-for-column-dta.md)  
  
-   [Элемент Filegroup описания индекса (DTA)](../../tools/dta/filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a>Элементы для описания базы данных  
  
-   [Элемент Name описания базы данных (DTA)](../../tools/dta/name-element-for-database-dta.md)  
  
-   [Элемент Schema описания базы данных (DTA)](../../tools/dta/schema-element-for-database-dta.md)  
  
-   [Элемент Name описания схемы (DTA)](../../tools/dta/name-element-for-schema-dta.md)  
  
-   [Элемент Table для схемы (DTA)](../../tools/dta/table-element-for-schema-dta.md)  
  
-   [Элемент Name описания таблицы (DTA)](../../tools/dta/name-element-for-table-dta.md)  
  
## <a name="see-also"></a>См. также:  
 [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
