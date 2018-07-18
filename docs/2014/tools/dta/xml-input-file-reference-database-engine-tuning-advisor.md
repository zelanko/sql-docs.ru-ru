---
title: Справочник по входным файлам XML (помощник по настройке ядра СУБД) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], XML input files
- input file reference [Database Engine Tuning Advisor]
- XML input files [Database Engine Tuning Advisor]
ms.assetid: 05e5e5f0-d6df-4336-b18e-e9bc2835a766
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7ca9a22a2f6f4732a97387778484aae261fc0848
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37183491"
---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a>Справочник по входным XML-файлам (помощник по настройке ядра СУБД)
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] может настраивать базу данных с помощью входного файла XML-данных. Этот XML-файл определяет, какие базы данных, таблицы, файлы или таблицы рабочей нагрузки и параметры настройки должны быть использованы для сеанса настройки. Его можно также использовать в качестве пользовательской конфигурации для выполнения анализа вариантов.  
  
 Входной XML-файл помощника по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] содержит иерархию элементов XML, содержащих текстовые и прочие элементы, которые определяют параметры сеанса настройки. Входной XML-файл помощника по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] должен соответствовать стандартам XML-документов правильного формата, поэтому имена всех элементов обрабатываются с учетом регистра. Имена указываются в стиле языка Pascal, в котором принято, что первые буквы имен прописные, первая буква каждого из сцепленных слов прописная, а остальные — строчные.  
  
 Значения всех элементов должны соответствовать соглашениям об именах XML. Дополнительные сведения об этих соглашениях см. в статье [Текстовое содержимое XML](http://go.microsoft.com/fwlink/?LinkId=7614) библиотеки MSDN.  
  
 Обратите внимание, что этот справочник не является исчерпывающим. Дополнительные сведения обо всех элементах, используемых при определении входных данных XML, см. в XML-схеме помощника по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , файле DTASchema.xsd.  
  
## <a name="xml-declaration"></a>XML-декларация  
  
-   [Данные XML (SQL Server)](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a>Корневой элемент DTAXML  
  
-   [Элемент DTAXML &#40;DTA&#41;](dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a>Элементы DTAInput  
  
-   [Элемент DTAInput &#40;DTA&#41;](dtainput-element-dta.md)  
  
-   [Элемент Server &#40;DTA&#41;](server-element-dta.md)  
  
-   [Элемент Workload &#40;DTA&#41;](workload-element-dta.md)  
  
-   [Элемент TuningOptions &#40;DTA&#41;](tuningoptions-element-dta.md)  
  
-   [Элемент конфигурации &#40;DTA&#41;](configuration-element-dta.md)  
  
## <a name="server-elements"></a>Элементы для описания сервера  
  
-   [Элемент Name для Server &#40;DTA&#41;](name-element-for-server-dta.md)  
  
-   [Элемент Database описания сервера &#40;DTA&#41;](database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a>Элементы рабочей нагрузки  
  
-   [Файл элемента &#40;DTA&#41;](file-element-dta.md)  
  
-   [Элемент Database описания рабочей нагрузки &#40;DTA&#41;](database-element-for-workload-dta.md)  
  
-   [Элемент EventString &#40;DTA&#41;](eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a>Элементы для описания параметров настройки  
  
-   [Элемент TuningTimeInMin &#40;DTA&#41;](tuningtimeinmin-element-dta.md)  
  
-   [Элемент StorageBoundInMB &#40;DTA&#41;](storageboundinmb-element-dta.md)  
  
-   [Элемент TestServer &#40;DTA&#41;](testserver-element-dta.md)  
  
-   [Элемент FeatureSet &#40;DTA&#41;](featureset-element-dta.md)  
  
-   [Элемент partitioning &#40;DTA&#41;](partitioning-element-dta.md)  
  
-   [Элемент DropOnlyMode &#40;DTA&#41;](droponlymode-element-dta.md)  
  
-   [Элемент KeepExisting &#40;DTA&#41;](keepexisting-element-dta.md)  
  
-   [Элемент OnlineIndexOperation &#40;DTA&#41;](onlineindexoperation-element-dta.md)  
  
-   [Элемент DatabaseToConnect &#40;DTA&#41;](databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a>Элементы для описания конфигурации  
  
-   [Элемент Server описания конфигурации &#40;DTA&#41;](server-element-for-configuration-dta.md)  
  
-   [Элемент Database описания конфигурации &#40;DTA&#41;](database-element-for-configuration-dta.md)  
  
-   [Элемент Recommendation &#40;DTA&#41;](recommendation-element-dta.md)  
  
-   [Создать элемент &#40;DTA&#41;](create-element-dta.md)  
  
-   [Индекс элемента &#40;DTA&#41;](index-element-dta.md)  
  
-   [Элемент Name для индекса &#40;DTA&#41;](name-element-for-index-dta.md)  
  
-   [Элемент COLUMN описания индекса &#40;DTA&#41;](column-element-for-index-dta.md)  
  
-   [Элемент Name для столбца &#40;DTA&#41;](name-element-for-column-dta.md)  
  
-   [Элемент FILEGROUP описания индекса &#40;DTA&#41;](filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a>Элементы для описания базы данных  
  
-   [Элемент Name для базы данных &#40;DTA&#41;](name-element-for-database-dta.md)  
  
-   [Элемент schema описания базы данных &#40;DTA&#41;](schema-element-for-database-dta.md)  
  
-   [Элемент Name для схемы &#40;DTA&#41;](name-element-for-schema-dta.md)  
  
-   [Элемент таблицы для схемы &#40;DTA&#41;](table-element-for-schema-dta.md)  
  
-   [Элемент Name для таблицы &#40;DTA&#41;](name-element-for-table-dta.md)  
  
## <a name="see-also"></a>См. также  
 [помощник по настройке ядра СУБД](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
