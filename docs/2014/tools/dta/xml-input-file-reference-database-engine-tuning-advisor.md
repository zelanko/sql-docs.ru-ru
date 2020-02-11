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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62509986"
---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a>Справочник по входным XML-файлам (помощник по настройке ядра СУБД)
  [!INCLUDE[ssDE](../../includes/ssde-md.md)]Для настройки базы данных помощник по настройке компонента может использовать входной XML-файл. Этот XML-файл определяет, какие базы данных, таблицы, файлы или таблицы рабочей нагрузки и параметры настройки должны быть использованы для сеанса настройки. Его можно также использовать в качестве пользовательской конфигурации для выполнения анализа вариантов.  
  
 Входной XML-файл помощника по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] содержит иерархию элементов XML, содержащих текстовые и прочие элементы, которые определяют параметры сеанса настройки. Входной XML-файл помощника по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] должен соответствовать стандартам XML-документов правильного формата, поэтому имена всех элементов обрабатываются с учетом регистра. Имена указываются в стиле языка Pascal, в котором принято, что первые буквы имен прописные, первая буква каждого из сцепленных слов прописная, а остальные — строчные.  
  
 Значения всех элементов должны соответствовать соглашениям об именах XML. Дополнительные сведения об этих соглашениях см. в статье [Текстовое содержимое XML](https://go.microsoft.com/fwlink/?LinkId=7614) библиотеки MSDN.  
  
 Обратите внимание, что этот справочник не является исчерпывающим. Дополнительные сведения обо всех элементах, используемых при определении входных данных XML, см. в XML-схеме помощника по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , файле DTASchema.xsd.  
  
## <a name="xml-declaration"></a>XML-декларация  
  
-   [SQL Server &#40;XML-данных&#41;](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a>Корневой элемент DTAXML  
  
-   [Элемент DTAXML &#40;DTA&#41;](dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a>Элементы DTAInput  
  
-   [Элемент DTAInput &#40;DTA&#41;](dtainput-element-dta.md)  
  
-   [Элемент Server (DTA)](server-element-dta.md)  
  
-   [Элемент рабочей нагрузки &#40;DTA&#41;](workload-element-dta.md)  
  
-   [Элемент TuningOptions &#40;DTA&#41;](tuningoptions-element-dta.md)  
  
-   [Элемент конфигурации &#40;DTA&#41;](configuration-element-dta.md)  
  
## <a name="server-elements"></a>Элементы для описания сервера  
  
-   [Элемент Name для сервера &#40;DTA&#41;](name-element-for-server-dta.md)  
  
-   [Элемент Database для сервера &#40;DTA&#41;](database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a>Элементы рабочей нагрузки  
  
-   [Файловый элемент &#40;DTA&#41;](file-element-dta.md)  
  
-   [Элемент Database для рабочей нагрузки &#40;DTA&#41;](database-element-for-workload-dta.md)  
  
-   [Элемент EventString &#40;DTA&#41;](eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a>Элементы для описания параметров настройки  
  
-   [Элемент TuningTimeInMin &#40;DTA&#41;](tuningtimeinmin-element-dta.md)  
  
-   [Элемент StorageBoundInMB &#40;DTA&#41;](storageboundinmb-element-dta.md)  
  
-   [Элемент TestServer &#40;DTA&#41;](testserver-element-dta.md)  
  
-   [Элемент "список_компонентов" &#40;DTA&#41;](featureset-element-dta.md)  
  
-   [Элемент секционирования &#40;DTA&#41;](partitioning-element-dta.md)  
  
-   [Элемент DropOnlyMode &#40;DTA&#41;](droponlymode-element-dta.md)  
  
-   [Элемент KeepExisting &#40;DTA&#41;](keepexisting-element-dta.md)  
  
-   [Элемент OnlineIndexOperation &#40;DTA&#41;](onlineindexoperation-element-dta.md)  
  
-   [Элемент DatabaseToConnect &#40;DTA&#41;](databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a>Элементы для описания конфигурации  
  
-   [Серверный элемент для &#40;конфигурации DTA&#41;](server-element-for-configuration-dta.md)  
  
-   [Элемент Database для &#40;конфигурации DTA&#41;](database-element-for-configuration-dta.md)  
  
-   [Элемент рекомендаций &#40;DTA&#41;](recommendation-element-dta.md)  
  
-   [Создать элемент &#40;DTA&#41;](create-element-dta.md)  
  
-   [Элемент index &#40;DTA&#41;](index-element-dta.md)  
  
-   [Элемент Name для индекса &#40;DTA&#41;](name-element-for-index-dta.md)  
  
-   [Элемент Column для индекса &#40;DTA&#41;](column-element-for-index-dta.md)  
  
-   [Элемент Name для столбца &#40;DTA&#41;](name-element-for-column-dta.md)  
  
-   [Элемент FILEGROUP для индекса &#40;DTA&#41;](filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a>Элементы для описания базы данных  
  
-   [Элемент Name для базы данных (DTA)](name-element-for-database-dta.md)  
  
-   [Элемент Schema описания базы данных (DTA)](schema-element-for-database-dta.md)  
  
-   [Элемент Name для Schema &#40;DTA&#41;](name-element-for-schema-dta.md)  
  
-   [Элемент Table для Schema &#40;DTA&#41;](table-element-for-schema-dta.md)  
  
-   [Элемент Name для таблицы &#40;DTA&#41;](name-element-for-table-dta.md)  
  
## <a name="see-also"></a>См. также:  
 [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
