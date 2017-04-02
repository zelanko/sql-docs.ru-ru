---
title: "Источник OData | Microsoft Docs"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.DTS.DESIGNER.ODATASOURCE.F1"
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# Источник OData
  Компонент источника OData используется в пакете служб SSIS для получения данных от служб OData. Этот компонент поддерживает протоколы OData версии 3 и 4.  
  
-   Для протокола OData версии 3 компонент поддерживает форматы данных ATOM и JSON.  
  
-   Для протокола OData версии 4 компонент поддерживает формат данных JSON.  
  
> [!NOTE]  
>  Источник OData можно также использовать для чтения данных из списков SharePoint. Просмотреть все списки на сервере SharePoint можно по следующему URL-адресу: http://\<сервер>/_vti_bin/ListData.svc. Дополнительные сведения о соглашениях об URL-адресах SharePoint см. в разделе [Интерфейс REST SharePoint Foundation](http://msdn.microsoft.com/library/ff521587.aspx).  Источник OData теперь поддерживает продукты Microsoft Dynamics AX Online и Microsoft Dynamics CRM Online.
  
## <a name="odata-format"></a>Формат OData  
 Большинство служб OData возвращают результаты в различных форматах. Можно указать формат результирующего набора с помощью параметра $format запроса. Такие форматы, как JSON и JSON Light, более эффективны, чем ATOM или XML, и способны обеспечить более высокую производительность при передаче больших объемов данных. В следующей таблице отображаются результаты типовых тестов. Как видно, прирост производительности составил 30–53 % при переходе от ATOM к JSON и 67 % при переходе от ATOM к новому формату JSON Light (доступный в WCF Data Services 5.1).  
  
|||||  
|-|-|-|-|  
|Строки|ATOM|JSON|JSON (Light)|  
|10000|113 секунд|74 секунды|68 секунд|  
|1000000|1110 секунд|853 секунды|665 с|  
  
> [!NOTE]  
>  Источник OData служб SSIS использует версию 5.6.1 для синтаксического анализа каналов OData V3 и ODataLib 6.12.0 для синтаксического анализа каналов OData V4.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Учебник. Использование источника OData](../../integration-services/data-flow/tutorial-using-the-odata-source.md)  
  
-   [Изменение запроса источника OData во время выполнения](../../integration-services/data-flow/modify-odata-source-query-at-runtime.md)  
  
-   [Редактор источника OData (страница "Подключение")](../../integration-services/data-flow/odata-source-editor-connection-page.md)  
  
-   [Редактор источника OData (страница "Столбцы")](../../integration-services/data-flow/odata-source-editor-columns-page.md)  
  
-   [Редактор источника OData (страница "Вывод ошибок")](../../integration-services/data-flow/odata-source-editor-error-output-page.md)  
  
-   [Свойства источника OData](../../integration-services/data-flow/odata-source-properties.md)  
  
## <a name="see-also"></a>См. также:  
 [Диспетчер подключений OData](../../integration-services/connection-manager/odata-connection-manager.md)  
  
  