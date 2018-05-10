---
title: Тип подключения к Oracle (службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 01/11/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-data
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9db86dd2-beda-42d8-8af7-2629d58a8e3d
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 0003522f6da1a6e83535a6f7270bdf2e192d8cf5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="oracle-connection-type-ssrs"></a>Тип соединения Oracle (службы SSRS)
Чтобы использовать в отчете данные из базы данных Oracle, необходимо иметь набор данных, основанный на источнике данных Oracle. Этот встроенный тип источника данных напрямую использует поставщик .NET Framework для Oracle и требует наличия клиентского программного обеспечения Oracle.

Чтобы установить инструменты клиента Oracle, можно выполнить указанные ниже действия.
 
1.  Перейдите на [сайт загрузки Oracle](http://www.oracle.com/us/products/tools/index-090165.html).
2.  Скачайте ODAC 12c 4 выпуска (12.1.0.2.4) для Windows (64-разрядная версия для сервера, 32-разрядная версия для инструментов).
3.  Установите поставщик данных Oracle для .NET 4.
  
 Используйте сведения в этом разделе для создания источника данных. Пошаговые инструкции см. в разделе [Добавление и проверка подключения к данным (построитель отчетов и службы SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Строка подключения  
 Данные для строки соединения и учетные данные для подключения к источнику данных можно получить у администратора базы данных. В следующем примере строки соединения указывается база данных Oracle на сервере Oracle9 с использованием Юникода. Имя сервера должно соответствовать значению, определенному в файле конфигурации tnsnames.ora в качестве имени экземпляра сервера Oracle.  
  
```  
Data Source="Oracle"; Unicode="True"  
```  
  
 Дополнительные сведения о примерах строки подключения см. в разделе [Подключения к данным, источники данных и строки подключения в построителе отчетов](http://msdn.microsoft.com/library/7e103637-4371-43d7-821c-d269c2cc1b34).  
  
##  <a name="Credentials"></a> Учетные данные  
 Учетные данные необходимы для запуска запросов, локального предварительного просмотра отчетов, а также для предварительного просмотра отчетов на сервере отчетов.  
  
 После публикации отчета может понадобиться изменить учетные данные источника данных, чтобы разрешения, необходимые для получения данных при запуске отчета на сервере отчетов, были допустимыми.  
  
 Дополнительные сведения см. в разделах [Подключения к данным, источники данных и строки подключения (построитель отчетов и службы SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) и [Указание учетных данных в построителе отчетов](http://msdn.microsoft.com/library/7412ce68-aece-41c0-8c37-76a0e54b6b53).  
  
  
##  <a name="Query"></a> Запросы  
 Для создания набора данных можно выбрать хранимую процедуру из раскрывающегося списка или создать SQL-запрос. Чтобы построить запрос, воспользуйтесь текстовым конструктором запросов. Дополнительные сведения см. в разделе [Пользовательский интерфейс текстового конструктора запросов (построитель отчетов)](../../reporting-services/report-data/text-based-query-designer-user-interface-report-builder.md).  
  
 Можно указать хранимые процедуры, возвращающие только один результирующий набор. Использование курсорных запросов не поддерживается.  
  
##  <a name="Parameters"></a> Параметры  
 Если запрос включает переменные запроса, то автоматически создаются соответствующие параметры отчета. Этот модуль поддерживает именованные параметры. Oracle версии 9 или более поздней поддерживает параметры с несколькими значениями.  
  
 Параметры отчета создаются со значениями свойств по умолчанию, которые, возможно, потребуется изменить. Например, все параметры отчета имеют тип данных **Text**. После создания параметров отчета можно изменить значения по умолчанию. Дополнительные сведения см. в разделе [Параметры отчета (построитель отчетов и конструктор отчетов)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
  
##  <a name="Remarks"></a> Замечания  
 Прежде чем подключиться к источнику данных Oracle, системный администратор должен установить версию поставщика данных .NET для Oracle, поддерживающую получение данных из базы данных Oracle. Этот поставщик данных должен быть установлен на компьютере, где работает построитель отчетов, а также на сервере отчетов.  
  
 Дополнительные сведения см. в следующих разделах:  
  
-   [Использование поставщика данных .NET Framework для Oracle](http://go.microsoft.com/fwlink/?LinkId=112314) на узле msdn.microsoft.com  
  
-   [Как использовать службы Reporting Services для настройки и доступа к источнику данных Oracle](http://support.microsoft.com/kb/834305)  
  
-   [Как добавить разрешения для субъекта безопасности NETWORK SERVICE](http://support.microsoft.com/kb/870668)  
  
###### <a name="alternate-data-extensions"></a>Альтернативные модули обработки данных  
 Также данные из базы данных Oracle можно получить с помощью источника данных OLE DB. Дополнительные сведения см. в разделе [Тип соединения OLE DB (службы SSRS)](../../reporting-services/report-data/ole-db-connection-type-ssrs.md).  
  
###### <a name="report-models"></a>Модели отчетов  
 Также можно создавать модели на основе базы данных Oracle.  
  
###### <a name="platform-and-version-information"></a>Сведения о платформе и версии  
 Дополнительные сведения о поддержке платформ и версий см. в разделе [Источники данных, поддерживаемые службами Reporting Services (службы SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md) документации к [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в [электронной документации](http://go.microsoft.com/fwlink/?linkid=121312) по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
##  <a name="HowTo"></a> Инструкции  
 В этом разделе содержатся пошаговые инструкции по работе с подключениями к данным, источниками данных и наборами данных.  
  
 [Добавление и проверка подключения к данным (построитель отчетов и службы SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Создание общего или внедренного набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Добавление фильтра к набору данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="Related"></a> См. также  
 В этих разделах документации содержатся подробные сведения о данных отчетов, а также методические сведения об определении, настройке и использовании элементов отчетов, связанных с данными.  
  
 [Наборы данных отчетов (службы SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md)  
 Предоставляет общие сведения о доступе к данным отчета.  
  
 [Подключения к данным, источники данных и строки подключения в построителе отчетов](http://msdn.microsoft.com/library/7e103637-4371-43d7-821c-d269c2cc1b34)  
 Предоставляет сведения о подключениях к данным и источникам данных.  
  
 [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Предоставляет сведения об общих и внедренных наборах данных.  
  
 [Коллекция полей набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
 Предоставляет сведения о коллекции полей набора данных, создаваемой запросом.  
  
 [Источники данных, поддерживаемые службами Reporting Services &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md), см. в документации [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в [электронной документации](http://go.microsoft.com/fwlink/?linkid=121312) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 Предоставляет подробные сведения о поддержке платформ и версий для каждого модуля обработки данных.  
  
  
## <a name="see-also"></a>См. также:  
 [Параметры отчета (построитель отчетов и конструктор отчетов)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Фильтрация, группирование и сортировка данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Выражения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  
