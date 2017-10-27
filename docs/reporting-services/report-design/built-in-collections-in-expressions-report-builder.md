---
title: "Встроенные коллекции в выражениях (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d5e3b8-9320-4e4b-a025-e2de3cf7afa7
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: ff834d00c915ae81179ff9b0bebed19e7c9ec6c1
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="built-in-collections-in-expressions-report-builder"></a>Встроенные коллекции в выражениях (построитель отчетов)
  В выражение в отчете можно включить ссылки на следующие встроенные коллекции: ReportItems, Parameters, Fields, DataSets, DataSources, Variables и встроенные поля для общих сведений, таких как имя отчета. В диалоговом окне **Выражения** отображаются не все коллекции. Коллекции DataSets и DataSources доступны только во время выполнения для отчетов, опубликованных на сервере отчетов. Коллекция ReportItems является коллекцией текстовых полей в области отчета, например текстовых полей на странице или в верхнем колонтитуле.  
  
 Дополнительные сведения см. в разделе [Выражения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="Collections"></a> Основные сведения о встроенных коллекциях  
 В следующей таблице перечислены встроенные коллекции, доступные при написании выражения. Каждая строка включает программное имя коллекции с учетом регистра, признак, можно ли использовать диалоговое окно «Выражение» для интерактивного добавления в коллекцию ссылки, пример и описание, включающее сведения о том, когда инициализируются и становятся доступными для использования значения коллекции.  
  
|Встроенная коллекция|Категория в диалоговом окне «Выражение»|Пример|Description|  
|--------------------------|-------------------------------------------|-------------|-----------------|  
|**Глобальные переменные**|Встроенные поля|`=Globals.ReportName`<br /><br /> `- or -`<br /><br /> `=Globals.PageNumber`|Представляет глобальные переменные, полезные для отчетов, например для имени отчета или номера страницы. Доступна всегда.<br /><br /> Дополнительные сведения см. в разделе [Встроенные глобальные значения и ссылки на пользовательские поля (построитель отчетов и службы SSRS)](../../reporting-services/report-design/built-in-collections-built-in-globals-and-users-references-report-builder.md).|  
|**Пользователь**|Встроенные поля|`=User.UserID`<br /><br /> — или —<br /><br /> `=User.Language`|Представляет коллекцию сведений о пользователе, выполняющем отчет, например языковые настройки или идентификатор пользователя. Доступна всегда.<br /><br /> Дополнительные сведения см. в разделе [Встроенные глобальные значения и ссылки на пользовательские поля (построитель отчетов и службы SSRS)](../../reporting-services/report-design/built-in-collections-built-in-globals-and-users-references-report-builder.md).|  
|**Параметры**|Параметры|`=Parameters("ReportMonth").Value`<br /><br /> — или —<br /><br /> `=Parameters!ReportYear.Value`|Представляет коллекцию параметров отчета, каждый из которых может быть однозначным или многозначным. Недоступна до завершения обработки инициализации. Дополнительные сведения см. в разделе [Ссылки на коллекцию параметров (построитель отчетов и службы SSRS)](../../reporting-services/report-design/built-in-collections-parameters-collection-references-report-builder.md).|  
|**Поля (**  *\<набора данных >* **)**|Поля|`=Fields!Sales.Value`|Представляет коллекцию полей набора данных, доступных для отчета. Доступна после получения данных из источника данных в набор данных. Дополнительные сведения см. в разделе [Ссылки на коллекцию полей набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/built-in-collections-dataset-fields-collection-references-report-builder.md).|  
|**Коллекция DataSets**|Не отображается|`=DataSets("TopEmployees").CommandText`|Представляет коллекцию наборов данных, к которым выполняется обращение из тела определения отчета. Не включает источники данных, которые используются только в верхних или нижних колонтитулах. Недоступна в режиме локального предварительного просмотра. Дополнительные сведения см. в разделе [Ссылки на коллекции DataSources и DataSets (построитель отчетов и службы SSRS)](../../reporting-services/report-design/built-in-collections-datasources-and-datasets-references-report-builder.md).|  
|**Коллекция DataSources**|Не отображается|`=DataSources("AdventureWorks2012").Type`|Представляет коллекцию источников данных, к которым выполняется обращение из тела отчета. Не включает источники данных, которые используются только в верхних или нижних колонтитулах. Недоступна в режиме локального предварительного просмотра. Дополнительные сведения см. в разделе [Ссылки на коллекции DataSources и DataSets (построитель отчетов и службы SSRS)](../../reporting-services/report-design/built-in-collections-datasources-and-datasets-references-report-builder.md).|  
|**Переменные**|`Variables`|`=Variables!CustomTimeStamp.Value`|Представляет коллекцию переменных отчета и групповых переменных. Дополнительные сведения см. в разделе [Ссылки на коллекции переменных отчета и группы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/built-in-collections-report-and-group-variables-references-report-builder.md).|  
|**ReportItems**|Не отображается|`=ReportItems("Textbox1").Value`|Представляет коллекцию текстовых полей для элемента отчета. Эта коллекция может использоваться для суммирования элементов на странице для включения в верхний или нижний колонтитул. Дополнительные сведения см. в разделе [Ссылки на коллекцию ReportItems (построитель отчетов и службы SSRS)](../../reporting-services/report-design/built-in-collections-reportitems-collection-references-report-builder.md).|  
  
##  <a name="Syntax"></a> Использование в выражениях синтаксиса коллекций  
 Чтобы обратиться к коллекции из выражения, можно использовать стандартный синтаксис [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] для элемента в коллекции. В следующей таблице показаны примеры синтаксиса коллекций.  
  
|Синтаксис|Пример|  
|------------|-------------|  
|*Collection!ObjectName.Property*|`=Fields!Sales.Value`|  
|*Collection!ObjectName("Property")*|`=Fields!Sales("Value")`|  
|*Collection("ObjectName").Property*|`=Fields("Sales").Value`|  
|*Collection("Member")*|`=User("Language")`|  
|*Collection.Member*|`=User.Language`|  
  
## <a name="see-also"></a>См. также  
 [Добавить выражение &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/add-an-expression-report-builder-and-ssrs.md)   
 [Примеры выражений &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)  
  
  

