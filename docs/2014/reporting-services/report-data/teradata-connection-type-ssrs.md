---
title: Тип соединения Teradata (службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b02779c2-a6b9-453c-815f-adad53353952
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6609ffe7c70169a2c261ca6103eeb74d34a62533
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37292244"
---
# <a name="teradata-connection-type-ssrs"></a>Тип соединения Teradata (службы SSRS)
  Чтобы включить в отчет данные из реляционной базы данных Teradata, необходимо иметь набор данных, основанный на источнике данных отчета типа Teradata. Этот встроенный тип источника данных основан на управляемом поставщике .NET для модуля обработки данных Teradata.  
  
 Используйте сведения в этом разделе для создания источника данных. Пошаговые инструкции см. в разделе [Добавление и проверка подключения к данным или источнику данных &#40;построитель отчетов и службы SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="Connection"></a> Строка подключения  
 Данные для строки соединения и учетные данные для подключения к источнику данных можно получить у администратора базы данных. В следующем примере строки соединения указана база данных Teradata на сервере, заданном с помощью IP-адреса:  
  
```  
data source=<IP Address>  
```  
  
 Дополнительные примеры строк соединения см. в разделе [Подключения к данным, источники данных и строки подключения в построителе отчетов](../data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
##  <a name="Credentials"></a> Учетные данные  
 Учетные данные необходимы для запуска запросов, локального предварительного просмотра отчетов, а также для предварительного просмотра отчетов на сервере отчетов.  
  
 После публикации отчета может понадобиться изменить учетные данные источника данных, чтобы разрешения, необходимые для получения данных при запуске отчета на сервере отчетов, были допустимыми.  
  
 Дополнительные сведения см. в разделе [подключения к данным, источники данных и строки подключения в службах Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) или [указание учетных данных в построителе отчетов](../specify-credentials-in-report-builder.md).  
  
 ![Значок стрелки, используемый для ссылки возврата в начало](../../2014-toc/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало") [В начало](#BackToTop)  
  
##  <a name="Remarks"></a> Замечания  
 Прежде чем подключиться к источнику данных Teradata, системный администратор должен установить версию поставщика данных .NET для Teradata, поддерживающую получение данных из базы данных Teradata. Этот поставщик данных должен быть установлен на компьютере, где работает построитель отчетов, а также на сервере отчетов.  
  
 Этот поставщик данных поддерживает не все режимы доставки отчетов. Доставка отчетов с помощью управляемых данными подписок для этого модуля обработки данных не предусмотрена. Дополнительные сведения см. в разделе [Использование внешнего источника данных для данных подписчика (управляемая данными подписка)](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md) документации по службам [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в [электронной документации](http://go.microsoft.com/fwlink/?linkid=121312) по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 ![Значок стрелки, используемый для ссылки возврата в начало](../../2014-toc/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало") [В начало](#BackToTop)  
  
##  <a name="Models"></a> Модели отчетов  
 Чтобы создать набор данных из модели отчета, основанной на источнике данных Teradata, эта модель должна быть создана в конструкторе моделей среды [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] и опубликована на сервере отчетов.  
  
 ![Значок стрелки, используемый для ссылки возврата в начало](../../2014-toc/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало") [В начало](#BackToTop)  
  
##  <a name="Related"></a> См. также  
 В этих разделах документации содержатся подробные сведения о данных отчетов, а также методические сведения об определении, настройке и использовании элементов отчетов, связанных с данными.  
  
 [Добавление данных в отчет &#40;построитель отчетов и службы SSRS&#41;](report-datasets-ssrs.md)  
 Предоставляет общие сведения о доступе к данным отчета.  
  
 [Подключения к данным, источники данных и строки подключения в построителе отчетов](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 Предоставляет сведения о подключениях к данным и источникам данных.  
  
 [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Предоставляет сведения об общих и внедренных наборах данных.  
  
 [Коллекция полей набора данных (построитель отчетов и службы SSRS)](dataset-fields-collection-report-builder-and-ssrs.md)  
 Предоставляет сведения о коллекции полей, создаваемой запросом набора данных.  
  
 [Источники данных, поддерживаемые службами Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md), см. в документации [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] в [электронной документации](http://go.microsoft.com/fwlink/?linkid=121312) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
 Предоставляет подробные сведения о поддержке платформ и версий для каждого модуля обработки данных.  
  
 [Использование служб SQL Server 2008 Reporting Services с поставщиком данных .NET Framework для Teradata](http://go.microsoft.com/fwlink/?LinkID=130848)  
 Предоставляет подробные сведения о работе с этим модулем обработки данных.  
  
 ![Значок стрелки, используемый для ссылки возврата в начало](../../2014-toc/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало") [В начало](#BackToTop)  
  
## <a name="see-also"></a>См. также  
 [Параметры отчета (построитель отчетов и конструктор отчетов)](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Фильтрация, группирование и сортировка данных (построитель отчетов и службы SSRS)](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Выражения (построитель отчетов и службы SSRS)](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
