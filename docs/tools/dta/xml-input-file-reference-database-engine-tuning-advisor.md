---
title: "Входные XML-ссылку на файл (помощник по настройке компонента Database Engine) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], XML input files
- input file reference [Database Engine Tuning Advisor]
- XML input files [Database Engine Tuning Advisor]
ms.assetid: 05e5e5f0-d6df-4336-b18e-e9bc2835a766
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d98a6bfc0fc61d76c434f20609205c52c202a257
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a>Справочник по входным XML-файлам (помощник по настройке ядра СУБД)
  [!INCLUDE[ssDE](../../includes/ssde-md.md)]Помощник по настройке ядра СУБД можно использовать для настройки базы данных входной XML-файл. Этот XML-файл определяет, какие базы данных, таблицы, файлы или таблицы рабочей нагрузки и параметры настройки должны быть использованы для сеанса настройки. Его можно также использовать в качестве пользовательской конфигурации для выполнения анализа вариантов.  
  
 Входной XML-файл помощника по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] содержит иерархию элементов XML, содержащих текстовые и прочие элементы, которые определяют параметры сеанса настройки. Входной XML-файл помощника по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] должен соответствовать стандартам XML-документов правильного формата, поэтому имена всех элементов обрабатываются с учетом регистра. Имена указываются в стиле языка Pascal, в котором принято, что первые буквы имен прописные, первая буква каждого из сцепленных слов прописная, а остальные — строчные.  
  
 Значения всех элементов должны соответствовать соглашениям об именах XML. Дополнительные сведения об этих соглашениях см. в статье [Текстовое содержимое XML](http://go.microsoft.com/fwlink/?LinkId=7614) библиотеки MSDN.  
  
 Обратите внимание, что этот справочник не является исчерпывающим. Дополнительные сведения обо всех элементах, используемых при определении входных данных XML, см. в XML-схеме помощника по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , файле DTASchema.xsd.  
  
## <a name="xml-declaration"></a>XML-декларация  
  
-   [Данные XML (SQL Server)](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a>Корневой элемент DTAXML  
  
-   [Элемент DTAXML &#40; DTA &#41;](../../tools/dta/dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a>Элементы DTAInput  
  
-   [Элемент DTAInput &#40; DTA &#41;](../../tools/dta/dtainput-element-dta.md)  
  
-   [Элемент Server &#40; DTA &#41;](../../tools/dta/server-element-dta.md)  
  
-   [Элемент Workload &#40; DTA &#41;](../../tools/dta/workload-element-dta.md)  
  
-   [Элемент TuningOptions &#40; DTA &#41;](../../tools/dta/tuningoptions-element-dta.md)  
  
-   [Элемент конфигурации &#40; DTA &#41;](../../tools/dta/configuration-element-dta.md)  
  
## <a name="server-elements"></a>Элементы для описания сервера  
  
-   [Элемент Name описания сервера &#40; DTA &#41;](../../tools/dta/name-element-for-server-dta.md)  
  
-   [Элемент Database описания сервера &#40; DTA &#41;](../../tools/dta/database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a>Элементы рабочей нагрузки  
  
-   [Элемент файла &#40; DTA &#41;](../../tools/dta/file-element-dta.md)  
  
-   [Элемент Database описания рабочей нагрузки &#40; DTA &#41;](../../tools/dta/database-element-for-workload-dta.md)  
  
-   [Элемент EventString &#40; DTA &#41;](../../tools/dta/eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a>Элементы для описания параметров настройки  
  
-   [Элемент TuningTimeInMin &#40; DTA &#41;](../../tools/dta/tuningtimeinmin-element-dta.md)  
  
-   [Элемент StorageBoundInMB &#40; DTA &#41;](../../tools/dta/storageboundinmb-element-dta.md)  
  
-   [Элемент TestServer &#40; DTA &#41;](../../tools/dta/testserver-element-dta.md)  
  
-   [Элемент FeatureSet &#40; DTA &#41;](../../tools/dta/featureset-element-dta.md)  
  
-   [Секционирование элемент &#40; DTA &#41;](../../tools/dta/partitioning-element-dta.md)  
  
-   [Элемент DropOnlyMode &#40; DTA &#41;](../../tools/dta/droponlymode-element-dta.md)  
  
-   [Элемент KeepExisting &#40; DTA &#41;](../../tools/dta/keepexisting-element-dta.md)  
  
-   [Элемент OnlineIndexOperation &#40; DTA &#41;](../../tools/dta/onlineindexoperation-element-dta.md)  
  
-   [Элемент DatabaseToConnect &#40; DTA &#41;](../../tools/dta/databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a>Элементы для описания конфигурации  
  
-   [Элемент Server описания конфигурации &#40; DTA &#41;](../../tools/dta/server-element-for-configuration-dta.md)  
  
-   [Элемент Database описания конфигурации &#40; DTA &#41;](../../tools/dta/database-element-for-configuration-dta.md)  
  
-   [Элемент Recommendation &#40; DTA &#41;](../../tools/dta/recommendation-element-dta.md)  
  
-   [Создать элемент &#40; DTA &#41;](../../tools/dta/create-element-dta.md)  
  
-   [Элемент index &#40; DTA &#41;](../../tools/dta/index-element-dta.md)  
  
-   [Элемент Name описания индекса &#40; DTA &#41;](../../tools/dta/name-element-for-index-dta.md)  
  
-   [Элемент COLUMN описания индекса &#40; DTA &#41;](../../tools/dta/column-element-for-index-dta.md)  
  
-   [Элемент Name описания столбца &#40; DTA &#41;](../../tools/dta/name-element-for-column-dta.md)  
  
-   [Элемент FILEGROUP описания индекса &#40; DTA &#41;](../../tools/dta/filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a>Элементы для описания базы данных  
  
-   [Элемент Name описания базы данных &#40; DTA &#41;](../../tools/dta/name-element-for-database-dta.md)  
  
-   [Элемент schema описания базы данных &#40; DTA &#41;](../../tools/dta/schema-element-for-database-dta.md)  
  
-   [Элемент Name описания схемы &#40; DTA &#41;](../../tools/dta/name-element-for-schema-dta.md)  
  
-   [Элемент TABLE описания схемы &#40; DTA &#41;](../../tools/dta/table-element-for-schema-dta.md)  
  
-   [Элемент Name описания таблицы &#40; DTA &#41;](../../tools/dta/name-element-for-table-dta.md)  
  
## <a name="see-also"></a>См. также:  
 [помощник по настройке ядра СУБД](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  

