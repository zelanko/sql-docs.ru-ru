---
title: Тип соединения Teradata (службы SSRS) | Документы Майкрософт
ms.date: 03/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.assetid: b02779c2-a6b9-453c-815f-adad53353952
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4c50b757f6866307b52106055fd5affbf46789c0
ms.sourcegitcommit: 1800fc15075bb17b50d0c18b089d8a64d87ae726
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66500134"
---
# <a name="teradata-connection-type-ssrs"></a>Тип соединения Teradata (службы SSRS)
  Чтобы включить в отчет данные из реляционной базы данных Teradata, необходимо иметь набор данных, основанный на источнике данных отчета типа Teradata. Этот встроенный тип источника данных основан на управляемом поставщике .NET для модуля обработки данных Teradata.  
  
 Используйте сведения в этом разделе для создания источника данных. Пошаговые инструкции см. в разделе [Добавление и проверка подключения к данным (построитель отчетов и службы SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Строка подключения  
 Данные для строки соединения и учетные данные для подключения к источнику данных можно получить у администратора базы данных. В следующем примере строки соединения указана база данных Teradata на сервере, заданном с помощью IP-адреса:  
  
```  
data source=<IP Address>  
```  
  
 Дополнительные примеры строк соединения см. в разделе [Подключения к данным, источники данных и строки подключения в построителе отчетов](data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
##  <a name="Credentials"></a> Учетные данные  
 Учетные данные необходимы для запуска запросов, локального предварительного просмотра отчетов, а также для предварительного просмотра отчетов на сервере отчетов.  
  
 После публикации отчета может понадобиться изменить учетные данные источника данных, чтобы разрешения, необходимые для получения данных при запуске отчета на сервере отчетов, были допустимыми.  
  
 Дополнительные сведения см. в разделе [подключения к данным, источники данных и строки подключения &#40;построитель отчетов и службы SSRS&#41; ](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md) или [задание учетных данных и сведений о соединении для источников данных отчета](specify-credential-and-connection-information-for-report-data-sources.md).  
  
  
##  <a name="Remarks"></a> Замечания  
 Прежде чем подключиться к источнику данных Teradata, системный администратор должен установить версию поставщика данных .NET для Teradata, поддерживающую получение данных из базы данных Teradata. Этот поставщик данных должен быть установлен на компьютере, где работает построитель отчетов, а также на сервере отчетов.  
  
 Этот поставщик данных поддерживает не все режимы доставки отчетов. Доставка отчетов с помощью управляемых данными подписок для этого модуля обработки данных не предусмотрена. Дополнительные сведения см. в разделе [Использование внешнего источника данных для данных подписчика (управляемая данными подписка)](../../reporting-services/subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md) документации по службам [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в [электронной документации](https://go.microsoft.com/fwlink/?linkid=121312) по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
##  <a name="Models"></a> Модели отчетов  
 Чтобы создать набор данных из модели отчета, основанной на источнике данных Teradata, эта модель должна быть создана в конструкторе моделей среды [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] и опубликована на сервере отчетов.  
  
  
##  <a name="Related"></a> См. также  
 В этих разделах документации содержатся подробные сведения о данных отчетов, а также методические сведения об определении, настройке и использовании элементов отчетов, связанных с данными.  
  
 [Наборы данных отчетов (службы SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md)  
 Предоставляет общие сведения о доступе к данным отчета.  
  
 [Подключения к данным, источники данных и строки подключения в построителе отчетов](data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
 Предоставляет сведения о подключениях к данным и источникам данных.  
  
 [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Предоставляет сведения об общих и внедренных наборах данных.  
  
 [Коллекция полей набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
 Предоставляет сведения о коллекции полей, создаваемой запросом набора данных.  
  
 [Источники данных, поддерживаемые службами Reporting Services &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md), см. в документации [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в [электронной документации](https://go.microsoft.com/fwlink/?linkid=121312) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 Предоставляет подробные сведения о поддержке платформ и версий для каждого модуля обработки данных.  
  
 [Использование служб SQL Server 2008 Reporting Services с поставщиком данных .NET Framework для Teradata](https://go.microsoft.com/fwlink/?LinkID=130848)  
 Предоставляет подробные сведения о работе с этим модулем обработки данных.  
  
  
## <a name="see-also"></a>См. также:  
 [Параметры отчета (построитель отчетов и конструктор отчетов)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Фильтрация, группирование и сортировка данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Выражения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  
