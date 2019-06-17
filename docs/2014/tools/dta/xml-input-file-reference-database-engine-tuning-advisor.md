---
title: Справочник по входным файлам XML (помощник по настройке ядра СУБД) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: b560b36eb98ec73723a4ce25cb3c647f4962b634
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62509986"
---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a>Справочник по входным XML-файлам (помощник по настройке ядра СУБД)
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] может настраивать базу данных с помощью входного файла XML-данных. Этот XML-файл определяет, какие базы данных, таблицы, файлы или таблицы рабочей нагрузки и параметры настройки должны быть использованы для сеанса настройки. Его можно также использовать в качестве пользовательской конфигурации для выполнения анализа вариантов.  
  
 Входной XML-файл помощника по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] содержит иерархию элементов XML, содержащих текстовые и прочие элементы, которые определяют параметры сеанса настройки. Входной XML-файл помощника по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] должен соответствовать стандартам XML-документов правильного формата, поэтому имена всех элементов обрабатываются с учетом регистра. Имена указываются в стиле языка Pascal, в котором принято, что первые буквы имен прописные, первая буква каждого из сцепленных слов прописная, а остальные — строчные.  
  
 Значения всех элементов должны соответствовать соглашениям об именах XML. Дополнительные сведения об этих соглашениях см. в статье [Текстовое содержимое XML](https://go.microsoft.com/fwlink/?LinkId=7614) библиотеки MSDN.  
  
 Обратите внимание, что этот справочник не является исчерпывающим. Дополнительные сведения обо всех элементах, используемых при определении входных данных XML, см. в XML-схеме помощника по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , файле DTASchema.xsd.  
  
## <a name="xml-declaration"></a>XML-декларация  
  
-   [Данные XML (SQL Server)](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a>Корневой элемент DTAXML  
  
-   [Элемент DTAXML (DTA)](dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a>Элементы DTAInput  
  
-   [Элемент DTAInput (DTA)](dtainput-element-dta.md)  
  
-   [Элемент Server (DTA)](server-element-dta.md)  
  
-   [Элемент Workload (DTA)](workload-element-dta.md)  
  
-   [Элемент TuningOptions (DTA)](tuningoptions-element-dta.md)  
  
-   [Элемент Configuration (DTA)](configuration-element-dta.md)  
  
## <a name="server-elements"></a>Элементы для описания сервера  
  
-   [Элемент Name описания сервера (DTA)](name-element-for-server-dta.md)  
  
-   [Элемент Database описания сервера (DTA)](database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a>Элементы рабочей нагрузки  
  
-   [Элемент File (DTA)](file-element-dta.md)  
  
-   [Элемент Database для рабочей нагрузки (DTA)](database-element-for-workload-dta.md)  
  
-   [Элемент EventString (DTA)](eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a>Элементы для описания параметров настройки  
  
-   [Элемент TuningTimeInMin (DTA)](tuningtimeinmin-element-dta.md)  
  
-   [Элемент StorageBoundInMB (DTA)](storageboundinmb-element-dta.md)  
  
-   [Элемент TestServer (DTA)](testserver-element-dta.md)  
  
-   [Элемент FeatureSet (DTA)](featureset-element-dta.md)  
  
-   [Элемент Partitioning (DTA)](partitioning-element-dta.md)  
  
-   [Элемент DropOnlyMode (DTA)](droponlymode-element-dta.md)  
  
-   [Элемент KeepExisting (DTA)](keepexisting-element-dta.md)  
  
-   [Элемент OnlineIndexOperation (DTA)](onlineindexoperation-element-dta.md)  
  
-   [Элемент DatabaseToConnect (DTA)](databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a>Элементы для описания конфигурации  
  
-   [Элемент Server описания конфигурации (DTA)](server-element-for-configuration-dta.md)  
  
-   [Элемент Database описания конфигурации (DTA)](database-element-for-configuration-dta.md)  
  
-   [Элемент Recommendation (DTA)](recommendation-element-dta.md)  
  
-   [Элемент Create (DTA)](create-element-dta.md)  
  
-   [Элемент Index (DTA)](index-element-dta.md)  
  
-   [Элемент Name описания индекса (DTA)](name-element-for-index-dta.md)  
  
-   [Элемент Column описания индекса (DTA)](column-element-for-index-dta.md)  
  
-   [Элемент Name описания столбца (DTA)](name-element-for-column-dta.md)  
  
-   [Элемент Filegroup описания индекса (DTA)](filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a>Элементы для описания базы данных  
  
-   [Элемент Name описания базы данных (DTA)](name-element-for-database-dta.md)  
  
-   [Элемент Schema описания базы данных (DTA)](schema-element-for-database-dta.md)  
  
-   [Элемент Name описания схемы (DTA)](name-element-for-schema-dta.md)  
  
-   [Элемент Table для схемы (DTA)](table-element-for-schema-dta.md)  
  
-   [Элемент Name описания таблицы (DTA)](name-element-for-table-dta.md)  
  
## <a name="see-also"></a>См. также  
 [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
